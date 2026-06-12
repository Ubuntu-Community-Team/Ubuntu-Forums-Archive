---
title: "Installed Ubuntu On Sata Drive, Will Not Boot"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by zorgan on 2007-08-18
Hi Guys,

I Have Windows XP on raid 0 on sata 3 and 4 slots,

I installed Ububtu on a 200GB Sata on "FIRST SATA" in the sata chain....

now.....

I installed Unbuntu, the drive would not boot, i looked up some answers,

I installed GRUB into the Raid 0 drive edited the boot.ini within windows xp to load grub, however when it loads it thinks the drive is NTFS, I think it may be looking at the wrong drive(s)?

I have no idea what i need to do next, is there a way for it to check ALL the hard drives as i think it is not checking the First SATA which i installed UBUNTU onto.

I`ve been at this for hours, i really really hope somebody here can explain what i need to do....

TIA!!!

THIS IS A SCREENSHOT OF THE CONFIG OF MY HARD DRIVES!

[http://img175.imageshack.us/img175/395/linuxjh0.jpg](http://img175.imageshack.us/img175/395/linuxjh0.jpg)

Here.....

Thanks.

---

### Post by zorgan on 2007-08-19
help!!

Was hoping to fix this i will be really thankful! :)

---

### Post by TL_Mechanic on 2007-08-19
Zorgan,

I had a problem at first install with recognizing SATA drives.  In my case it would recognize the first SATA device but none of the others.  I ended up fixing it by making a change in the BIOS.  Default for SATA mode was IDE.  I switched it to AHCI and all was well.  Don't know if this will help, but it's easy to try and easy to put back if it doesn't work.

Tony

---

### Post by Duck2006 on 2007-08-19
When you edited your menu table did you tell where the root partition of ubuntu was?

ie:
root (sd0,2)
chainload +1

---

### Post by zorgan on 2007-08-19
sounds like you know what your talking about, no i did not do that, would that be the menu.lst file?

where about is my menu.lst file and how/where do i edit it please mate? :)

thanks!!!

---

### Post by Duck2006 on 2007-08-19
From the live CD run the 

code
sudo fdisk -l

to fine where the root partition is of ubuntu

Then boot into windoze
Open wingrub you will see the menu table
point the mouse in the square and right click then click edit
and edit the menu table

---

### Post by zorgan on 2007-08-19
here is a screenshot

[http://img408.imageshack.us/img408/376/linux2oh8.jpg](http://img408.imageshack.us/img408/376/linux2oh8.jpg)

I loaded the menu.lst from my "J" drive and wingrub has somehow created J:\Grub\menu.lst file in there, however my "J" drive is only used for storing TV Episodes :|

is something wrong going on here?

---

### Post by Duck2006 on 2007-08-19
Yes, because you have only windows in your wingrub
you have to edit the menu table in wingrub for ubuntu
delete the line windows at (0,0)
and change it to where the root partition of ubuntu is

Your boot.ini file loads windows so your using wingrub to load ubuntu

---

### Post by zorgan on 2007-08-19
any chance you can post what i need to type, i`m really sorry i need step by step sorry for wasting your time and i really do apprechiate your help, i`m totally new to this kind of thing, i`m a wizz in xp but not in anything to do with Linux lol

is this what it should look like then?

[http://img512.imageshack.us/img512/7046/linux3ax0.jpg](http://img512.imageshack.us/img512/7046/linux3ax0.jpg)

---

### Post by jake16424 on 2007-08-19
> **zorgan said:**
> Hi Guys,

I Have Windows XP on raid 0 on sata 3 and 4 slots,

I installed Ububtu on a 200GB Sata on "FIRST SATA" in the sata chain....

now.....

I installed Unbuntu, the drive would not boot, i looked up some answers,

I installed GRUB into the Raid 0 drive edited the boot.ini within windows xp to load grub, however when it loads it thinks the drive is NTFS, I think it may be looking at the wrong drive(s)?

I have no idea what i need to do next, is there a way for it to check ALL the hard drives as i think it is not checking the First SATA which i installed UBUNTU onto.

I`ve been at this for hours, i really really hope somebody here can explain what i need to do....

TIA!!!

THIS IS A SCREENSHOT OF THE CONFIG OF MY HARD DRIVES!

[http://img175.imageshack.us/img175/395/linuxjh0.jpg](http://img175.imageshack.us/img175/395/linuxjh0.jpg)

Here.....

Thanks.

go into the boot menue of your bios, and select the 200gig,, haha.. thats what i had todo.. =-\ then again i have 2 satas, and one ide.. i had my version on the IDE.. so,, might work for your application as well?

---

### Post by Duck2006 on 2007-08-19
In the live cd post the output to

Applications > Accessories > Terminal and type

sudo fdisk -l

---

### Post by zorgan on 2007-08-19
hi duck

this is what was outputted

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24230   194627443+  83  Linux
/dev/sda2           24231       24792     4514265    5  Extended
/dev/sda5           24231       24792     4514233+  82  Linux swap / Solaris

Disk /dev/hdb: 300.0 GB, 300090728448 bytes
224 heads, 63 sectors/track, 41533 cylinders
Units = cylinders of 14112 * 512 = 7225344 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       41533   293055304+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19458   156296353+   7  HPFS/NTFS

---

### Post by Duck2006 on 2007-08-19
In windows open wingrub
The box where you see Menu Table on the left at the bottom
put the mouse pointer in the box and right click
then click on edit and enter this in the box

root (hd1,0)
chainload  +1

then save and reboot the system

---

### Post by zorgan on 2007-08-19
okay it seems it`s already set at that

timeout 10

title Unbuntu at (hd1,0)
root (hd1,0)
chainloader +1

I`ll try boot into Linux and take a pic of whats on the screen

---

### Post by zorgan on 2007-08-19
okay it seems when i try to boot ubuntu

it still thinks it`s on hd2? (i see a flash of HD3 trying to load something i think then HD2) it flashes real fast the screen then goes to HD2 cant load after that........

even though my wingrub has been set to hd1 as you told me to set it....

i sent you a personal message on here with my msn if you can help there? :)

---

### Post by zorgan on 2007-08-19
Still Unsolved :(:confused:

Still I have not resolved my issue, i`m just hoping there is somebody out there who can resolve it plain as, I`m willing to give any more info on this as i possibly can.........

---

### Post by Duck2006 on 2007-08-21
[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)

This may help

---

