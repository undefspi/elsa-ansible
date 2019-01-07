# Playbooks for provisioning a vm that connects to a nas 

## Run playbook
ansible-playbook -i inventory configure_elsamedia.yml --tag "elsamedia,mountnas" --ask-sudo --ask-vault-pass

Example Vault entries

vnc_password: 'mypassword'
#cifs_shares
myshare_net_path: '//192.168.0.2/myshare'
myshare_net_path_hash: "{{ myshare_net_path | password_hash('sha512')}}"
share_username: 'shareusername'
share_password: 'sharepassword'

###
tags include:
* elsamedia - install dev packages for the elsamedia box
* mountnas - mounts the nas shares
* enablevnc - sets up the vnc server on remote server and starts it
