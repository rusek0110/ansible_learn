# Ansible learning

## First steps Ansible

### **1. Instaling packages**

Ubuntu

```
apt install ansible python pip pytnon3-venv
```

### 2. **Python virtual environment (venv)**

```
python3 -m venv "path to venv"
python3 -m venv $HOME/venv/ansible
```

Actiate venv

```
. "path to venv"/bin/activate
source "path to venv"/bin/activate
```

eg. for ansible

```
. $HOME/venv/ansible/bin/activate
source $HOME/venv/ansible/bin/activate
```

### **3. Ansible config** 

Default config is located in

```
/etc/ansible/ansible.cfg 
```

### **4. Ansible inventory**

Command to check if inventory is valid

```
ansible-inventory -i inventory_file --list
```

There are 2 ways to create inventory files:
- INI file
- YAML file

Example INI file:

```
[controler]
dev ansible_host=192.168.0.242

[vms]
vm01  ansible_host=Hostname/IP
vm02  ansible_host=Hostname/IP
```

Example YAML file:

```
all:
  children:
    controler:
      hosts:
        dev: 
          ansible_host: Hostname/IP
    vms:
      hosts:
        vm01:
          ansible_host: Hostname/IP
        vm02:
          ansible_host: Hostname/IP
```

Those files are equal and elier command will retun equal data. To check this we can dump outut to 2 files and check if they are diffrent with `diff` command

