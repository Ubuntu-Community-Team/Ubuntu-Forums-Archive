---
title: "uninstall ksh"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by jsentianus on 2008-02-08
first time, I have installed ksh but later decided to uninstall it as it might interfere with pdksh. I have uninstalled it from synaptic package manager. But when I try to install another software whihc require pdksh, there is warning saying that I need to uninstall ksh. When I find the ksh using whereis ksh , the ksh is still there. see below... so how can I uninstall ksh cleanly.

** ERROR **
 Required package pdksh is not installed.
 Please uninstall package ksh and then install pdksh.
To install pdksh:
   as root/superuser, insert the PRECIS DVD, then:
   mkdir -p /media/dvd 
   mount /dev/cdrecorder /media/dvd 
   rpm -Uvh /media/dvd/utils/pdksh-5.2.14-16.i386.rpm 
 
sentian@dell:~$ whereis ksh
ksh: /bin/ksh /usr/bin/ksh /usr/X11R6/bin/ksh /usr/bin/X11/ksh /usr/share/man/man1/ksh.1.gz
sentian@dell:~$ ls -l /bin/ksh
lrwxrwxrwx 1 root root 21 2008-01-30 16:26 /bin/ksh -> /etc/alternatives/ksh
sentian@dell:~$

---

### Post by jan quark on 2008-02-08
try this command

```
sudo apt-get remove --purge package
```

---

