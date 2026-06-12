---
title: "WinXP Dual Boot 2 drives"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by jppwt on 2007-07-09
I have added Ubuntu 7.04 on a second SATA drive to an existing WinXP system.  The installation went fine.  The problem I'm having is that when both drives are connected, the system ALWAYS boots to Windows.  I would like it to go to GRUB.  It doesn't seem to matter what I set in BIOS or which SATA drive I set as primary.

Is there any way to get the Linux drive to boot ahead of windows?  Do dual boot systems have to be on the same drive?

Any help would be appreciated.

Thanks,
JPP

---

### Post by dstew on 2007-07-09
Boot an Ubuntu Live CD, and open a terminal. Enter the command **sudo fdisk -l** and post the results on the forum. Do this with both drives connected. This will tell us some drive information. We can then use the information to try to install grub properly. Dual boot systems do not have to be on the same drive, but only grub can dual-boot. The Windows booter will ignore your linux installation.

---

### Post by jppwt on 2007-07-09
Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8294    66621523+   7  HPFS/NTFS
/dev/sda2            8295       20023    94213192+   f  W95 Ext'd (LBA)
/dev/sda5            8295       20023    94213161    7  HPFS/NTFS

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19272   154802308+  83  Linux
/dev/sdb2           19273       20023     6032407+   5  Extended
/dev/sdb5           19273       20023     6032376   82  Linux swap / Solaris

I swapped the drives again in bios.  This time it came up to GRUB, but since I unplugged the WinXP drive when I installed Linux, Grub does not know about Windows.  How do I add it?

Thanks,
JPP

---

### Post by dorath on 2007-07-10
JPP,

My setup is what you've got: 7.04 on one drive and XP on the other (both SATA).  You definataly don't have to have both systems on the same drive! :)

Here is how I got GRUB to boot XP:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
sudo pico /boot/grub/menu.lst
```
The first step makes a backup copy of menu.lst.  The second step opens menu.lst in a text editor.  Lots of people use nano instead of pico (and there's a bajillion other ways to do it).  

This is what I had to add to the very bottom of my /boot/grub/menu.lst:
```
title           XP (Games)
map             (hd0,0) (hd1,0)
map             (hd1,0) (hd0,0)
rootnoverify    (hd1,0)
savedefault
makeactive
chainloader     +1
```

Hope that helps!

---

### Post by jppwt on 2007-07-11
[SIZE="5"]It worked perfectly!  Thanks![/SIZE]

---

