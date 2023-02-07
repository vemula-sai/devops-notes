## Ansible defination:

* Ansible is an open-source IT automation tool that helps you manage and configuring systems, deploying software and install softwares and perform IT tasks
* Ansible maintains the list of nodes to be communicated and is referred as inventory.
* Ansible is push configuration management.
* To write the declarative configuation, Ansible used YAML and calls it as Playbook.

## what are the possible to install or deploy the application:

* Admins have permissions to deploy the application manually.
* write scripts like shell/powershell to deploy the application.
* Using decleartive approch like configuration management to deploy the application. 

## Test enviroments in ansible:

* Dev Environment: This environment needs to deployed for every change done by dev team.
* System Test Environment: This environment needs to be deployed once every day at 11:00 PM
* Performance Test Environment : This environment needs to be deployed once every day at 1:00 AM
* UAT (User Acceptance Testing)/Pre-Prod/Staging: This we deploy every weekend i.e. saturday 6:00 AM

## configuration management 
* configuartion management has two methods:
   * pull: In pull Cm nodes initiate the communication to the cm server.
       * In PULL BASED CM, An agent is installed on every node which is responsible for initiating the communication and following instructrions from CM Server 
   * push: In push Cm initiate the communication to the nodes.
       * In PUSH BASED CM, CM Server has admin credentials of the node and the details like ip adress/hostname to login and execute the declarative configuration.

## Ansible requirements

* Configuration Management Server in the case of ansible can be very light weight machin.
* Ansible logs in to the nodes and executes the declarative configuration & for that it requires python to be installed on the node.

## Approach

* Make a note all the manual steps for deploying the application.
* For each step find the command and convert that into declaration (Module).
* ![preview](images/ansible1.png)
* [ReferHere](https://docs.ansible.com/ansible/2.9/modules/apt_module.html#apt-module) for all modules.
  
## playbook syntax
```
---
- name: <describe your playbook here>
  tasks:
    - name: <what this task is about>
      <module>:
         <module-parameter-1>: <module-value-1>
         ..
         <module-parameter-n>: <module-value-n>
         state: <value (present)>
    - name: <what this task is about>
      <module>:
         <module-parameter-1>: <module-value-1>
         ..
         <module-parameter-n>: <module-value-n>
         state: <value (present)>
```
## Ansible Installation and configuration

* ![preview](images/ansible2.png)
* AWS machines have passwords disabled by default. So lets enable password.(sudo vi /etc/ssh/sshd_config password=yes)
* And add the user to sudoers file (sudo visudo)
* same setup in node install agent passwd and sudoers file.

## Installing the ansible 

```
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible -y
ansible --version
```
## ansible commands 

```
ansible --version (check version)
ansible -i hosts -m ping -k all (to ping the hosts)
ansible-playbook -i inventoryfile yamlfile