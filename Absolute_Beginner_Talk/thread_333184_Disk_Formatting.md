---
title: "Disk Formatting"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by sdyardking on 2007-01-07
I am trying to format my first disk with:
sudo mke2fs -c /dev/sdb1
But I am getting the error:
/dev/sdb1 is mounted; can not make a filesystem here!
The disk is connected via USB and has a Linux partition
Surely I need to me mounted to format the disk?
Any help appreciated
Thanks
Chris

---

### Post by mykalreborn on 2007-01-07
no. actually you need to unmount the partition and then you can format it. ;)

---

### Post by infoseeker on 2007-01-07
At command prompt:
```
sudo umount /dev/sdb1
```first

---

### Post by sdyardking on 2007-01-08
umount worked, drive now formatted, thank you for your help

---

