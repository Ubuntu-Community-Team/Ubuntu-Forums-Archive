---
title: "Dual Boot issues"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by hattrick on 2007-09-23
hello, im real new to ubuntu, and already im stuck.... i have three hdd, and xp is on the third hd (sata) in the second partition.  ubuntu is on the first hdd.   anywho... it wont boot xp anymore.
menu.lst gives this
fdisk gives this....
# on /dev/sda5
title		Windows NT/2000/XP
root		(hd2,4)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1 


Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1216     9767488+  83  Linux
/dev/hda2            1217        1465     2000092+  82  Linux swap / Solaris
/dev/hda3            1466        4865    27310500   83  Linux

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       32541   261385551    7  HPFS/NTFS
/dev/sda2           32542       36480    31640017+   f  W95 Ext'd (LBA)
/dev/sda5           32542       36480    31639986    7  HPFS/NTFS

Disk /dev/hdb: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         784     6297448+  42  SFS


any help is appreciated...

---

### Post by ddrichardson on 2007-09-23
Grub has the wrong partition.```
title        Windows NT/2000/XP[COLOR=Red]
root        (hd2,4)[/COLOR]
``` should be hd2,1 shouldn't it?

---

### Post by hattrick on 2007-09-23
tried that gave error

Error 12: Invalid Device

yeah,

---

### Post by Sef on 2007-09-23
> hello, im real new to ubuntu, and already im stuck.... i have three hdd, and xp is on the third hd (sata) in the second partition. ubuntu is on the first hdd. anywho... it wont boot xp anymore.

XP needs to be on the frst primary partition from what I remember.

---

### Post by alienexplorers on 2007-09-23
WHich disk do you have as master, slave, and third drive.  Basically what disk is your primary boot disk.

---

### Post by ddrichardson on 2007-09-24
Well spotted Sef, yeah he's right - Windows XP needs to be on the primary.

---

### Post by louieb on 2007-09-24
If I remember right XP just needs to be install on a primary partition. There are people out there that Dual  boot XP  and VISA. 
And if you jump thought some hoops you could even install it in a logical partition. 

 Please post you /boot/grub/device.map

Just looking at the fdisk my wild *ss guess today is XP is on sda1 so I'd try **root (hd1,0)  **and adjust the map statements accordingly.

---

### Post by dn_desaku on 2007-09-24
I suffered a similar (but not exactly the same) problem where Vista would not boot. Apparenty, GRUB freaks out when I shrink my partition again to make another one. Anyway, I solved this with EmergencyBoot CD's Smart Boot Manager. I was able to boot Vista and I able to solve all the problems. In your case, if you can't solve the problem with GRUB, try running a boot manger off a floppy or use EBCD.

---

