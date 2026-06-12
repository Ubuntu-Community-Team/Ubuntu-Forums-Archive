---
title: "advice on install  NXserver"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by bison0927 on 2008-01-28
I am installing the NXserver, and encountered a problem.

gzou@gzou-laptop:~$ sudo /etc/init.d/ssh restart
[sudo] password for gzou:
sudo: /etc/init.d/ssh: command not found
gzou@gzou-laptop:~$ sudo /usr/NX/nxserver --status
sudo: /usr/NX/nxserver: command not found
gzou@gzou-laptop:~$ sudo /usr/NX/bin/nxserver --status
NX> 900 ssh: connect to host 127.0.0.1 port 22: Connection refused
NX> 110 NX Server is stopped.
NX> 999 Bye.
gzou@gzou-laptop:~$ 

in fact , I looked the solution in the forum , but i can not figure it not.Anyone who can help?
PS: how can i modified the ssh_config?
I use the command  sudo nano /etc/ssh/sshd_config, after I  do not know how to edit the content,any ideas?

---

### Post by sciencectn on 2008-01-28
I'm not that experienced on this, but judging by "sudo: /etc/init.d/ssh: command not found", you might not have the ssh server installed. Have you installed these packages?

```
sudo apt-get install openssh-client
sudo apt-get install openssh-server
```

---

### Post by Amstell on 2008-01-28
also make sure your router is set for port forwarding on port 22.

---

