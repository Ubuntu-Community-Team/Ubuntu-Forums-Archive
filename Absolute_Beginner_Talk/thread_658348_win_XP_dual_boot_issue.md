---
title: "win XP dual boot issue"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by moosky13 on 2008-01-04
I'm very new to this.  Trying to do dual boot.  I inserted the Ubuntu disk and followed all the directions and now I don't see Windows XP anymore.  Ubuntu works fine.  I don't even see any of my files on my hard drive.  I was able to see all my files when I ran Ubuntu off of the CD.  I think I might have wiped my hard drive clean in order to install Ubuntu.  I made a backup for XP but I don't have XP as an option to login to and restore.  Is my XP and all my files gone now?  I apologize ahead of time if this is a dumb question.  thanks

---

### Post by sirgogo on 2008-01-04
Hello moosky13,

Based on your description, it seems that you have indeed swiped your harddisk and put Ubuntu. When installing did you select "Use the whole drive", rather than "Manual partitioning" ?. If you did, you have swiped your drive.

I would suggest downloading and burning G-Parted onto a DVD and using that to recreate a ntfs partition (Windows XP) and then reinstalling windows onto that partition.

However, there are many problems with installing Windows after Ubuntu has been installed, primarily to do with ovewriting the MBR. The best solution in your case would be to swipe your hard disk, install Windows, and then install Ubuntu.

Hope that makes sense!
Good luck!

---

### Post by moosky13 on 2008-01-04
I did not choose manual partitioning.  Also, all my files are gone then?

---

### Post by Jim Edwards on 2008-01-04
.

---

### Post by huntnplay on 2008-01-04
hi, moosky13, if you did not choose manual partitioning, u must have chosen, use entire drive, in that case, it erases everything from your hdd, ur windows os, and installed ubuntu over it. u should have chosen manual partitioning if u wanted to dual boot. and jim edwards, do u have the right ram for the installation, sometimes that could be prolbme.

---

### Post by Jim Edwards on 2008-01-04
.

---

### Post by dstew on 2008-01-04
To be sure, open a terminal window in Ubuntu and enter the command```
sudo fdisk -l
```That's a small "L", not a "1" in the command. If windows is gone, the output will show only the ubuntu ext3 partition and the swap partition.

---

### Post by jlnh on 2008-01-04
Hi Mooskey,

Some years ago I did a lot of partitioning of my Hard Disks, 
A program to use was Partition Magic, but above all I had tremendous help from a program called PowerBoot from Blue Sky Inventions.
(see write up :[http://www.linuxjournal.com/article/3364](http://www.linuxjournal.com/article/3364))

Easy to use and you are the Master of yoour MBR,

At computer start up load a DOS diskette, run DOS (1st disk only) when ready installing DOS will ask you for 2nd disk, just hit the F3 key to get out of DOS and you will have the Dos Prompt on your screen.
Now Load the PowerBoot disk by typing: > DIR
Select the "powerboot.exe" program and follow the instructions.

Every time you start up your computer you are presented with a selection of ALL your partitions. Find the boot partition you want and run the O/S you want. (you can also autostart your regular selection).

Success
JLNH
PS: Once trained, you can also make your partitions with PowerBoot.

---

### Post by moosky13 on 2008-01-04
I will give that a try.  thanks for the info.

---

