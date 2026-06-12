---
title: "build essentials"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by r0tc0d on 2007-08-15
im trying to get build-essentials but i get 

r0tc0d@r0tc0d:~$ sudo apt-get install build-essentials
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essentials
r0tc0d@r0tc0d:~$ 

any help?

---

### Post by talby on 2007-08-15
drop the last "s" for savings (sorry that was poor :)

$ sudo apt-cache search build-essential
build-essential - informational list of build-essential packages
devscripts - Scripts to make the life of a Debian Package maintainer easier
dh-buildinfo - Debhelper addon to track package versions used to build a package
sbuild - Tool for building Debian binary packages from Debian sources

---

### Post by Steve1961 on 2007-08-15
sudo apt-get install build-essential

---

### Post by r0tc0d on 2007-08-15
Now im embarrassed ;D 

thanks for helping me both of you :)

---

