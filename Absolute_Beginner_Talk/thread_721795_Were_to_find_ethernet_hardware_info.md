---
title: "Were to find ethernet hardware info?"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Astura on 2008-03-11
Im trying to find out what the brand name of my ethernet and wirelessethernet adaptors are inorder to get drivers (wireless does not work), but I am having trouble locating this information.

Can some one point me in the right direction?
Thanks!

---

### Post by spupy on 2008-03-11
Try the command
```
lspci
```
under root. Look for "ethernet controller".

---

### Post by alphaniner on 2008-03-11
There's also a gui method if you are running ubuntu:

System -> Preferences -> Hardware Information

There may be something like that in Kubuntu, too, but not in Xubuntu I think.

---

