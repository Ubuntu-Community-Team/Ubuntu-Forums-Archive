---
title: "Please please urgent help - formatted my home dir :-("
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by debernardis on 2006-05-12
While trying to make some free space in order to test dapper, I reformatted my ext3 partition. I wish I could recover at least the jpg's of my newborn... is there a way?*I have not touched that partition in any way after my stupid command. Might there be a way? 
I don't feel like browsing forums, I'm down. If anybody could help, I'd be really grateful.

---

### Post by cgjones on 2006-05-12
What exactly have you done so far? How did you reformat? [Here](http://linux.sys-con.com/read/117909.htm) is a link that might help, although it gets kind of technical.

---

### Post by Sammi on 2006-05-12
[QUOTE=cgjones]What exactly have you done so far? How did you reformat? [Here](http://linux.sys-con.com/read/117909.htm) is a link that might help, although it gets kind of technical.[/QUOTE]

That article is more for undeleting specific deleted files not whole partitions.

This little application might do the trick though: [http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")
The wiki, which that URL points to, also has good documentation on how you use the program.

It helped me recover once, when I accidentally wiped my MBR #-o :lol:
I love TestDisk ;-)

Best of luck to you!

---

### Post by Kvark on 2006-05-12
I guess it is a bit late to say that you should have backups of all important files.

---

### Post by debernardis on 2006-05-12
It was in qtparted. I had hda6 (blank partition, where I wanted to put dapper) and hda7 (my fs). I formatted hda6, but for some strange reason found hda7 completely  erased. Presently, I am restoring a very old backup I had on hda6, and did not touch hda7 at all after that unfortunate formatting, in the hope there's something I can do.
I have read a quite strange trick, that is formatting the erased partition in fat32 and then "unformat" by some Norton utility (I do not have). Any hint?

---

### Post by skippy81 on 2006-05-12
Whatever you do, dont write anything to the partition which had your home directory on it.  Dont touch it. 

You need to boot off a seperate partition or better still, a seperate hard disk.  It does not matter which OS you boot into really.

Testdisk is good, but not easy to use for those who dont often use text based utilities.  

PC Inspector is a good free recovery program for windows.  

Providing you havnt written data to the partition which you deleted home from, you shouldnt lose ANY data.  To my knowledge linux partitions rarely get fragmented, so all your files should be together in nice little bundles.  A reformat or even deleting a partition doesnt actually destroy files, it just wipes the record of where those files 'live'.  Try both unformat and raw data recovery methods with PC instpector and you should get it all back, just make sure that you don't at any point write to, or defragment, the partition you are recovering from.

---

### Post by macdo on 2006-05-12
Gpart [http://www.stud.uni-hannover.de/user/76201/gpart/ ]("http://www.stud.uni-hannover.de/user/76201/gpart/") will recuperate virtually any partitions on a hard disk. Not for the faint-hearted though.
The plan is to scan with gpart, note the start/end bloocks of the partitions it finds, and redefine them using fdisk (the gnu one, not DOS).
Then you scan your filesystem, and if necessary, rebuild its structure.

Good luck!
(Please note that I am just passing on a solution that someone else (who has used it) gave to me. Probably worth a try, though.)

---

### Post by debernardis on 2006-05-13
Thanks to all, thanks a lot. I am still trying to restore a very old backup on *the other* partition, in order to have a booting system to make all these utils work. I'll let you know...

---

### Post by macdo on 2006-05-13
Argggg - Don't install ANYTHING on the disk!

Use a Live CD

The less you touch the disk, the more chance you have of recuperating your data...

---

