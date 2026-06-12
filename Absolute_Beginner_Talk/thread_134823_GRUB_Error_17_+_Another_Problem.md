---
title: "GRUB Error 17 + Another Problem"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by Osias on 2006-02-22
Last week Windows decided that it was my turn for the Blue Screen of Death, and told me on every boot that i had an UNMOUNTABLE_BOOT_VOLUME error. I tried everything including bootable floppy's, but nothing worked.

So two days ago a guy i know brought around his PC, so that i could put my harddrive in and access the files out of my partition, and perhaps even fix Windows.

He has a 40GB HD, and my one is a 20GB. He has two partitions. One with Ubuntu, and the other with XP Proffesional, like mine.

So we decided to try access my files through his XP OS first, but it wouldn't load up the login screen. So once that had failed we went into ubuntu, saw Windows in /Media, and then mounted it. I was sucessfully able to grab the important files off my HD.

But that didn't fix the problem, and i have deadlines to meet. So i though for the next few week's i would borrow his PC untill i got mine fixed, and use Ubuntu, and WINE to run the applications i need. Sadly, however, i couldn't see Windows in /Media anymore.

What's even worse is that when ever i take my HD out of his PC and boot it up, GRUB gives me an Error 17.

So the point of this topic is to ask;

Why is GRUB giving me an Error 17 When ever i take my own HD out of his PC ?
How can i fix this "Windows not showing up in /Media" problem ?

I would really appreciate any advice.

Cheers

---

### Post by Greg T. on 2006-02-22
Regarding the GRUB error, check your boot order in BIOS. I keep Ubuntu and Windows on separate (removable) drives, and if I pull one out, my boot order in BIOS gets juggled.

---

### Post by Osias on 2006-02-22
Thanks for the advice Greg T, i'll give it a try now.

Anyone else have advice regarding my Windows partition not showing up in /Media ?

---

### Post by Osias on 2006-02-23
Ok i've saughted out my Partition not showing up problem. Had to add a line to fstab.

Anyway, i went into BIOS, yet sadly there's no option for Boot Ordering partitions.

So i'm stuck.

Does anyone know what the hell i have to do ?

---

### Post by Bartender on 2006-02-23
regarding your windows machine, you say you tried everything so I don't want to beat a dead horse.  Did you go thru the Recovery Console to fix the MBR?  I had this exact same prob a while back.  This in W2K - I think a coupla steps are dif in XP 
From my notes:
1 - Change boot order in BIOS
2- Windows CD in DVD tray
3- F8 at the "For troubleshooting and advance startup options" window
4- "R" to repair
5- Next screen - "C"
6- Next screen - "1"
7- password
8- Computer says    C:\WINNT
9- here's where I had some problems.  The exact command was not what I'd read form the internet, and I don't think this is the exact cmd for XP either.  The exact command for W2K was   C:\WINNT>CHKDSK C: /P
That's with a **space** between CHKDSK & C: and another **space** between C: & /P  But the command may be dif in XP

Did you already do this or something similar?

Have you tried a Search in the forum for "Grub Error 17"?  I remember seeing that term come up several times in the last month

---

### Post by DiscoKiller on 2006-02-23
Just had a quick google, dont know if this will help or how to alter anything like this bu if anyone can help you from this here it is :)

GRUB error 17


This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

Be sure to check your root(x,y) settings in your grub.conf.

Also, if you are trying to boot Windows, make sure that your grub.conf file has the root (hdX,Y) (or rootnoverify (hdX,Y)) and chainloader (hdX,Y)+1 in it. 


DK

---

### Post by Osias on 2006-02-23
Bartender - The XP disc i have doesn't work, either that or my CD Drive is screwed. So i'll try to get my hands on another.

DiscoKiller - Where do i find my Grub.Conf file ?

---

