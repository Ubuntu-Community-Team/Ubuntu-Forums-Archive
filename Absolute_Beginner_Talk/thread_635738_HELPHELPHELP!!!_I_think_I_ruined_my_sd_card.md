---
title: "HELPHELPHELP!!! I think I ruined my sd card"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Watchtow3r on 2007-12-09
I was trying to install Ubuntu onto my sd card using [this]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") guide. However, in the terminal editing my sd card data, I hit a wrong number and pressed enter. So, I figured, "ok, I'll just format it. That'll erase everything and I can start again." I did that, and now, when I go back to fdisk -l , it's showing this for the sd card:


Disk /dev/mmcblk0: 2032 MB, 2032664576 bytes
4 heads, 16 sectors/track, 62032 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   ?    12158374    29994462   570754815+  72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/mmcblk0p2   ?     2635774    32886216   968014120   65  Novell Netware 386
Partition 2 does not end on cylinder boundary.
/dev/mmcblk0p3   ?    29216898    59467339   968014096   79  Unknown
Partition 3 does not end on cylinder boundary.
/dev/mmcblk0p4   ?    45088769    45089636       27749+   d  Unknown
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order



I think I messed up my sd card. Is there any way to get it back to normal? Please help!

---

### Post by Watchtow3r on 2007-12-09
please some1 help

---

### Post by clauguia on 2008-01-22
It seams to me that you just have to follow the guide again. Just type fdisk /dev/yoursdhere and follow the rest of the commands on the tutorial. This will write a partition to your sd card again.

---

