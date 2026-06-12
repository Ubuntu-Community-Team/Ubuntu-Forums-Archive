---
title: "Problems Mounting NTFS Raid"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by Saicho on 2007-01-30
I'm trying to mount my NTFS raid so ubuntu can read files from it. I'll get right to it. I have 3 HDDs in my box, and successfully dual boot ubuntu and windows (on an NTFS raid array):

/dev/sda
/dev/sdb
/dev/sdc

/dev/sda has three partitions. The first sda1 is a 2gb boot NTFS partition, sda2 is my main ubuntu partition, sda3 is swap.

sdb and sdc are in a nvidia software raid array where windows is installed.

my fdisk -l output:

```

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         255     2048256    7  HPFS/NTFS
/dev/sda2           30133       30394     2104515   82  Linux swap / Solaris
/dev/sda3             256       30132   239987002+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60787   488271546    7  HPFS/NTFS

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdc doesn't contain a valid partition table
```

gparted doesn't see any partitions on sdb or sdc, and installing dmraid didn't help much either.

my dmraid -r output:

```

/dev/sda: nvidia, "nvidia_bafadeai", stripe, ok, 488281248 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_bfdccfeb", stripe, ok, 488281248 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_bfdccfeb", stripe, ok, 586072366 sectors, data@ 0
```

my dmraid -ay output:

```

RAID set "nvidia_bafadeai" already active
RAID set "nvidia_bafadeai1" already active
RAID set "nvidia_bafadeai2" already active
RAID set "nvidia_bafadeai3" already active
```

The only thing I can do right now is mount that little 2gb windows boot partition (sda1) at the beginning of sda. I get the same results if I try to mount /dev/mapper/nvidia_bafadeai1. When I tried to mount sdb1 as NTFS it didn't work either...

Can anyone help me find a way to mount the NTFS raid? Seems like Ubuntu doesn't even see that it exists at the moment.

---

### Post by Saicho on 2007-01-31
no one knows?

---

### Post by Hibbelharry on 2007-01-31
The output of dmraid seems to look right. Did you try to mount the partitions with the right device nodes in /dev/mapper ? Seems you're trying with the single devices, not the raid array.

---

### Post by Saicho on 2007-02-10
> **Saicho said:**
> I'm trying to mount my NTFS raid so ubuntu can read files from it. I'll I get the same results if I try to mount /dev/mapper/nvidia_bafadeai1. When I tried to mount sdb1 as NTFS it didn't work either...

I've tried mounting every possible combination, it does not seem to work

---

