---
title: "Ubuntu on VM on XP host"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by livestrong on 2007-12-16
Hi,

I am new to Ubuntu.

I created a VM on my XP host and installed the Ubuntu 7.10 server edition.

I have two issues here:

a) I realized that the root account on Ubuntu is disabled. How do I enabled that? I have tried using the following commands and none of them work:
1 - sudo passwd root
2 - su root
3 - sudo xterm

b) The second issue is, when I enter the above commands, I get the error:
sendmail: fatal: open/postfix/main.cf: No such file or directory
<myownusername> is not in the sudoers file. This incident will be reported.

I can't edit the sudoers file because I don't have the permissions for it.

During the installation of Ubuntu, I also realized that I wasn't asked for the root password. I created <myownusername> with my password, but apparently, I am not the root of my own machine.

Any help?

---

### Post by zvacet on 2007-12-16
If you need to do something with admin privileges type **sudo** in front of command.for example if you want to install some package you will type 

```
sudo dpkg -i package
```

and if you want to become root 

```
sudo -i
```

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

