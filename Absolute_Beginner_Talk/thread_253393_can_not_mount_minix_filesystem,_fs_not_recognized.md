---
title: "can not mount minix filesystem, fs not recognized"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by katsolimon on 2006-09-08
i have just installed ubuntu and afterwards minix3 on my disk. i have been using debian for a long time. there were 2 partitions on my disk one for xp one for debian.

i started ubuntu install and using its partition tool i have shrinked the old debian partition and made it extended so that i would create a swap partition and a root partition inside that extended partition. and lastly i have allocated the remaining disk space to a primary partition so as to install minix3.

here is my ```
fdisk -l
``` output

> 
Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3558    28579603+   7  HPFS/NTFS
/dev/hda2            3559        4474     7357770    f  W95 Ext'd (LBA)
/dev/hda3            4475        4864     3132675   81  Minix / old Linux
/dev/hda5            3559        4387     6658911   83  Linux
/dev/hda6            4388        4474      698796   82  Linux swap / Solaris
/dev/hda7            3559        3559           0+  83  Linux
/dev/hda8            4388        4388           0+  83  Linux

Partition table entries are not in disk order

and here is the ```
fdisk -l /dev/hda3
``` output


> Disk /dev/hda3: 3207 MB, 3207859200 bytes
255 heads, 63 sectors/track, 390 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

     Device Boot      Start         End      Blocks   Id  System
/dev/hda3p1   *        4475        4477       16384   81  Minix / old Linux
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(378, 0, 2) logical=(4474, 0, 2)
Partition 1 has different physical/logical endings:
     phys=(380, 10, 9) logical=(4476, 10, 9)
Partition 1 does not end on cylinder boundary.
/dev/hda3p2            4477        4668     1536000   81  Minix / old Linux
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(380, 10, 10) logical=(4476, 10, 10)
Partition 2 has different physical/logical endings:
     phys=(571, 67, 3) logical=(4667, 67, 3)
Partition 2 does not end on cylinder boundary.
/dev/hda3p3            4668        4864     1580290+  81  Minix / old Linux
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(571, 67, 4) logical=(4667, 67, 4)
Partition 3 has different physical/logical endings:
     phys=(767, 254, 63) logical=(4863, 254, 63)

i issue ```
mount -t minix /dev/hda3 /mnt/
```
result is:

> mount: wrong fs type, bad option, bad superblock on /dev/hda3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

result of ```
dmesg | tail
``` is:

> VFS: Can't find a Minix or Minix V2 filesystem on device hda3.

so what should i do in order to get the minix partition  mounted from ubuntu? thanks in advance :)

---

### Post by TwoWordz on 2006-09-08
I am not sure if the minix filesystem is supported by the default kernel.

Maybe you should have a look at the ubuntu kernel documentation.

Just to be sure your filesystem is ok, you can boot a live cd that support minix fs and check if you mount your partition.

TW

---

### Post by katsolimon on 2006-09-09
i have searched a bit but i cant figure out if my kernel supports minix file systems. i checked the man pages and it mentions about mounting minix file systems... and as far as i know, minix fs is used on the floppies. i can not grant that minix fs is supported by the kernel i use, but it seems to me that minix fs should be supported by default by an os like ubuntu. by the way i installed ubuntu 6.06 from the live cd and performed all the updates.

---

