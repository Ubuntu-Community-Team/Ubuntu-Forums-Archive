---
title: "Cannot write to SanCruzer flash drive"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by rbc on 2007-12-16
I have a Sandisk Cruzer micro with that annoying U3 partition, that I can't write to. I am not trying to write to the U3 part, which I believe is some CDFS file system.The data partition was FAT16 but I changed it to FAT32, following the advice of a previous post. I have tried "chmod", "chown". I can manually mount the data portion. If it helps, here's the results of:

fdisk -l
 Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         983      495313+   b  W95 FAT32


mount
/dev/sdb1 on /media/sdb1 type vfat (rw)

What am i not doing correctly?

---

### Post by nowshining on 2007-12-16
have u simply tried unmounting and re-mounintg if not reboot, if u used gpartition partition editor, i've had that problem changing ntfs to ext3 on an external drive, does a reboot solve ur problem, it did me.

---

### Post by rbc on 2007-12-16
Thanks for the reply, but yes, I tried that, no luck

---

