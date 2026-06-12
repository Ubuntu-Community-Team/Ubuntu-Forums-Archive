---
title: "grub / dual boot (winXP + Ubuntu 7.04) question"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by pecoronas on 2007-04-21
dear everybody,

i am an absolute beginner and i need some help for my dual boot system.
this is my system:

motherboard ASUS A7N8X-E Deluxe
CPU AMD Athlon XP 3000+
HDD (1) maxtor 6 Y120M0 SCSI Disk Device (120 GB, 7200 RPM, Serial-ATA/150)
HDD (2) IBM DTTA-371010 (10.1 GB, 7200 rpm, Ultra ATA-33 EIDE )
controller SATARaid silicon image Sil 3112


on the first hard disk (the 120 GB SATA) i have windows xp, with his own mbr and loader. it is formatted in NTFS.
on the other hard disk (the 10 GB EIDE) i have ubuntu 7.04, as automatically installed from the live cd, with his own grub.


when i want to use winXP i have to phisically UNPLUG the EIDE hard disk, because grub doesnt give me the winXP option.
if both disks are plugged, GRUB (hence Ubuntu) is loaded, no matter what the bios boot sequence is.

what commands should i write on the GRUB command line to load windows XP? please note it is a SATA disk, so not conventionally numbered hdx,y, i can't find this particular case on the grub wiki.

---

### Post by mitchell7man on 2007-04-21
Hi, I dual boot with a SATA drive also, i believe the answer lies in "sudo gedit /boot/grub/menu.lst" once there you will need to add the lines 

title		Windows XP Media Center Edition
root		(hd0,x)
savedefault
makeactive
chainloader	+1

(that's strait from my menu.lst) where x is your windows partition... of course youll probably need to change the drive, where mine is hd0 urs might be be different seeing as u are using two drives, you may need to check on that, it may be hd1,1 in your case if your windows partition is secondary, (slave), which it probably is.....again you probably want to double check that the partition is correct and that you are selecting the correct drive, as I am not sure b/c i do it all on one drive (hd0) and i am guessing that if you have another it would be numerated like (hd1) for a second drive........ There are many other ways to dual boot which you may be interested in, like putting your os's on one drive and info on other drive etc. Of course you can always try, it won't hurt to add to the menu.lst worst thing that could happen is you delete it or modify it is your info is not correct. - Just as long as you don't screw up the info for your linux bootloads. - (my windows is also ntsf)

---

### Post by pecoronas on 2007-04-22
i got the solution with these commands, which i post for users with my problem:

title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
chainloader +1
boot


the "map" command is for making windows believe it is on the first disk, without this command windows won't load (in my scsi+eide system the eide disk is considered first, and windows is on the sata).

---

