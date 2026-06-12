---
title: "maintaining ubuntu"
date: 2005-10-07
forum: Absolute Beginner Talk
---

### Post by Vega on 2005-10-07
You know how in the Windows enviroment you have tools such as disk cleanup, Disk Defragmenter, and CHKDSK. Does ubuntu have similar commands or tools to that. that would be recommended to do.

---

### Post by nitricacid on 2005-10-07
I often wondered this myself so i did a search on this forum and found that you don't need to defrag the HD when using a linux box.

I could be wrong though...

---

### Post by aysiu on 2005-10-07
Yes, with Linux filesystems, you don't need to defragment. I noticed that a checkdisk of some sort happens every thirty times I reboot (it happens during bootup). I'm not sure about the cleanup thing, though...

---

### Post by landotter on 2005-10-07
fsck can repair borked drives. Don't run it on mounted partitions, this is a good command to run from a live cd. 

:D

---

### Post by nitricacid on 2005-10-07
[QUOTE=aysiu] I noticed that a checkdisk of some sort happens every thirty times I reboot (it happens during bootup). I'm not sure about the cleanup thing, though...[/QUOTE]

I have noticed this happen on my system aswell and have been meaning to post about it but keep forgetting to, looks like i don't have to now.

---

### Post by Vega on 2005-10-07
self maintanence.

ubuntu is like having OSX. Except there is no price tag ^^

---

### Post by dasunst3r on 2005-10-07
The beauty of Linux is that there is no need for that time-consuming maintenance.  Anything necessary will "automagically" run and you will not even know it!  So what are you going to do with that extra free time?  

P.S. "Where do you want to go today?"  The "Places" menu is easily accessible, so you should know... :)

---

### Post by Vega on 2005-10-07
[QUOTE=dasunst3r]

P.S. "Where do you want to go today?"  The "Places" menu is easily accessible, so you should know... :)[/QUOTE]

An Awesome example!
well done!

---

### Post by Qrk on 2005-10-07
You remember those strange clicking noise that seems to come from your hard drive in Windows? That comes from NTFS, (You can get it in Linux if you read a NTFS drive) NTFS stores data across the whole drive, so as you delete and then add stuff it gradually looses room for it. The clicking comes from the hard disk physically gathering bits from all the different spots on it. Ext3 doesn't have that problem.

---

### Post by Vega on 2005-10-07
[QUOTE=Qrk]You remember those strange clicking noise that seems to come from your hard drive in Windows? That comes from NTFS, (You can get it in Linux if you read a NTFS drive) NTFS stores data across the whole drive, so as you delete and then add stuff it gradually looses room for it. The clicking comes from the hard disk physically gathering bits from all the different spots on it. Ext3 doesn't have that problem.[/QUOTE]

Is that why Redmond is pushing WinFS?

---

### Post by Goober on 2005-10-07
I've often wondered this myself, and was very relieved to discover that you don't need to do Disk Defrag and such.  I always hated doing that in Windows.  Seemed pointless.

Automaintenance is just another reason why I love Ubuntu.

---

### Post by Chippendale on 2005-10-30
[QUOTE=Qrk]You remember those strange clicking noise that seems to come from your hard drive in Windows? That comes from NTFS, (You can get it in Linux if you read a NTFS drive) NTFS stores data across the whole drive, so as you delete and then add stuff it gradually looses room for it. The clicking comes from the hard disk physically gathering bits from all the different spots on it. Ext3 doesn't have that problem.[/QUOTE]

hi, im also new to ubuntu... i had 3 hard drives all with NTFS with WinXP as my OS... last week i changed 1 to ext3 with Ubuntu and the other 2 hard drives i made them to FAT32... all 3 i deleted the partitions and formatted to have a nice clean install. My problem is that i can still hear that weird strange clicking noise, is there a way i can make that stop or work around it?

---

### Post by Breaks on 2005-10-30
Howcome you have the other two in FAT32 for?  I never realised people still used this format lol.

---

### Post by Chippendale on 2005-10-30
cause i could never get another filesystem to mount lol

---

### Post by Breaks on 2005-10-30
Why not format them into ext2/3 ?

---

### Post by towsonu2003 on 2005-10-30
[QUOTE=aysiu]Yes, with Linux filesystems, you don't need to defragment. [/QUOTE]

the filesystem will fragment if your partition is more than 80% full. but i don't know of a tool to defragment. and if there is no tool, then there is no need :) enjoy non-maintenance!

---

