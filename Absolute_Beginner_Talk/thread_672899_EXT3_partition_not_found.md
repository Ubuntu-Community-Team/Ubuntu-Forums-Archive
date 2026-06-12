---
title: "EXT3 partition not found"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by antrax on 2008-01-20
Hi! I am a noob when it comes to UBUNTU. I want to install it bu when the setup reaches the part where i have to choose a partition where the ubuntu should be installed there is none. I used Partiton Magic on WIN to create an ext3 partiton but the setup doesnt recognise it. in the list i can only see something that says dev/. Any help is well apreciated.

---

### Post by forestpixie on 2008-01-20
choose manual - then use the partition you know you've created, edit partition give it / as a mountpoint and let the installer format it

---

### Post by frup on 2008-01-20
is it like /dev/sda1 or /dev/hdb2 or like that?

/dev/ is short for devices and sda1 is like storage device 1 partition 1
hdb2 is like hard drive 2 partition 2 (i think sata drives use the sd version where ide drives use hd version)

---

### Post by antrax on 2008-01-20
My problem happens when i choose manual. When i selsect manual i can only see /dev/sda1

---

### Post by forestpixie on 2008-01-20
open aterminal - in apps >accessories and paste this in

sudo fdisk -l

post the output, but it sounds like partition magic didn't do anything to me

---

### Post by antrax on 2008-01-20
here is the output

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x921f921f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        4866    28844707+   f  W95 Ext'd (LBA)
/dev/sda5            1276        3800    20282031    b  W95 FAT32
/dev/sda6            3800        3944     1164649+  82  Linux swap / Solaris
/dev/sda7            3945        4866     7405933+  83  Linux

---

### Post by forestpixie on 2008-01-20
ok - so it did then :)

make sure you've closed the installer, open gparted from terminal (type gparted and then enter)

and use that to reformat sda6 and 7 - if they're mounted it won't work, right click and unmount if necessary

alternatively delete the 2 partitions and get the installer to use the free space

---

### Post by antrax on 2008-01-20
gparted didnt work. But i managed to delete them with Disk Managment from WIN and now i have installed UBUNTU on my pc. Thanks guys :)

---

### Post by forestpixie on 2008-01-20
glad you're sorted then - can you mark thread please

---

