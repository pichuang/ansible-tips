# Ansible Tips

## Var Prompt
```bash
cd ./vars_prompt
ansible-playbook comfirm.yml
```

Sample Output when you reply 'no':
```bash
"Do you want to install podman? [no/yes]"
 [no]: no

PLAY [Confirm whether user really meant to install the packags] ***************************************************************

TASK [exit playbook, if user did mean to purge cluster] ***********************************************************************
fatal: [localhost]: FAILED! => {"changed": false, "msg": "\"Existing the playbook, the system will NOT install\n podman. To install podman, either say 'yes' on  the prompt\n or use `-e install_podman=yes` on the command line when invoking\n the playbook\"\n"}

PLAY RECAP ********************************************************************************************************************
localhost                  : ok=0    changed=0    unreachable=0    failed=1    skipped=0    rescued=0    ignored=0
```

Sample Output when you reply 'yes':
```bash
"Do you want to install podman? [no/yes]"
 [no]: yes

PLAY [Confirm whether user really meant to install the packags] ***************************************************************

TASK [exit playbook, if user did mean to purge cluster] ***********************************************************************
skipping: [localhost]

TASK [Install podman] *********************************************************************************************************
ok: [localhost] => {
    "msg": [
        "Install podman! install podman",
        "Run!"
    ]
}

PLAY RECAP ********************************************************************************************************************
localhost                  : ok=1    changed=0    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0
```
