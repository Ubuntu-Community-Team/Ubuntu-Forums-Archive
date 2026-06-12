---
title: "/dev/hdc1 doesn't exist"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by alley on 2007-02-11
I have ubuntu setup on my sata disk /dev/sda1
I have my home mounted on /dev/sdb1

My /dev/hdc device is the one containing grub, and boots fine.
However, ubuntu does not see my partitions on hdc

there should be /dev/hdc1 (an ntfs partition) and /dev/hdc5 (fat32 partition)

If I run 'sudo fdisk -l' those 3 partitions are listed. Gparted sees them also.

But I cannot mount them since they're not listed in /dev/
(gparted also gives a warning notice on those partitions saying 'The device /dev/hdc1/ doesn't exist').

Here's my output from fdisk:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    5  Extended
/dev/sdb5               1       18951   152223844+  83  Linux
/dev/sdb6           18952       19457     4064413+  82  Linux swap / Solaris

Disk /dev/hdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       23503   188787816    7  HPFS/NTFS
/dev/hdc2           23504       24792    10353892+   f  W95 Ext'd (LBA)
/dev/hdc5           23504       24792    10353861    c  W95 FAT32 (LBA)

```

---

### Post by alley on 2007-02-12
anyone?

---

