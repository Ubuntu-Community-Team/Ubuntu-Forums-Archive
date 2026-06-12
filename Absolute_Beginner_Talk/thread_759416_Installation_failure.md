---
title: "Installation failure"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by twp_twm on 2008-04-19
Tried to install Ubuntu, Gutsy Gibbon 7.10 on a friends computer running Windows XP and 512MB  of RAM. Choose to use the whole hard-drive for the installation and waited a long time for this procedure to be completed. But had a message which stated that due to the computer crashing sometime in the past that the MBR was corrupt? Would a new hard drive solve this problem if not could anyone tell me if there's a way around this please. Thanks.

---

### Post by warbread on 2008-04-19
A new hard drive would indeed solve the problem, but it's not necessary.  

From live boot, do a 'sudo apt-get install gparted' from the terminal.   Then run gparted.  Since you're doing a whole drive installation, I assume you have already backed up everything you want to keep.  Delete all of the partitions that you see and apply the changes.  Then try installing.

---

### Post by anerdindeed on 2008-04-19
a simple google search yielded this:
(it is done from the recovery console on the windows xp disk)
[http://askbobrankin.com/fix_mbr.html]("http://askbobrankin.com/fix_mbr.html")

---

### Post by Kevbert on 2008-04-19
Probably the best thing to try would be a low level format of the hard disk.  If you have the CD you'll need to run the install program to reformat the disk, if this fails, you'll need to try using 'fdisk'.  I couldn't find it on the XP CD but any version of windows will have it in system tools*.  Next you'll need to set up a new master boot record (MBR) by using 'format c: /s' (in system tools*) which will copy command.com and  some hidden system files.  If this fails then it looks like a new hard disk.
Once done you should be able to install any OS.
* If you have a Windows boot floppy then files should be here.

---

### Post by twp_twm on 2008-04-19
Thanks for all the replies guys. I'll get right on to it. Cheers!

---

### Post by sandysandy on 2008-04-19
>  But had a message which stated that due to the computer crashing sometime in the past that the MBR was corrupt? Would a new hard drive solve this problem if not could anyone tell me if there's a way around this please. Thanks.

u can fix MBR with an utility called Super Grub Disk ([http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/))

u can download it and burn it as iso image. then u can boot from the bootable CD and use the various options which r self explanatory. u can fix MBR of windows XP or Linux etc.

heres a tutorial on Super Grub.

[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

regards

---

### Post by bumanie on 2008-04-19
If it is just a matter of windows mbr being corrupted you can easily fix this (in most cases) via windows' recovery console if you have a windows installation disk. If you have a xp disk, post back and someone will give you instructions. If you don't have an xp disk, try sandysandy's suggestion or try test disk, it too can write a windows mbr.

---

