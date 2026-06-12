---
title: "gnome part ed"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by misterf1 on 2007-07-26
Hi all.  I'm having trouble trying to install 7.04.  Using the live CD and Gnome Part ed on the CD, I'm attempting to make a dual boot and can't get it to work.  Here's the detail list: (paraphrased, but almost in detail).

ntfsresize v1.13.1 (libntfs 9:0:0)
Device name          :/dev/sda1
NTFS volume verson: 3.1
Cluster size             :4096 bytes
Current volume size: 300074631680 bytes (300075 MB)
Current device size: 300074632704 bytes (300075 MB)
Checking filesystem consistency
Accounting clusters
Space in use          :111567 MB (37.2%)
Collecting resizing constraints ...
Needed relocations : 4437 (19 MB)
Schedule chkdsk for NTFS consistency check at Windows
Resetting $LogFile 
Relocating needed data
ERROR : Extented record needed (1080>1024), not yet supported!
Please try to free less space.


Right, so, I've been around computers a long time, all of that I recognize right up to the error line.  I tried making the 3 partitions for Ubuntu, I went back to just making one, no go for anything.  The drive isn't mounted (I checked) and when I use the Gparted Live CD, the screen distorts and I can't get past the options (keyboard and language).  Any thoughts?  I've backed up my stuff, it's all ready to be installed, but the drive doesn't seem to want to play.  Thanks in advance.

---

### Post by p_quarles on 2007-07-26
What version of Windows are you using? I've heard different stories from others, but personally I have never been able to get gparted to resize an NTFS volume created by Vista. 

If that might be the problem, the easiest workaround is to use Vista's own disk manager to create the free space you want. Gparted will have no problem using the freed space to create an ext3 partition.

---

### Post by misterf1 on 2007-07-26
Hi, yeah I guess I should have added that, I'm on XP SP2.

---

### Post by misterf1 on 2007-07-26
bump.  this forum moves fast!!

---

### Post by misterf1 on 2007-07-27
just an update, I got the GParted Live CD to load, whatever it was doing with my monitor, I got it to work.  I'm no longer on the DVI and back on an RGA cable for the moment, but also picked the third option on the menu (forget what it was). 


 HOWEVER, :( Even in the Live CD, the drive still won't partition.  My Dad and I had a discussion about this last night.  When I'm making a partition, I'm making "Primary" Partitions, right? Or should I be making extended?  Plus if I remember (it was late), even the extended option won't work.  I guess what it boils down to is that I'm fighting the ntfs partition, not necessarily GParted.  Any thoughts?  I keep getting the same error about the partition size being too big.

---

### Post by ugm6hr on 2007-07-27
Maybe post a screenshot from GParted LiveCD so we can see what the issue is.

I would suggest just shrinking the NTFS partition, and leaving the rest empty with GParted LiveCD, then apply.  There is in fact no need to create partitions in GParted at all - the Ubuntu CD can do that for you automatically.

---

