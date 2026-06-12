---
title: "Can't install xp"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by Schnare on 2007-11-14
Recently I've done a complete overhaul of my system. I wiped my partition containing xp because it was completely non-functional and before that so horribly crippled that it was near unusable. My problem is this: I've reinstalled Ubuntu (Gutsy) and am quite happy with the way things are running other than some 3d acceleration issues, I want to install XP so I can use steam but I can't even load the installer, it freezes after "setup is determining your hardware configuration". 
Is there any way to remedy this without having to wipe my Ubuntu partition?

-Thakns

---

### Post by Inxsible on 2007-11-14
Do you have some unallocated space or ntfs partition where you can install XP ?

I don't think that the XP install Cd recognizes the EXT3 partitions that Ubuntu lies in. Also, since you are installing XP after Ubuntu, you might face issues with MBR and you will have to fix it accordingly.

---

### Post by Schnare on 2007-11-14
I think it's fat 32 for my xp partition 
I had xp installed there before and I haven't changed the partitions, just wiped them.

---

### Post by Inxsible on 2007-11-14
Can you login to you Ubuntu OS and then post the output of the following command
```
sudo fdisk -l
``` -l is lowercase L

---

### Post by Schnare on 2007-11-14
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc6d7c6d7

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1824    14651248+  83  Linux
/dev/hda2            1825        1886      498015   82  Linux swap / Solaris
/dev/hda3   *        1887        3710    14651280    b  W95 FAT32
/dev/hda4            3711        9729    48347617+   b  W95 FAT32

---

