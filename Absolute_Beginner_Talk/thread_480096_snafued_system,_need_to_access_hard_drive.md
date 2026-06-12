---
title: "snafued system, need to access hard drive"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by johntkucz on 2007-06-21
I messed up my system (with permissions) and need to access my internal boot drive, which is 80gb, pretty sure its /dev/hda1, how do I access that?


 disk after fdisk -l and blkid; here's the code:

Device Boot Start End Blocks Id System
/dev/hda1 * 1 9376 75312688+ 83 Linux
/dev/hda2 9377 9729 2835472+ 5 Extended
/dev/hda5 9377 9729 2835441 82 Linux swap / Solaris

Disk /dev/sda: 1021 MB, 1021312512 bytes
129 heads, 16 sectors/track, 966 cylinders
Units = cylinders of 2064 * 512 = 1056768 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 967 997367+ e W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
phys=(972, 128, 16) logical=(966, 57, 15)

Disk /dev/sdc: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 7872 2015216 e W95 FAT16 (LBA)

Disk /dev/sdd: 517 MB, 517341184 bytes
218 heads, 45 sectors/track, 103 cylinders
Units = cylinders of 9810 * 512 = 5022720 bytes

Device Boot Start End Blocks Id System
/dev/sdd1 * 1 103 505192+ b W95 FAT32

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdf1 1 60801 488384001 c W95 FAT32 (LBA)

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
ubuntu@ubuntu:/boot$ blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="TravelDrive" UUID="392C-62FA" TYPE="vfat"
/dev/sdc1: SEC_TYPE="msdos" LABEL="TRAVEL2GB" UUID="D4BB-92EF" TYPE="vfat"
/dev/sdd1: LABEL="JTK_IPOD" UUID="0000-0000" TYPE="vfat"
/dev/sdf1: LABEL="My Book" UUID="92A8-ABE1" TYPE="vfat"
ubuntu@ubuntu:/boot$


Please help! I need to get files off of dev/hda1
from
/dev/hda1 * 1 9376 75312688+ 83 Linux
/dev/hda2 9377 9729 2835472+ 5 Extended
/dev/hda5

How can I do that?

---

### Post by kspn on 2007-06-21
I think that the simplest solution would be to boot your system off the LiveCD.

Once the system is up then you should be able to mount the /dev/hda1 partition.

That should give you access to the Partition.

---

