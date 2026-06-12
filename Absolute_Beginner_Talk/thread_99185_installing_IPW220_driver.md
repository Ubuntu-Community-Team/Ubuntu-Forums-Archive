---
title: "installing IPW220 driver"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by adduds on 2005-12-05
i d/led ipw2200-1.0.8.tgz driver and did

tar xvpf ipw2200-1.0.8.tgz and it unpacked and created the folder

ipw2200-1.0.8.tgz

now i'm stuck...anyone know where to go from here?

files inside are:

> adduds@ubuntu:~/packs$ cd /home/adduds/packs/ipw2200-1.0.8
adduds@ubuntu:~/packs/ipw2200-1.0.8$ ls
CHANGES  FILES     INSTALL    ISSUES   Makefile        remove-old  unload
config   GIT_SHA1  ipw2200.c  LICENSE  pci             restart
dvals    idvals    ipw2200.h  load     README.ipw2200  status


---

### Post by schdefan on 2005-12-05
after unpacking you need to run ```
$make
``` and ```
$make install
```
this will install your driver.

By the way. Maybe this [thread]("http://ubuntuforums.org/showthread.php?t=26623") helps you. 
schdefan

---

