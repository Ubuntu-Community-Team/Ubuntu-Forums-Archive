---
title: "GRUB error17 - GRUB only loads with WinXP CD in drive."
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by BoxCar on 2005-11-19
Hello, I have just installed Ubuntu and from what I have seen of it, I like it. However, I am having the following problem. I have searched the forum for the past two days to no avail...

On boot, I receive a **Grub error 17 message unless the windows XP disc is in my CD drive**. With the CD in the drive, Grub loads fine and I am able to boot into either OS. How do i make it so that Grub loads without having to have the WinXP disc in the drive?

Here's some info:

Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3648    29302528+   7  HPFS/NTFS

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2330    18715693+  83  Linux
/dev/hdb2            2331        2434      835380    5  Extended
/dev/hdb5            2331        2434      835348+  82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321   42  SFS
[LIST]
[*]My Windows XP installation is on /dev/hda (which is my primary drive -- first IDE Master).
[*]I've installed Ubuntu to /dev/hdb (the slave to the aforementioned drive).
[*]I've installed Grub to the MBR of my primary drive.
[*]The /dev/sda drive is simply for storage of media (no OS here).
[/LIST]

Below are the contents of /boot/grub/device.map

[I](hd0)	/dev/hda
(hd1)	/dev/hdb
(hd2)	/dev/sda[/I]

Below is the relevant(?) content of /boot/grub/menu.lst

[I]title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin  
boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
rootnoverify		(hd0,0)
savedefault
makeactive
chainloader	+1[/I]

Please help if you can. It will be greatly appreciated.

---

### Post by campusloop on 2005-11-19
did you try reinstalling grub..

it can be done from withing ubuntu cd by "grub-install --root-directory=/mnt/hdb1 /dev/hda

[http://www.ubuntuforums.org/showthread.php?t=92415](http://www.ubuntuforums.org/showthread.php?t=92415)

---

### Post by BoxCar on 2005-11-20
Yeah, I have tried that.

A buddy of mine suspects that it's probably a SATA drive issue. Possibly due to the way the MB is recognizing the hard drives before loading Grub, i.e. the SATA drive isn't the primary drive (it doesn't even have an OS on it).

---

### Post by jackmacokc on 2005-11-27
[QUOTE=BoxCar]Yeah, I have tried that.

A buddy of mine suspects that it's probably a SATA drive issue. Possibly due to the way the MB is recognizing the hard drives before loading Grub, i.e. the SATA drive isn't the primary drive (it doesn't even have an OS on it).[/QUOTE]

If your system is anything like mine, with a SATA drive in it - it wants to boot to the SATA drive before the PATA drives. Are you absolutely sure you put your grub install on the right drive?

---

### Post by BoxCar on 2005-11-28
I put Grub on the First PATA drive, it's the one that shows up first in the boot order. has windows on it, and is the primary master hard drive.

---

