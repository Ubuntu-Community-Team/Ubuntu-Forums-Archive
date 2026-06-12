---
title: "Help Dual Booting on Dell"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by cam2009 on 2006-05-31
I'm trying to dual boot Ubuntu on my Dell Inspiron 1150 laptop, with XP on it. So far, I have

-Used a LiveCD to open gparted, then partioned the harddrive by resizing ntfs, creating an ext3 for linux, linux-swap twice my ram, and a fat32 for shared
-Burned the Ubuntu iso, started the install. Got past keyboard and location, then it comes up with an error saying: 

"Your installation CD-ROM couldn't be mounted. This probably means that the CD-ROM was not in the drive. If so you can try it again."

I found this: [http://ubuntuforums.org/archive/index.php/t-7667.html](http://ubuntuforums.org/archive/index.php/t-7667.html) article, and I tried the suggestion in LiveCD, but it didn't work. Any ideas?

---

### Post by wylie348 on 2006-05-31
For starters, I would try to create a boot partition aboutr 50 MB, a shared data partition for storing data that is shared between xp and buntu (ext3), and finally a buntu os partition  (ext3), and of course a swap.

Ensure that you use acpi=off on boot as a command line parameter to ensure it is not messing up your CD ROM detection upon installation.

Just some things to try.
;)

---

### Post by catlett on 2006-05-31
Are you using the latest version of Dapper? Hopefully you are using an older version of Ubuntu and a newer version has better detection of your drive.
 Do you have another cd rom drive you can switch to? I have 2, a rom and a burner, one time I kept getting errors and I switched the drives around so the slave was the master and vice-versa. The point is when I tried a different cd drive my errors were gone.
If nothing else get into your bios and see what it says about cd rom settings. Try the above mentioned post's recommendation, if your bios has that capabilities. 
Sorry I don't have an exact answer.

P.S. There are 2 good how tos in my signature if you haven't seen them before. Good luck.

---

### Post by cam2009 on 2006-05-31
on the boot prompt I put 
pci=noacpi
but that didn't seem to do anything different. 

I'm using 5.10. I figured I would get the partitioning figured out first, then I could upgrade easy later. should I just wait until dapper? I'll go into gparted again and make sure it all looks right. I tried using gparted on the System Rescue Disk, too but I also got a mounting error.

---

### Post by catlett on 2006-05-31
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) I use gparted live. It is a quick download, it's only 30mb. The big benefit is that your drive is unmounted because it is running off the cd.
I would wait for dapper since it comes out today (it's already June 1st GMT time)
You don't have much to loose other than the time it takes to download, and you have alot to gain, if it something to do with the software on the cd that deals with detecting and mounting the cd for install, and Dapper happens to have it and Breezy didn't.

---

