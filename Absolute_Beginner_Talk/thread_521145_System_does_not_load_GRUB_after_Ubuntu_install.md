---
title: "System does not load GRUB after Ubuntu install"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Thunder0ne on 2007-08-09
Hi all,
I installed ubuntu from the live cd but on system restart the loader failed to run: the system was just stuck at the very first screen, in text mode, showing a list of devices and hard disks etc...
I have two hard disks one of them has windows xp and I chose the 2nd to instal ubuntu.
Both are SATA master config: the windows one on the primary port and the other on the secondary.
I let ubuntu set the partition table of the second HD allowing it to take all the disk for ubuntu installation.
I tried then to start the system from the live CD choosing to start from the hard disk and it successfully showed the correct list of operative system installed in my computer. Choosing both windows XP and ubuntu works.
here is the result of fdisk -l

> Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       16573   112639747+   7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29949   240565311   83  Linux
/dev/sdb2           29950       30515     4546395    5  Extended
/dev/sdb5           29950       30515     4546363+  82  Linux swap / Solaris


Here is a fragment of /boot/grub/menu.lst
> title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=4bf0627e-5157-42f2-bd46-21467bda2175 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=4bf0627e-5157-42f2-bd46-21467bda2175 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


here is the result of cat /boot/grub/device.map
> (hd0)   /dev/sda
(hd1)   /dev/sdb


I would like not to be forced to put ubuntu live CD to start my system.

Many thanks.

---

### Post by Trab on 2007-08-09
i hate grub, even right now i'm having to deal with it, using almost the same solution i'm about to give you.

here is my advice:

boot up your liveCD. open a terminal and type
```

sudo grub-install hd0

```
(that is hd ZERO not the letter O)

i dunno where you keep your /boot section (guess you didnt create a seperate partion, which thus far i cant see making a difference >.<)


the problem appears to be, as you correctly guess, grub is never loaded. if that command does not work, try doing it again with hd1 instead of hd0

let us know your results.

---

### Post by Dedoimedo on 2007-08-09
Hello,
Your disks are sd and your menu.lst shows hd - first problem.
Second, you have two uncommented lines title and root below the end of debian magic list.
Dedoimedo

---

### Post by Thunder0ne on 2007-08-09
It works.
I checked the bios settings and I found that the two hard drives were exchanged in priority in the bootable hard drive list (not the boot priority list)
Actually the question now is : how was it working before?
However now the grub starts on startup and let me choose the operative system to load properly.
Many thanks again.

---

