---
title: "External Drive"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by medha on 2008-02-19
I am trying to use my laptop with Ubuntu to access some documents backed up on my external drive. It detects the hard drive because fdisk shows:

~$ fdisk -l
Disk /dev/sdc: 650.1 GB, 650136969216 bytes
255 heads, 63 sectors/track, 79041 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c5ccba8
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       79041   634896801    c  W95 FAT32 (LBA)

But every time I try to mount it, it gives me:

$ sudo mount /dev/sdc /media/myHD/
mount: you must specify the filesystem type

Should I use mkfs to create a fs for the HD? I dont want to change the contents of the hard drive in any way.

Thanks!

---

### Post by Origin415 on 2008-02-19
add the line -t vfat to the command, to specify the filesystem type :D

mount only automatically recognizes certain common types, like ext3, nfs, etc.

---

### Post by medha on 2008-02-19
Yes, but that still doesnt answer my question, will it install the fs on the external drive?

Sorry for being so naive..

---

### Post by Origin415 on 2008-02-20
No, it wont change the disks format, it is just telling mount how to handle the drive how it is.

---

