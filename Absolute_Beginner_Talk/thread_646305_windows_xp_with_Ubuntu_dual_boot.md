---
title: "windows xp with Ubuntu dual boot"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by everest on 2007-12-21
Hola,
I had installed Windows XP on a single 40 GB hard disk. I created one primary partition that is C: drive and one extended partition and one logical partition D: drive. Windows XP is installed on C: drive. Now I installed Ubuntu Feisty Fawn on the remaining free space. I chose manual partition and created one swap partition of 500 MB and one ext3 partition and set its mounting point as / (root). After installing Ubuntu I reboot the PC to start Windows and when I select Windows XP from the GRUB boot loader list, it doesn't boot into Windows. I have tried playing with /boot/grub/menu.lst but no results. What could be wrong here? Ubuntu boots and I can access Windows XP files. 
Cheers

here is the output of fdisk -l command.
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 1912 15358108+ 7 HPFS/NTFS
/dev/sda2 1913 4865 23719972+ f W95 Ext'd (LBA)
/dev/sda5 1913 3187 10241406 7 HPFS/NTFS
/dev/sda6 3249 4865 12988521 83 Linux
/dev/sda7 3188 3248 489951 82 Linux swap / Solaris

---

### Post by Sef on 2007-12-21
Check out [Super GRUB Boot Disk]("http://ubuntuforums.org/showthread.php?t=640824").  It is very easy to use if you follow the instructions.  If you have any questions, please post them.

---

### Post by mikewhatever on 2007-12-21
If you want help, please post your menu.lst here, at least the relevant part.

> sudo cat /boot/grub/menu.lst

---

### Post by everest on 2007-12-21
Thank you for offering your help, I solved this problem. Some mysterious changes I did to the menu.lst file and now I can dual boot windows and ubuntu.

---

