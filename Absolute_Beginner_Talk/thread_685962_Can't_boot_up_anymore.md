---
title: "Can't boot up anymore"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by JerseyDevil1111 on 2008-02-02
I can't get my IDE drive to boot up after installing and uninstalling Ubuntu. I can't do an XP reinstall because I get an OS error. What can I do?

---

### Post by Shazaam on 2008-02-02
Looks like when you removed Ubuntu it took grub with it. If you have a retail version of a  Windows disk you can do a "fixmbr" from the Recovery Console to get windows back.
First, lets see what your drive looks like. Boot the Ubuntu livecd, open terminal and enter this in.....
```
sudo fdisk -l
```
(small L)
Copy and paste the output here.

---

