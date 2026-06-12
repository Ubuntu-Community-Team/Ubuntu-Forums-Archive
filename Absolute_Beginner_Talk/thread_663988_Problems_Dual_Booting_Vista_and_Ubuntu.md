---
title: "Problems Dual Booting Vista and Ubuntu"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by mirulmuffs on 2008-01-10
i want to format my linux partition.

i dualboot windows vista and ubuntu..
please help me.

this is the output of

sudo fdisk -l
```


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74a4d7fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39074816    7  HPFS/NTFS
/dev/sda2            4865        6421    12499023+   7  HPFS/NTFS
/dev/sda3            6422        9587    25430895   83  Linux
/dev/sda4            9588        9729     1140615    5  Extended
/dev/sda5            9588        9729     1140583+  82  Linux swap / Solaris

Disk /dev/sdb: 2061 MB, 2061500416 bytes
16 heads, 32 sectors/track, 7864 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x21704ef3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7864     2013168    6  FAT16

Disk /dev/sdc: 1 MB, 1474560 bytes
1 heads, 3 sectors/track, 960 cylinders
Units = cylinders of 3 * 512 = 1536 bytes
Disk identifier: 0x69737369

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?   623257122   679486963    84344761   69  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(68, 13, 10) logical=(623257121, 0, 3)
Partition 1 has different physical/logical endings:
     phys=(288, 115, 43) logical=(679486962, 0, 1)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?   567173161  1190466982   934940732+  73  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(567173160, 0, 2)
Partition 2 has different physical/logical endings:
     phys=(366, 32, 33) logical=(1190466981, 0, 3)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?         858         858           0   74  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(857, 0, 3)
Partition 3 has different physical/logical endings:
     phys=(372, 97, 50) logical=(857, 0, 2)
Partition 3 does not end on cylinder boundary.
/dev/sdc4               1  1145037824  1717556736    0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(1145037823, 0, 3)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order



```

---

### Post by linux-addict on 2008-01-10
Just done dual boot on Acer Aspire 4520.  You need to download a copy of  G-Parted and go from there.Running Vista Basic and Ubuntu 7.10  Working on connecting wireless.Without much success so far!:)

---

