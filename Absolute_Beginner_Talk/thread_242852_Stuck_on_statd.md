---
title: "Stuck on statd"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by mock47 on 2006-08-24
Hi,
Hope someone can assist.
I have statd hung up on Ubuntu 6.06.
following is my error message:
desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up statd (1.0.1-6ubuntu1) ...
/var/lib/dpkg/info/statd.postinst: line 5: /etc/init.d/inetd: No such file or directory
dpkg: error processing statd (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 statd
E: Sub-process /usr/bin/dpkg returned an error code (1)
What can I do?
thanks, art

---

### Post by mock47 on 2006-08-24
Figured it out for myself, deleted dpkg post install folder with gksudo Nautilus.  This cleared the flawed install and allowed install -f to reinstall sucessfully.
art:)

---

