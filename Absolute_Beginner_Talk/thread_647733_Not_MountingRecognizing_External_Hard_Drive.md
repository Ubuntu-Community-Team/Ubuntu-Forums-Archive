---
title: "Not Mounting/Recognizing External Hard Drive"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by System Monitor on 2007-12-22
I just bought a new 500GB usb external hard drive and when i connected it, nothing happend it appears that it was not recognized.

---

### Post by taurus on 2007-12-22
Can you open a terminal and post the output of this command?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by System Monitor on 2007-12-22
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       25326   203423062+   7  HPFS/NTFS
/dev/sda2           29252       30401     9230760    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3           25327       29251    31527562+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x12c20ecf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       41345   312568168+   7  HPFS/NTFS

Disk /dev/sdc: 4026 MB, 4026531840 bytes
216 heads, 32 sectors/track, 1137 cylinders
Units = cylinders of 6912 * 512 = 3538944 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1134     3915760    c  W95 FAT32 (LBA)

---

### Post by taurus on 2007-12-22
I don't see any 500GB harddrive from the output.  What brand name is it?  Does it have it own power ON/OFF?

---

### Post by System Monitor on 2007-12-22
Acom and it has its personal on off button. Worked with windows, i recently rebooted. I dual boot

---

