---
title: "[SOLVED] Ubuntu is driving me crazy!!"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by cptInsane0 on 2007-07-26
Ok, I am about to start pulling my hair out.  I have tried many different ways to install ubuntu on my system.  First, I had a fakeraid setup running my windows, but tried to install Ubuntu on the master IDE drive instead.  The installation always worked, but I could never boot into it.  I was using the method where you create a file based off of the boot info.  I did it from the partition, I did it with a working boot disk that I created, but nothing.  

Anyway, I have been way overdue for a windows reload.  Today, I deleted my raid array, causing my system to be set up as follows:

CPU: AMD Athlon 64 4200+ dual core(939)
RAM: 2GB Kingston Hyper X
MB: Asus A8N-SLI Premium
VC: ATI X1900 All in Wonder
Hard drives:

Primary Master: 120GB IDE drive --hd0
Primary Slave: 200 GB IDE drive--hd1

Sata1: 160GB SATA2--hd2
Sata2: 160GB SATA2--hd3

That is the order they show up in the bios, as well as in ubuntu. First I tried to install them both on the same hard drive(hd2).  I installed windows on an 80GB partition, and set up the rest as Ubuntu.  In the advanced options, I set grub to install on (hd2), which is the drive I have set to boot first.  It boots into windows without a problem.  After I installed ubuntu and restarted, the grub menu came up.  I chose Ubuntu, and it said partition not found or something like that.  I think it was error 22.  Well crap I thought, so I reset and tried to load xp.  Same error message.  I started the livecd and went into gparted, and made sure I had the linux partition set to boot.  I set it to boot, and restarted.  Now I got error 21, saying it couldnt see the disk.

Finally, I decided to just install xp on the first 160gig and then use the second for ubuntu.  I already installed xp, and its working fine.  My question is, when I set up ubuntu on the second drive, where do I need to install grub, and do I need to partition it first and set the boot flag in gparted?  Last night I installed ubuntu with wubi and it worked without a problem.  It was just way too slow for my taste.  

Sorry for the long post, but I have already tried a lot and hoped to narrow things down for everyone.  Another thing that I noticed, when I was installing xp, both hard drives were listed as id0 on bus0.  Also, last time I installed Ubuntu, I tried to have it format the other 160 as fat32 to be my shared drive, and it couldn't do it.  I had to start the installation over and not do it.  Do I maybe need to use the sillicon image sata controller instead of the nvidia?  Hopefully this thread will get enough views to where I can get some answers.  I use Ubuntu at work and really like it and want to know more about it, but this is becoming a huge hassle and maybe two people that have viewed my various threads on this forum and another one have even bothered to respond.  Thank you anyone that helps in advance. :confused:

---

### Post by Jeek Elemental on 2007-07-27
Ubuntu installer and grub seem to disagree on drive numbering, possibly because of changed order in bios.

press e in grub to edit the settings, look for 

root		(hd<x>,<y>)

from your post I expect it says (hd2,0)?

Try changing it to (hd0,0) by pressing e again and editing, then enter and b to try booting. Changes are not saved so dont worry about messing it up.

The above assumes you still have hd2 as 1. boot drive in bios and that ubuntu is on its 1. partition.
Change <y> to reflect partition number (starts at 0) if not the first.

once you can boot into the desktop, you can change menu.lst permanently to the right drive.

---

### Post by cptInsane0 on 2007-07-27
I will try that, thank you.  Although when I used the livecd, i went in and checked the menu thing and the drives looked right. I'll try it this way though.

---

