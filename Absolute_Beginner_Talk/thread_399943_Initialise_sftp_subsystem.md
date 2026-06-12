---
title: "Initialise sftp subsystem"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by zhenwei on 2007-04-02
Hi,

We have a 6.1.0  server installation. SSH is working- we are able to log in just fine. When trying to connect /etc/init.d/ssh sftp-system, the response is: 

Starting OpenBSD secure shell server ......................... [COLOR="Red"]Fail[/COLOR]

We can stop, start, restart SSH, but not the subsystem. We are very new to linux of any flavour. All asistance gratefully recevied.

Thank you.

---

### Post by Skrynesaver on 2007-04-03
Have you tried using scp from another machine to copy a file over? eg 
```
scp user@hostname:/home/user/file ./file
```The default is for sftp to be turned on, if not check your /etc/ssh/sshd_config for the line
```
Subsystem sftp /usr/lib/openssh/sftp-server
``` sshd reads this file on startup and so it's easier to do the configuration once in here.
Hope that helps

---

### Post by zhenwei on 2007-04-18
Hi

Thanks for your reply. Sorry for the long delay in replying, I got sidetracked to other projects. 
Anyway, i found the line: Subsystem sftp /usr/lib/openssh/sftp-server inside sshd.config. 

I got the error message " receive message too long 220933421" while trying to connect to the linux server.

Regards
zhenwei

---

### Post by Skrynesaver on 2007-04-19
Does the user logging in have any output in their .bashrc? This  can mess with expect statements in the client.  For example if you have fortune || pom ||w  set to execute @ login the sftp client isn't expecting this and can fail as a result as can motd if set system-wide.
Or am I completely misunderstanding your question ;) ?

---

