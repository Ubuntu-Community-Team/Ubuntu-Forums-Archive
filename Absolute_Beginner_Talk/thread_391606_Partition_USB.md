---
title: "Partition USB"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by i2omani on 2007-03-23
Using a live Ubunto CD i am trying to format and partition 
i umount the USB

the fdisk /dev/sdb1 
i get " warning : invalid flag 0x0000 of partition table 4 will be corrected by w(rite).
i can't Format or partition the USB at al

---

### Post by yabbadabbadont on 2007-03-23
sdb1 is the first partition on the sdb drive.  You don't run fdisk on a single partition but instead on the whole drive.  Try "sudo fdisk /dev/sdb" instead.

---

