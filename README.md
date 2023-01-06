# How to install the Nolus-networks node

This manual describes how to install the Starknet node on your Linux box using a predefined Ansible script

# Install Nolus-networks node on Linux

## Minimum requirements

Linux box with 1 CPU and 4 GB of RAM

About 100 GB Disk free space

## Prepare your Linux server to run Ansible playbooks

It is necessary to do it only once. If you did it before, skip the docker and Ansible installation


### Install docker stuff to prepare environment

Install from [here](https://github.com/zukudm/tools)

Also, you can do it without any scripts by yourself:

<details>


Docker engine from [here](https://docs.docker.com/engine/install/)

Just select your Linux distributive. 

Docker conmpose from [here](https://docker-docs.netlify.app/compose/install/)
</details>

### Install Ansible

Connect to the Linux box, where you are going to run the Starknet node and run commands to install Ansible

In the case of Ubuntu run these commands:

```bash
 apt update -y
 apt install -y software-properties-common
 add-apt-repository --yes --update ppa:ansible/ansible
 apt install -y ansible
```

In case of other distributions of Linux, follow instructions from [here](https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html)

## Fetch the repository with Ansible files and prepare to run the Starknet node on the Linux box

```bash
 apt update -y
 git clone https://github.com/zukudm/nolus-networks.git
 cd ~/nolus-networks
 ansible-galaxy install -r collections/requirements.yml
```

## Run Starknet node

```bash
cd ~/nolus-networks
ansible-playbook nolus_networks_setup.yml
```

After starting the nolusd daemon, the chain will begin to sync to the network. The time to sync to the network will vary depending on your setup and the current size of the blockchain, but it could take a very long time

To get Rila testnet tokens, check out the #testnet-faucet channel in our Discord server!

Wait for some time and run Validator upgrade. 

```bash
 cd ~/nolus-networks
 ansible-playbook nolus_networks_validator_setup.yml
```

After creating a new key, its information will be shown alongside the seed phrase. Make sure to write it down, as it is the only way to restore your keys.


# List of Ansible playbooks:

nolus_networks_setup.yml - Setup Nolus-netwroks node within your Linux box. Run it from root user. 

nolus_networks_validator_setup.yml - Run a Validator


nolus_remove.yml  - Remove all nolus-netwroks data, suitable for all cases.


# Update

Not done yet :(

# Remove

To remove Starnet node from the server just log in and run

```bash
 cd ~/nolus-networks
 ansible-playbook nolus_remove.yml
 ```
 
 
 
