# cisco-ios-command

This Ansible script runs commands on remote Cisco IOS XE device and retrieve the result into output folder. The script gathers the IOS Facts Information.

```yml
---
all:
  children:
    all_cisco_ios:
      hosts:
        r4.xpnetworks.local:
          inventory_network_os: cisco.ios.ios
          inventory_host: 192.168.1.14
          inventory_port: 22
          inventory_user: admin
          inventory_pass: password
    all_cisco_asa:
      hosts:
        ciscoasa1:
          inventory_network_os: cisco.asa.asa
          inventory_network_cisco_asa_type: vpn
          inventory_network_cisco_asa_ha_type: standalone
          inventory_host: 192.168.1.98
          inventory_port: 22
          inventory_user: admin
          inventory_pass: password
    all_f5:
      hosts:
        bigip1:
          inventory_network_os: f5.bigip
          inventory_host: 192.168.1.245
          inventory_port: 443
          inventory_user: admin
          inventory_pass: password
        bigip2:
          inventory_network_os: f5.bigip
          inventory_host: 192.168.1.246
          inventory_port: 443
          inventory_user: admin
          inventory_pass: password
        bigip3:
          inventory_network_os: f5.bigip
          inventory_host: 192.168.1.247
          inventory_port: 443
          inventory_user: admin
          inventory_pass: password
```

## Prerequisite
Ansible ansible-pylibssh modules must be installed before running the script.
```bash
pip install ansible-pylibssh
```

## Usage:
```bash

ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook -vvvv --vault-password-file vault_pass.yaml -i inventory-vault.yaml cisco-ios-command.yml --extra-vars="ios_device=r4"
```
**_NOTE:_**  `output` folder must be created before running the script.

## Files
- cisco-ios-command.yml >> Ansible script file
- vault_pass.yaml >> Inventory vault password information
- inventory-vault.yaml >> Inventory vault file encrypted by "Inventory vault password"
