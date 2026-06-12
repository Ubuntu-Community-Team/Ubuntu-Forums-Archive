---
title: "Dual boot blues - please help!"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by psyguy92 on 2007-07-05
Hi. I installed a second HDD on a friend's computer (250GB) that already had a 60GB(?) drive with WinXP.  I deleted all partitions set up on the 250gb drive using windows and set that drive as a slave with the jumper. I then allowed Ubuntu's install disk to autopartition and install to the 250gb drive.  Install was smooth, but afterword, rebooting gave GRUB error 18.  

I googled for GRUB error 18 and it said something about the cylinder exceeding maximum suported by BIOS. I tried reinstalling Ubuntu, and had the same error. Of course, WinXP no longer booted, but I was able to get XP booting again by using the [Super Grub Disk (SGD)]("http://freshmeat.net/projects/supergrub/"), but was unable to get SGD to successfully re-write the MBR.

I really don't know anything about hard disk geometry or cylinders or very much of the BIOS ins-and-outs, and am at a loss as to how to go about setting up a working dual boot system.  I really don't even understand the error I've gotten.  Please help out if you have any ideas- I'm on vacation and will only be able to try this for another couple of days. :-O

---

### Post by Hobo Joe on 2007-07-05
Just to verify, the 250GB drive has Ubuntu on it, and the 60GB drive has Windows on it?

---

### Post by psyguy92 on 2007-07-05
yes. 60 windows 250 ubuntu

---

### Post by splintercellguy on 2007-07-05
I suspect your BIOS does not support HDD sizes over 139 GB.

---

### Post by confused57 on 2007-07-05
Maybe one of the solutions here will help:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)

---

### Post by psyguy92 on 2007-07-06
Thanks for the help so far. I had seen that page hosted at bigpond before when looking for answers... I felt that the 137GB limit was probably not the problem, as I believe this system to be only a couple of years old.  

What I've done now is disconnect the Windows drive (60gb) and set the 250GB as master, wiped the partitions, and reinstalled Ubuntu to the 250GB drive.  It booted fine into Ubuntu.  
Q: Am I correct in assuming that since it partitioned correctly, with Ubuntu showing ~225GB free space, that the BIOS _is_ able to work for drives above 137GB?

If so, now what I need is a way to be able to freely select between Ubuntu and XP.  

Recapping: the 250GB is set as master and is currently the only one connected, and boots Ubuntu fine.  The 60GB drive is physically disconnected and holds a working XP installation.  If I connect the 60GB drive as master and it is the only connected drive, it will boot XP (the super grub disk option similar to fix mbr was used, and XP boots normally.

It looks like I'm pretty close, but need help to finish.  I don't want to leave my friend having to open the case and swap cables, to select between Ubuntu and XP.

---

### Post by confused57 on 2007-07-07
> **psyguy92 said:**
> Thanks for the help so far. I had seen that page hosted at bigpond before when looking for answers... I felt that the 137GB limit was probably not the problem, as I believe this system to be only a couple of years old.  

What I've done now is disconnect the Windows drive (60gb) and set the 250GB as master, wiped the partitions, and reinstalled Ubuntu to the 250GB drive.  It booted fine into Ubuntu.  
Q: Am I correct in assuming that since it partitioned correctly, with Ubuntu showing ~225GB free space, that the BIOS _is_ able to work for drives above 137GB?

If so, now what I need is a way to be able to freely select between Ubuntu and XP.  

Recapping: the 250GB is set as master and is currently the only one connected, and boots Ubuntu fine.  The 60GB drive is physically disconnected and holds a working XP installation.  If I connect the 60GB drive as master and it is the only connected drive, it will boot XP (the super grub disk option similar to fix mbr was used, and XP boots normally.

It looks like I'm pretty close, but need help to finish.  I don't want to leave my friend having to open the case and swap cables, to select between Ubuntu and XP.
You could try connecting the drive with Windows as slave, then adding an entry to grub to boot Windows:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

