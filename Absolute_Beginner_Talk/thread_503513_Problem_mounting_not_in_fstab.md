---
title: "Problem mounting not in fstab"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by bobabot1 on 2007-07-18
I'm trying to fix an external hard drive for a friend.

She mainly used it on her mac, but said that it worked on a pc. I borrowed it for a couple of weeks to use on my old windows machine. When I gave it back, she said that it no longer worked on her mac or windows boxes.

I'm trying to get it to mount on my main feisty computer but it really doesn't want to be read. I tried```
sudo fstab -l
``` but it didn't read anything more than my partitions on my main hard drive.

What can I do?

---

### Post by wolfen69 on 2007-07-18
```
sudo apt-get install ntfs-3g ntfs-config
```
there will be an ntfs config tool in Applications-->System Tools  you can configure the drive from there.

---

### Post by bobabot1 on 2007-07-18
I installed NTFS Configuration Tool and checked the box for writing to external drives but I still can't find my external drive.

---

### Post by bobabot1 on 2007-07-19
I tried restarting with the drive in and powered on and nothing seems to have changed.

---

### Post by jombeewoof on 2007-07-19
does fdisk read external drives? 
try sudo fdisk -l check for /dev/sda or something similar

---

### Post by bobabot1 on 2007-07-19
> **jombeewoof said:**
> does fdisk read external drives? 
try sudo fdisk -l check for /dev/sda or something similar

It only sees my main drive and its partitions.

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1245    10000431   83  Linux
/dev/sda2            1246        1369      996030   82  Linux swap / Solaris
/dev/sda3            1370        5285    31455270    b  W95 FAT32
/dev/sda4            5286       13118    62918572+   b  W95 FAT32

```

---

