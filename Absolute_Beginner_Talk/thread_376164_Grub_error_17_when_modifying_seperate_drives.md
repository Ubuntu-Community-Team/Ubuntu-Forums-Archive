---
title: "Grub error 17 when modifying seperate drives"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by mark206000 on 2007-03-04
Hi i'm new to linux and ubuntu.  Want to get away from windows and their new vista c*** 

I've just installed it with xp to get me started so I can learn it over time, some programs I use will only run on windows as well.


Problem is, xp and ubuntu are on the same drive, with xp on a partition and ubuntu root and swap space on 2 other partitions on the same drive.

I have another physical drive split into 2 partitions.  If I resize or do anything with these partitions it causes a grub 17 error at next start up.  I've tried ways to fix the grub i've seen on various forums, but usually end up reinstalling ubuntu, loosing everything i've done with it.

Why would making changes to this drive have any affect on the grub or linux since its not even on the same drive ?

Have i installed it properly ?  grub installed to hd0 i think it was if thats any use ?

Help please !

Cheers,

Mark :)

---

### Post by nickpaton on 2007-03-04
Hi Mark and welcome to Ubuntu and the forums.

Have a look at:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17")

This talks about making Super Grub on a floppy and using it to boot into grub to carry out modifications to fix any problems.

The following post discusses grub error 17 and 18 problems in some depth and may also be of help:

[http://ubuntuforums.org/showthread.php?t=367070]("http://ubuntuforums.org/showthread.php?t=367070")

The following post is the same problem as yours - OK they don't get to the solution, but useful stuff in there:

[http://ubuntuforums.org/showthread.php?t=371115]("http://ubuntuforums.org/showthread.php?t=371115")

---

