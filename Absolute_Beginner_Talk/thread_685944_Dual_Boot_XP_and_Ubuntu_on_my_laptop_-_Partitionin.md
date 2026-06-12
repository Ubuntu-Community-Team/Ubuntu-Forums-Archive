---
title: "Dual Boot XP and Ubuntu on my laptop - Partitioning Issues"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by CreamCheesey on 2008-02-02
So I'm completely new to Linux. I'm trying to install a dual boot with XP and Ubuntu on a laptop that isn't really used anymore just so I can try it out. From what I understand, when you hit the partitioning menu in the installation process, you should get three choices - Guided (resize and use free space), Guided (use entire disk), and manual, right? Well for whatever reason I don't have the "Guided (resize and use free space)" option. Fine, I hit manual and go on.

This is where I get lost. The hard drive is 40GB. When I first get to "Prepare partitions," there are two partitions.

Device                Type             Mount Point                 Size                Used
/dev/sda1   fat16       /media/sda1        49 MB      33 MB
/dev/sda2   ntfs         /media/sda2        39958MB Unknown

I can't resize the ntfs partition at all. When I try to create a new partition table, it doesn't let me create a partition of type ntfs, though I'm not sure if I even need to do this at all. I also have no idea what to do for mount points. As I've said, I'm a complete newbie, and most of the guides I've seen have an ntfs partition so I'm not really sure what to do anymore. Thanks in advance for any help.

---

### Post by louieb on 2008-02-02
System>Administration>Partition Editor.

Go there 1st: it opens up GParted.  More intuitive to use.  Shrink your windows partition. and create your Linux install partition. 
a couple of links to help. 

 [GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")
[Psychocats Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index.php") look along the left for the partition and install pages. - very good stuff.

---

### Post by wilson47 on 2008-02-02
@louieb 
Thanks for the great advice! I am in the process of dual booting too, and that was just what I was looking for! Thanks again!!!

---

### Post by CreamCheesey on 2008-02-02
Ah, I didn't see that before. Thanks!

I've now run into other problems, though. When I try to resize the ntfs (and I hope that's what I'm supposed to be doing), it says "Minimum Size: 38107 MiB Maximum Size: 38107 MiB." I would guess that that creates some issues.

I also get a warning message when I double click that partition. It says:

"ERROR: This software has detected that the disk has at least 295 bad sectors.
WARNING: The disk has a bad sector. This means physical damage on the disk sruface caused by deterioration, manufacturing faults, or other reason. The reliability of the disk may stay stable or degrade fast. We suggest making a full backup urgently by running 'ntfsclone --rescue ...' then run 'chkdsk /f /r' on Windows and reboot it TWICE! Then you can resize the NTFS safely by additionally use the --bad-sectors option of ntfsresize."

Not sure how this affects what I'm supposed to be doing...

---

### Post by wilson47 on 2008-02-02
Actually, I'm having a bit of an issue now. I created a partition on my hard drive, and I go to install ubuntu with the manual partition setting, and I get the warning:

"File system doesn't have expected sizes for windows to like it. Cluster size is 2k (1k expected); number of clusters is 28034 (55960 expected; size of FATs is 110 sectors (219 expected)"

what do i do!?

---

### Post by louieb on 2008-02-02
CreamCheesey:
Boot into windows. **Run chkdsk**. Gparted won't shrink an NTFS partition if it thinks it has any errors. While your in windows run the the disk cleanup utility.  Uninstall any programs you don't need.  **Run the windows defragger**.  the object is to reduce the amount of data and programs in your windows partition. 

If GParted still refuses to shrink the NTFS partition you may have to boot back to XP  and turn off virtual memory. (Turn it back on after your done installing Ubuntu). 

wilson47:
Your past the dangerous part of shrinking the NTFS partition. if windows still boots you are good to go on with the install. I've seen that message before - haven't had a problem.

---

### Post by CreamCheesey on 2008-02-02
Thanks a bunch, louieb. I'll go try it now.

---

### Post by wilson47 on 2008-02-02
Thank you so much!!! Everything works great now =)

---

### Post by CreamCheesey on 2008-02-02
I wish I could say the same. I can't boot into Windows anymore so I'm gonna have to wait until I get my hands on an XP disk before I try anything again. Thanks for the help though, louieb.

---

