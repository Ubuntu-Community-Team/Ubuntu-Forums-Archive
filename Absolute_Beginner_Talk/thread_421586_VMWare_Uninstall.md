---
title: "VMWare Uninstall"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Joka999 on 2007-04-24
Hi, just installed Ubuntu 7.04 and I installed VMWare with Automatix and then i got VMWare Workstation but when I try and install the workstation it says there is another VMWare although i uninstalled it throught Automatix, anything else I have to do?

---

### Post by zvacet on 2007-04-24
In usr/bin is vmware uninstall file,so go to the usr/bin
```
cd /usr/bin
```
and when you are there

sudo ./uninstall file

of course you will put corrrect file name 

Chek etc to see is there vmware folder and if it is delete it.Do the same with home directory and with hidden folders in home directory.When it is all clean start installing vmware again.

---

