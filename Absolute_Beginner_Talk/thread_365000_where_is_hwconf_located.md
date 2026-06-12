---
title: "where is hwconf located"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by DesiSinger on 2007-02-19
Hello

Where is hardware config file located on Ubuntu 6.10.

It's not under /etc/sysconfig  - sysconfig does not exist under /etc

Please help.
Thank you

---

### Post by Koybe on 2007-02-19
The directory /etc/sysconfig is from RedHat/Suse. Ubuntu comes from Debian and does not have this directory.

Anyway all config files are still in /etc. It depends on what your are really looking for. 

/etc/sysconfig/networking/if-eth0.cfg -> /etc/network/interfaces.

You can use several command to find what you need : whereis, locate, find, grep...

---

