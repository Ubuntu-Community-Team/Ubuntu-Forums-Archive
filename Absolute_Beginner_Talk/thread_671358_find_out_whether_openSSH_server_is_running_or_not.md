---
title: "find out whether openSSH server is running or not"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by ben22 on 2008-01-18
- Where can I check whether openSSH server is running or not?
- does openSSH server start automatically with system start?
- where do u define openSSH server to start with system?

---

### Post by stump138 on 2008-01-18
to see running services from console it is:
ps -aux | less

you can also go System->Administration->System Monitor

SSH should start automatically for you :)

---

### Post by atoponce on 2008-01-18
> **ben22 said:**
> - Where can I check whether openSSH server is running or not?
- does openSSH server start automatically with system start?
- where do u define openSSH server to start with system?

1. ```
root@kratos:~# ps aux | grep sshd
```2. Depends on your rc scripts, whether or not it starts with an S or a K.

```
root@kratos:~# ls /etc/rc?.d/*ssh
```3. Again, look at the rc init scripts.  Use update-rc.d to manage OpennSSH in the various runlevels.

---

### Post by Cypher on 2008-01-18
SSH will be set to start if it is installed. So start with
```

ps -eaf | grep -i ssh

```
If that lists the "ssh" daemon running, then you're all set. If not, then see if the server is installed with
```

dpkg -l | grep -i openssh

```
You should see "openssh-server" listed. If not, install it with
```

sudo apt-get install openssh-server

```
Once installed, you can start it up with
```

sudo /etc/init.d/openssh start

```

---

