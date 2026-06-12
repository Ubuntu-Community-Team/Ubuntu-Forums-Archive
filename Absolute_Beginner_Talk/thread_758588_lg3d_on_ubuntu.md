---
title: "lg3d on ubuntu"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by viperskunk on 2008-04-18
hi 
i just downloaded lg3d on ubuntu 7.10 thru the terminal.
but while installing i get the message:

viper@viper-laptop:~$ sudo apt-get install lg3d-core
[sudo] password for viper:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lg3d-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 211 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up lg3d-core (1.0.0) ...
/usr/share/lg3d/bin/postinstall: line 10: /bin/arch: No such file or directory
/usr/share/lg3d/bin/../bin/add-lg-to-gdm: line 28: /bin/arch: No such file or directory
Success. LG has been added as a gdm session.
/usr/share/lg3d/bin/postinstall: line 43: cd: /usr/share/lg3d/bin/../lib/linux-/lg3d-x11/programs/Xserver: No such file or directory
chown: cannot access `Xorg': No such file or directory
chgrp: cannot access `Xorg': No such file or directory
chmod: cannot access `Xorg': No such file or directory
dpkg: error processing lg3d-core (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 lg3d-core
E: Sub-process /usr/bin/dpkg returned an error code (1)
viper@viper-laptop:~$ 


i really don't know what xorg is or how to get it working as i am quite new (sorry) to ubuntu.
could someone please tell me what to do to get lg3d running on my computer? i mean all the basic steps and things i need to keep in mind?
thanks a lot in advance.

---

### Post by northern lights on 2008-04-18
As for X: [http://www.x.org/wiki/]("http://www.x.org/wiki/")

Try running ```
apt-get update
```and```
apt-get upgrade
``` first, see what happens.

---

### Post by viperskunk on 2008-04-20
thanks it worked.

---

### Post by spider3000 on 2008-04-30
I have exactly the same problem. I run on Hardy. I ran both commands as suggest with sudo, and on the second it asked me to again agree to the license agreement, etc.. but then I get the same error. Any help would be appreciated.

---

### Post by usernameomar on 2008-05-01
cd /bin; echo 'uname -m' > /bin/arch; chmod 755 /bin/arch
then complete your installation or apt-get install lg3d-core

---

### Post by setsuna on 2008-06-09
owh, i have the same problem with spider3000

and i do
```

$ su[INDENT]{type the root password}[/INDENT]

$ cd /bin
$ echo 'uname -m' > /bin/arch
$ chmod 755 /bin/arch[INDENT]{and the last}[/INDENT]
$ apt-get install lg3d-core
```


and it worked!! thx usernameomar
HE HE HE

---

