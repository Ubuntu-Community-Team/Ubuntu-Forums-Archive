---
title: "deb can't find a flle"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by bratliff on 2007-03-28
Why is it deb can't find any .deb files as shown below. I was in the terminal program.

ratliff

-rw-r--r-- 1 bob  bob  12675332 2007-03-11 03:29 avg71flm-r30-a0791.i386.rpm
drwx------ 3 bob  bob      4096 2007-03-28 17:24 gconfd-bob
drwx------ 2 root root     4096 2007-03-28 19:31 gconfd-root
drwxr-xr-x 2 bob  bob      4096 2007-03-28 17:32 hsperfdata_bob
drwx------ 2 bob  bob      4096 2007-03-28 19:44 kde-bob
drwx------ 2 root root     4096 2007-03-28 19:44 kde-root
drwx------ 2 bob  bob      4096 2007-03-28 17:24 keyring-oUIJkm
drwx------ 3 bob  bob      4096 2007-03-28 19:44 ksocket-bob
drwx------ 3 root root     4096 2007-03-28 19:44 ksocket-root
-rw-r--r-- 1 root root  6176846 2007-03-28 19:27 limewire-free_4.12.11-1_i386.deb
-rw-r--r-- 1 bob  bob   8902576 2007-03-28 19:36 LimeWireOther.zip
-rw-r--r-- 1 bob  bob   6268517 2007-03-28 19:04 l.rpm
srwxr-xr-x 1 bob  bob         0 2007-03-28 17:24 mapping-bob
drwx------ 2 bob  bob      4096 2007-03-28 19:43 orbit-bob
drwx------ 2 root root     4096 2007-03-28 19:31 orbit-root
drwx------ 2 bob  bob      4096 2007-03-28 17:24 ssh-AweShZ5659
drwx------ 2 bob  bob      4096 2007-03-28 17:24 virtual-bob.RQkMpy
bob@bob-desktop:/tmp$ sudo rpm -qip –scripts avg71flm-r30-a0791.i386.rpm
error: open of –scripts failed: No such file or directory
error: open of –scripts failed: No such file or directory
bob@bob-desktop:/tmp$

---

### Post by ComplexNumber on 2007-03-28
i notice that you have some rpm files there. they're useless on ubuntu because ubuntu is a debian based system that uses deb files.


i don't understand what you mean when you say "Why is it deb can't find any .deb files"

btw what exactly are you wanting to do?

---

### Post by mcduck on 2007-03-28
There is no such program as 'deb'. The tool to install .deb packages is dpkg, for example 'sudo dpkg -i package.deb'.

Also you shouldn't try to use RPM packages in Ubuntu, Ubuntu uses .deb, not .rpm. Try to find correct packages and if you really can't find one then use the 'alien' tool to convert rpm packages to deb first.

---

