---
title: "invalid mount option for USB key"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Vincent Plagnol on 2008-01-31
Dear all,

I am using the most recent Ubuntu (Gutsy Gibbon I think) on my Toshiba X61 laptop and my USB keys cannot be mounted anymore (none works, not key specific) and I could not find answers in old posts. The error message tells me:
Invalid mount option when attempting to mount the volume 'usb'.

On top of that my fdisk -l shows strange messages:


Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf566b7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         610     4895744   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         610        6692    48856445+   7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            6693       11932    42078960   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4           11932       12161     1844640    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5           11932       12161     1844608+  82  Linux swap / Solaris

Disk /dev/sdb: 1004 MB, 1004011520 bytes
248 heads, 32 sectors/track, 247 cylinders
Units = cylinders of 7936 * 512 = 4063232 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         248      980464    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 247, 32) logical=(247, 23, 32)

Does someone have an idea re. what is going on?

Thanks in advance for the help,

Vincent

---

### Post by dcstar on 2008-02-02
> **Vincent Plagnol said:**
> Dear all,

I am using the most recent Ubuntu (Gutsy Gibbon I think) on my Toshiba X61 laptop and my USB keys cannot be mounted anymore (none works, not key specific) and I could not find answers in old posts. The error message tells me:
Invalid mount option when attempting to mount the volume 'usb'.

On top of that my fdisk -l shows strange messages:
............
Disk /dev/sdb: 1004 MB, 1004011520 bytes
248 heads, 32 sectors/track, 247 cylinders
Units = cylinders of 7936 * 512 = 4063232 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         248      980464    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 247, 32) logical=(247, 23, 32)

Does someone have an idea re. what is going on?

Thanks in advance for the help,

Vincent

You need to do a fsck on /dev/sdb, because Ubuntu does not like the way the partition is set up.

You probably should copy off all the data and reformat the USB.

---

