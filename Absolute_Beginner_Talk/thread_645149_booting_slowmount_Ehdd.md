---
title: "booting slow/mount Ehdd/"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by psakhil on 2007-12-19
Hai everyone

	I am new to Linux and I have installed Ubuntu 7.10 and I am trying to get my way around in 	the free world. and I am enjoying it really well, but I am having some series of problems...

after the boot loader OS login window coming almost 4 minutes after..I don't know why it taking that long?I am using acer aspire1680 laptop

I have Seagate 360Gb External Hard disk, which I have been using with Windows XP, and I guess the format NTFS, important thing is all my documents and music are in that drive, how can I mount that to my new OS.

Disk /dev/sda: 60.0 GB, 60011642880 bytes 
255 heads, 63 sectors/track, 7296 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xdd7edd7e 

Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        3442    27647833+   c  W95 FAT32 (LBA) 
/dev/sda2            3443        4658     9767520   83  Linux 
/dev/sda3            4659        4840     1461915   82  Linux swap / Solaris 

Disk /dev/sdb: 320.0 GB, 320072933376 bytes 
255 heads, 63 sectors/track, 38913 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x170a8ae2 

 Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1       38913   312568641    c  W95 FAT32 (LBA) 
 
my ATI MOBILITY RADEON 9700 - 64 MB DDR video memory is in the restricted drives so I can't able to put extra visual effects, how can I install the graphic driver for it.


I hope you will help me out with this problems I am having.


thanks very much

AK

---

### Post by spiderbatdad on 2007-12-19
i have found removing "quiet" and "ro quiet splash" from /boot/grub/menu.lst solves the same problem for me.

---

### Post by agerg on 2007-12-19
try the steps given on this page:[http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075)
worked like a charm for me :)

---

### Post by psakhil on 2007-12-19
thanks very much for your quick replay, but I am not really understood your replay, forgive my ignorance. I am just started to using Linux from last week. thanks once again..

---

### Post by spiderbatdad on 2007-12-19
i just followed the thread linked above and restored my original /boot/grub/menu.lst and it worked like a charm.


Sounds like your usplash settings are messed up.

Check /etc/usplash.conf

xres=1024
yres=768

Should match what ever your screen supports, if it doesn't then this is causing the problem and needs to be changed.

Once you have changed it u need to update the theme with

Code:

sudo update-usplash-theme usplash-theme-ubuntu

[B]
so... open a terminal and enter[/B]```
gksu gedit /etc/usplash.conf 
``` then change xres, yres to match your screen probably 1024, 768. Then hit save. Then in the terminal run the above sudo command...sudo update-usplash-theme...blah, blah, blah

---

### Post by psakhil on 2007-12-19
thanks

---

### Post by psakhil on 2007-12-20
thanks everyone, i have managed to solve everything...thanks once again...

---

