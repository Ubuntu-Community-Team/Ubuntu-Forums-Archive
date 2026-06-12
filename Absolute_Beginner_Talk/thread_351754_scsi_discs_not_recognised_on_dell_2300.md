---
title: "scsi discs not recognised on dell 2300"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by bigun on 2007-02-02
Hi, 

I have a Poweredge 2300, PII 350Mhz with 256 Mb, 3x 9Gb SCSI Discs 

I have tried installing "edgy" but the install can't detect disks.

From the LiveCD of 6.06 I get this...

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 8984 MB, 8984199168 bytes
255 heads, 63 sectors/track, 1092 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         127     1020096    6  FAT16
/dev/sda2             128        1092     7751362+   5  Extended
/dev/sda5             128        1092     7751331    7  HPFS/NTFS

Disk /dev/sdb: 8984 MB, 8984199168 bytes
255 heads, 63 sectors/track, 1092 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1092     8771458+  87  NTFS volume set

Disk /dev/sdc: 9120 MB, 9120514048 bytes
255 heads, 63 sectors/track, 1108 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1108     8899978+  87  NTFS volume set
```

Thanks for the help...

---

