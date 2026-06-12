---
title: "Seriously, getting an iriver to work"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by SexyLexie on 2007-11-14
I have found many topics on this, but none of them were very helpful.
I have an iRiver H10. When I plug it into my laptop, nothing happens. As far as I can tell, the system is completely unaware of its existence. How, in total noob terms, can I get this damned thing to work?

---

### Post by Inxsible on 2007-11-14
I think Amarok has built in support for IRiver, but I am not sure if it is for your specific model.

Connect the device via a USB. and then do```
sudo fdisk -l
```-l is lowercase L. Post the results here.

---

### Post by philinux on 2007-11-14
also try [FONT="Microsoft Sans Serif"]lsusb[/FONT] sometimes this wakes usb up

---

### Post by LeeM on 2007-12-01
Hi,

I don't mean to horn in on someone else's thread, but I also am having IRiver grief (Gutsy Gibbon).. Here is what I get when I do sudo fdisk -l: (I'm running dual boot with Windoz)

[INDENT]Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2           23167       24321     9277537+   c  W95 FAT32 (LBA)
/dev/sda3            5100        5736     5116702+   b  W95 FAT32
/dev/sda4            5737       23166   140006475    5  Extended
/dev/sda5   *        5737       19626   111571393+  83  Linux
/dev/sda6           22814       23166     2835441   82  Linux swap / Solaris
/dev/sda7           19627       22813    25599546   83  Linux

Partition table entries are not in disk order

Disk /dev/sdf: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000880a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1        6709    53890011    c  W95 FAT32 (LBA)
/dev/sdf2            6710       15633    71682030    f  W95 Ext'd (LBA)
/dev/sdf5            6710       15633    71681998+  83  Linux[/INDENT]

When I do lsusb I get the following (but no response to IRiver):

[INDENT]Bus 002 Device 005: ID 058f:6362 Alcor Micro Corp.
Bus 002 Device 002: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 0c0b:2bcf Dura Micro, Inc. (Acomdata)
Bus 001 Device 008: ID 047d:102a Kensington
Bus 001 Device 007: ID 099a:610c Zippy Technology Corp. EL-610 Super Mini Electron luminescent Keyboard
Bus 001 Device 009: ID 10d5:000d Uni Class Technology Co., Ltd
Bus 001 Device 005: ID 04b8:0122 Seiko Epson Corp.      [/INDENT]

So it sees the device on USB, but doesn't do nada!
Any thoughts?

---

### Post by LeeM on 2007-12-01
Just noticed, I didn't copy the most important entry in lsusb response - the iRiver entry:

Bus 002 Device 006: ID 4102:2102 iRiver, Ltd.

Sorry!

---

### Post by shankariyer on 2007-12-18
Any update on this ? I've pretty much the same output/result. lsusb does report about iRiver, and ??

---

