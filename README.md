systemd
=======

Adds a systemd service, with a similar interface to the `master` branch.

Role Variables
--------------

You **must** specify:

* `service_name` - The name of the service
* `service_exec` - The executable and arguments to run

The default variables are as follows:

```
service_env: ''                                # Environment variables as 'VAR=val VAR2=val2'
service_chdir: '{{ service_exec | dirname }}'  # The directory to execute from
service_user: '{{ ansible_ssh_user }}'         # The user that runs the service executable
service_restart: true                          # Whether to restart the service once configured
```


Example Playbook
----------------

```
- hosts: servers
  roles:
    - role: ssilab.upstart
      service_name: 'my-app'
      service_chdir: '{{ deploy_helper.current_path }}'
      service_exec: 'nodejs server.js'
```

License
-------

BSD. See LICENSE.
