---
title: "refit is not booting ubuntu"
date: 2008-05-20
forum: Apple Hardware Users
---

### Post by abhiomkar on 2008-05-20
I have 1 HFS+ parition & two linux partition (one is ubuntu, and other one is blank ext3), i am using refit in MacBook to boot. I 'm not able to boot in to Ubuntu, it says missing operating system when i choose lagacy os in refit . may be the refit is trying to boot the blank ext3 partition. 
my parition table : 
```
$ sudo fdisk /dev/rdisk0
Disk: /dev/rdisk0	geometry: 9729/255/63 [156301488 sectors]
Signature: 0xAA55
         Starting       Ending
 #: id  cyl  hd sec -  cyl  hd sec [     start -       size]
------------------------------------------------------------------------
 1: EE 1023 254  63 - 1023 254  63 [         1 -     409639] <Unknown ID>
 2: AF 1023 254  63 - 1023 254  63 [    409640 -  131259100] HFS+        
*3: 83 1023 254  63 - 1023 254  63 [ 131668740 -     976563] Linux files*
 4: 83 1023 254  63 - 1023 254  63 [ 132645303 -   23654297] Linux files*

```

[http://paste.ubuntu.com/13523/](http://paste.ubuntu.com/13523/) .
Help ?

---

### Post by cyberdork33 on 2008-05-20
make sure you sync the partition tables in refit:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by abhiomkar on 2008-05-24
Thanks, I got the solution.
I installed grub, then it worked.

Boot into Ubuntu Live CD
Open Terminal
*$ **sudo grub***
> **root (hd0,3)**
#where 3 is your (linux parition - 1), if your linux parition is hda4, then put 3.
*> **setup (hd0)***
*> **quit***
Restart the machine, & sync the parition table with refit. Then, it should work.

---

