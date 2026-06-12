---
title: "Can't get the new library versions using apt-get"
date: 2005-12-27
forum: Absolute Beginner Talk
---

### Post by Reggie on 2005-12-27
Hi,

I'm trying to install LMMS. When I try to install the package, it gives an error:

> dpkg: dependency problems prevent configuration of lmms:
 lmms depends on libqt3-mt (>= 3:3.3.5); however:
  Version of libqt3-mt on system is 3:3.3.4-8ubuntu5.


When I try apt-get install libqt3-mt I get:
> root@kwebbel:/home/reggie/Desktop/lmms # apt-get install libqt3-mt
Reading package lists... Done
Building dependency tree... Done
libqt3-mt is already the newest version.


Why doesn't apt get the newest version ? Are there good sources for this ?

---

### Post by Reggie on 2005-12-27
Ok I found out about the backports ... but is it safe to add a backport of hoary to a dapper version of ubuntu ?

---

