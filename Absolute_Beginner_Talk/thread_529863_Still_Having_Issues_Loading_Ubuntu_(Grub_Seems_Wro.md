---
title: "Still Having Issues Loading Ubuntu (Grub Seems Wrongly Configured)"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by zorgan on 2007-08-19
Hi guys, 

recently i installed Ubuntu for education purposes, I wanted to dual boot with Windows XP 

I installed Ubunto on a spare sata drive i have, however once installed the computer wouldn`t boot from the Ubuntu Drive for some reason. 

no idea why, i`m compleatly new at this......... 

So i found a little program for dual booting called "Wingrub" 

I`ve tried to configure it, menu.lst file etc although i still can`t seem to get it to boot my install of Ubuntu 

Was Wondering If anyone out there has the knowledge of linux and grub and how to configure it all. 

if they require any info i can post it, so far i have this info 

sudo fdisk -l 

displays.......... 

Disk /dev/hda: 320.0 GB, 320072933376 bytes 
255 heads, 63 sectors/track, 38913 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 

Device Boot Start End Blocks Id System 
/dev/hda1 1 38913 312568641 7 HPFS/NTFS 

Disk /dev/sda: 203.9 GB, 203928109056 bytes 
255 heads, 63 sectors/track, 24792 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 

Device Boot Start End Blocks Id System 
/dev/sda1 * 1 24230 194627443+ 83 Linux 
/dev/sda2 24231 24792 4514265 5 Extended 
/dev/sda5 24231 24792 4514233+ 82 Linux swap / Solaris 

Disk /dev/hdb: 300.0 GB, 300090728448 bytes 
224 heads, 63 sectors/track, 41533 cylinders 
Units = cylinders of 14112 * 512 = 7225344 bytes 

Device Boot Start End Blocks Id System 
/dev/hdb1 * 1 41533 293055304+ 7 HPFS/NTFS 

Disk /dev/sdb: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 

Disk /dev/sdb doesn't contain a valid partition table 

Disk /dev/sdc: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 

Device Boot Start End Blocks Id System 
/dev/sdc1 * 1 19458 156296353+ 7 HPFS/NTFS 

My menu.lst file is configured (afaik) to boot from (hd1,0) 

although when i boot, i have a screen 

Windows XP Professional 
Load Grub 

I select Load Grub 

It flashes a screen which i can see something like HD3 somewhere on the page 

then says some error about it not being able to load i think it`s now looking at HD2 at this point......... 

I hope somebody can help!

---

### Post by Paul133 on 2007-08-19
How many drives do you have? It appears, from fdisk -l, that you have a 320 GB drive with XP, a 200 GB drive with Ubuntu, a 300 GB drive with XP, and a 80 GB drive with nothing.  So, can you access Ubuntu (if not, where did ou run 'sudo fdisk -l' from)? If so, post your /boot/grub/menu.lst file.

---

### Post by Lithium17 on 2007-08-19
you should just have created a partition within the ubuntu installer, then you wouldnt have any problems.

---

### Post by Paul133 on 2007-08-19
If you have a spare drive and want to dualboot, there's no reason to shrink XP.

---

### Post by zorgan on 2007-08-19
ok this is my drive config on my system


I have 2 80gb sata in raid 0 (stripe) runs windows xp

I have 320gb (MP3 Drive) Formatted NTFS

I have 300gb (Tv Series) Formatted NTFS

I have also another 200GB Sata which Ubuntu is on,

I used sudo fdisk -l command from the boot cd environment.

My Menu.lst file is on the J drive - Which is the 300gb Tv Series drive, it installed here, i`m not sure if it is supposed to be there also, Wingrub put it there and created the path J\Grub\menu.lst

hope this info helps.

---

### Post by zorgan on 2007-08-20
any idea why i`m having issues dual booting?

---

### Post by Paul133 on 2007-08-20
I'd reccomend you try the Super GRUB disk. That might help.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by alienexplorers on 2007-08-20
The menu.lst file should be in your /boot/grub file on your linux partition.  If it is not there try to move it to that location.  You may need to reset grub by booting your install cd and running terminal.  In terminal type sudo grub.
Enter > find /boot/grub/menu.lst
root (hd#,#)
setup (hd#)

---

### Post by zorgan on 2007-08-21
ok then my menu list file is on the wrong drive, it`s on an NTFS drive, so do i have to mount my linux partition in windows before i re-install wingrub then?

how would i go about that?

---

### Post by zorgan on 2007-08-25
I solved the issue, apparently (just wondering why nobody knew this)

Ubuntu

does not like the line

Chainloader+1

within the Menu.lst file.

---

