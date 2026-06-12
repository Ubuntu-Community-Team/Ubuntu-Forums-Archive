---
title: "Installing real players"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by darvina on 2006-06-13
darvi222a:~$ sudo dpkg -i realplayer_10.0.7-0.0_i386.deb
(Reading database ... 58456 files and directories currently installed.)
Preparing to replace realplayer 10.0.7-0.0 (using realplayer_10.0.7-0.0_i386.deb) ...
Unpacking replacement realplayer ...
dpkg: dependency problems prevent configuration of realplayer:
 realplayer depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
dpkg: error processing realplayer (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 realplayer


I look at package manger and it says i have libc6 installed  what am i doing wrong

---

### Post by Jagot on 2006-06-13
Try installing the libstdc++5 package then try and install the .deb again.

---

### Post by taurus on 2006-06-13
Are you trying to install it on Breezy?

---

