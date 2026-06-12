---
title: "Partitioning Drive Assistance"
date: 2012-03-19
forum: Any Other OS
---

### Post by devxdev on 2012-03-19
Hey guys like always, back with an extremely random question! But if you guys weren't so damn helpful I wouldn't ask :D

Any ways, I was getting ready to 'tri-boot'; and not using any tutorials for the windows, and ubuntu part of OS installs I just got to Mac OS X Lion 10.7.x and now its telling me I cant edit my NTFS partition? It tells me it cannot be edited due to the use of MBR(Master Boot Record), another reason Im guessing is because the drive already has 4 primary partitions.

Soo after further reading everyone says to install Mac->Windows and then of course we say to do Windows->Ubuntu.

I had an iffy question about a partition on the drive though that i was going to attempt to delete but unsure what it is? does any one know how to look at it in Windows/Ubuntu? (see attachment)

Last note when I boot i have the 2 Linux boots [normal&recovery]
but Windows has the boot from /sda1 AND /sda2 THEN recovery option, but not a recovery option for both...

If I have confused please ask for clarification :D

---

### Post by devxdev on 2012-03-22
[FONT=Tahoma]Never mind, I reformatted the drive and installed/partitioned (in order): [all x64]

[/FONT][FONT=Tahoma]hfs+(Mac Journaled) mac os x 10.7 Lion, 
NTFS Windows 7 Ultimate
ext4(Linux Journaled) Ubuntu 11.10
ext4(swap)[/FONT]

No problems either fyi, all three boot perfectly from grub2 menu :)

---

