---
title: "Ready to install - dual boot need help"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by 3pinner on 2008-01-30
First off - Thanks for the help!!
Iam getting ready to install ubuntu 7.10
Will dual boot with windows 2000

I have 2 books that describe an install, both of them assume I want to install Ubuntu to the same hard disk that has Windows.

I have two seperate hard drives - both SATA, Windows lives on one, the other is for Ubuntu.
I do not want Ubuntu to resize/reformat any part of the Windows hard disk. I want to load Ubuntu on Disk 2.

How do I direct the wizard to install to the second hard disk?
 (I need help in recognizing how the wizard will designate that disk.)

Should I just disconnect the Windows drive before installing Ubuntu?

I will format that disk with 3 partitions, one for the OS, one for the swap, one for my files. (seems logical to do it that way)

Anything to watch out for regarding GRUB? 
The last time I tried to set up a dual boot, it was a disaster.
GRUB somehow got messed up, NTLDR was removed from Windows. It wasn't fun getting everything all patched together.

Any specific direction will be helpful.

THANK YOU again for the help.

Bruce

---

### Post by oedha on 2008-01-30
you dont need to unplug the disk
just go on by installing the ubuntu from live cd
on the 4 of 7 step......choose manual
then you can manage the partition as you wish on the 2nd hd
it means...you will create / , /home , / swap

regards;
~E~

---

### Post by wolfen69 on 2008-01-30
you ***could*** unplug the windows disk then just choose "use entire disk" for ubuntu. then plug the windows back in, and choose which drive to boot to from quick boot menu or bios.

or as oedha said, choose manual, highlight the ubuntu drive, make new partition,(/) size it, leave about a gig for swap, then you will have 1gig unallocated left for swap. highlight it and choose new partition, and make it swap. you dont need to make a home partition if you want to keep it simple. done.

---

### Post by jimrz on 2008-01-30
I have 1 box with 2 SATA2 drives with XP on 1 + ubuntu on the other. When I first installed ubuntu (6.10 at the time, but worked with 7.04 + 7.10 also) on this machine my BIOS and  GRUB did not get along at all. To solve this I, in fact, had to: 

1- unplug the XP drive 
2- plug the drive for ubuntu into the first SATA port
3- install ubuntu
4- plug the XP drive into a second SATA port (had to leave the ubuntu drive in the first port so as not to confuse GRUB)

This has worked out quite well and completely eliminates any chance of fouling up your win mbr. I simply used my BIOS setup to make the ubuntu drive the 1st boot option and go into setup to select the XP drive when I want to boot there. Since I very rarely boot to XP anymore, this is actually a bit quicker( and requires fewer keystrokes when selecting XP)  than a standard dual boot setup.

Regarding partitioning, I would suggest 4 partitions for your ubuntu drive = "/" "/home" "swap" + 1 for your data. A separate "/home" can come in handy.

---

### Post by 3pinner on 2008-01-31
Thank you for the tips.
I've decided to go ahead and just try the dual boot install.
But this time I'm copying my whole Windows HD to another disk just in case. 
If the install screws up again, I'll just swap disks and go back to work.

I'll post back with results to help others with the same question.

---

