sa-auto-ssh
===========
[![Build Status](https://travis-ci.org/softasap/sa-auto-ssh.svg?branch=master)](https://travis-ci.org/softasap/sa-auto-ssh)


Persistent ssh tunnels.


Example of use: check box-example

Simple:

```YAML

vars:

  - autossh_forwarded_rules:
    - {
      forward_line: "-NL 9090:192.168.0.3:80",
      forward_host: "remoteuser@remotehost"
      }
    - {
      forward_line: "-NL 9091:192.168.0.151:80",
      forward_host: "remoteuser@remotehost"
      }

...

roles:

     - {
         role: "sa-auto-ssh",
         autossh_forwarded_rules: "{{autossh_forwarded_rules}}"
       }

```


Advanced:

```YAML

option_create_user: true

autossh_debug: False
autossh_gatetime: 30
autossh_first_poll: 30
autossh_loglevel: 0
autossh_pidfile: "/var/run/autossh/autossh.pid"
autossh_port: 0
autossh_poll: 60

autossh_user: "{{ansible_user_id}}" # you may consider using custom user for tunelling
autossh_user_shell: "/bin/false"

autossh_forwarded_rules:
  - {
    forward_line: "-NL 9090:192.168.0.3:80",
    forward_host: "remoteuser@remotehost"
    }
  - {
    forward_line: "-NL 9091:192.168.0.151:80",
    forward_host: "remoteuser@remotehost"
    }


```


```YAML


     - {
         role: "sa-auto-ssh",

         option_create_user: "{{option_create_user}}",

         autossh_debug: "{{autossh_debug}}",
         autossh_gatetime: "{{autossh_gatetime}}",
         autossh_first_poll: "{{autossh_first_poll}}",
         autossh_loglevel: "{{autossh_loglevel}}",
         autossh_pidfile: "{{autossh_pidfile}}",
         autossh_port: "{{autossh_port}}",
         autossh_poll: "{{autossh_poll}}",

         autossh_user: "{{autossh_user}}",
         autossh_user_shell: "{{autossh_user}}",

         autossh_forwarded_rules: "{{autossh_forwarded_rules}}"
       }

```


Usage with ansible galaxy workflow
----------------------------------

If you installed the `sa-auto-ssh` role using the command


`
   ansible-galaxy install softasap.sa-auto-ssh
`

the role will be available in the folder `library/softasap.sa-auto-ssh`
Please adjust the path accordingly.

```YAML

     - {
         role: "softasap.sa-auto-ssh"
       }

```




Copyright and license
---------------------

Code is dual licensed under the [BSD 3 clause] (https://opensource.org/licenses/BSD-3-Clause) and the [MIT License] (http://opensource.org/licenses/MIT). Choose the one that suits you best.

Reach us:

Subscribe for roles updates at [FB] (https://www.facebook.com/SoftAsap/)

Join gitter discussion channel at [Gitter](https://gitter.im/softasap)

Discover other roles at  http://www.softasap.com/roles/registry_generated.html

visit our blog at http://www.softasap.com/blog/archive.html

