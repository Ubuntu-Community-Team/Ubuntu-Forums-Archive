---
title: "XP not recognizing FAT32"
date: 2005-11-07
forum: Absolute Beginner Talk
---

### Post by Griff on 2005-11-07
Sharing a fat32 with windows.  Got it mounted on boot as per ubuntuguide.org.  However, windows isn't recognizing.  Don't see what the problem is.  How can i get windows to recognize this partition?

---

### Post by Ramses on 2005-11-07
Is the partition on the same disk as the windows?

See if partition is visible in windows disk management:

> How to use Disk Management
To start Disk Management:
1.	Log on as administrator or as a member of the Administrators group.
2.	Click Start, click Run, type compmgmt.msc, and then click OK.
3.	In the console tree, click Disk Management. The Disk Management window appears. Your disks and volumes appear in a graphical view and list view. To customize how you view your disks and volumes in the upper and lower panes of the window, point to Top or Bottom on the View menu, and then click the view that you want to use.

---

### Post by Griff on 2005-11-07
Ok, the file systems are visible from computer management.  However, i don't see how to make my fat32 usable for sharing.  i.e. make it so that is is a seperate drive on the 'my computer' screen.
edit: the partition is on the same hdd as windows

---

### Post by patrick295767 on 2005-11-07
[QUOTE=Griff]Ok, the file systems are visible from computer management.  However, i don't see how to make my fat32 usable for sharing.  i.e. make it so that is is a seperate drive on the 'my computer' screen.
edit: the partition is on the same hdd as windows[/QUOTE]
   
[http://www.ubuntuforums.org/showthread.php?t=64557&page=6](http://www.ubuntuforums.org/showthread.php?t=64557&page=6)   
       
[http://www.ubuntuforums.org/showthread.php?t=64557&page=7](http://www.ubuntuforums.org/showthread.php?t=64557&page=7)

---

### Post by manicka on 2005-11-07
You'll probably need a program like partition magic to manually allocate it a drive letter in windows

---

### Post by tonysathre on 2005-11-07
u can use disk management to add a drive letter

---

### Post by Kyral on 2005-11-07
Ubuntuforums: We rock so much that we solve XP problems ;P

---

### Post by Griff on 2005-11-08
[QUOTE=Kyral]Ubuntuforums: We rock so much that we solve XP problems ;P[/QUOTE]
So right!  I went to the official xp forums with internet explorer (install so fresh i don't have firefox in yet) and lo and behold popups EVERYWHERE.  I didn't even get time to search...i can't believe i even wasted the time to go there.
Anyway, you say i can add a drive letter from disk management.  This is what i'm having trouble finding out how to do.  How does one do this?  I couldn't find what i was looking for in the above links by patric295767...

---

### Post by chazzjazz on 2005-11-08
in xp, it in control panel>>performance and maintenance>>admin tools>>computer managanemtn>>diskmanagement :D

phew...g luck

---

### Post by Griff on 2005-11-08
I can view all my partitions in disc management.  DM tells me that it is a healthy partition, but that it is an unknown partition.  All actions that i can perform on the fat32 are greyed out, unless of course i would like to delete it.  Someone once told me that sometimes windows has problems recognizing fat32's made by linux.  Hopefully this isn't the case and i'm just not seeing the problem here.  I wish i could just do something with the linux terminal...all this mouse pumping is starting to get old.:)

---

### Post by zerhacke on 2005-11-08
Windows somethimes has problems recognizing fat32 made by Linux, but Linux never has problems recognizing fat32 partitions made by Windows.

I think the easiest thing you could do right now would be to boot Ubuntu, copy everything (or at least, the important stuff) to your Home folder.  Then boot Windows, destroy the fat32 partition, and recreate it.  You could then boot back to Ubuntu, copy everything back to the redone fat32 partition, and sigh with relief.

Doing this would escape having to edit fstab again, assuming you have that partition setup to automount on boot with fstab.

---

### Post by Griff on 2005-11-08
[QUOTE=zerhacke]Doing this would escape having to edit fstab again, assuming you have that partition setup to automount on boot with fstab.[/QUOTE]
I do.  And since i don't actually have anything in the fat32 partition, i'll go ahead and reformat it with windows.  Thanks for the tip.

---

### Post by Arktis on 2005-11-17
I just want to chime in here.  I was forced to install windows xp (ARGH! And it's been longer than 6 months since I've had to use it!) and I've got a fat32 partition that windows can't peek into.  Same exact problem; the partition was created by linux and shows up in the disk management utility as a healthy unknown fat32 partition with the only option availible being deletion.  Luckily, there isn't anything important on there.  But if there was, this would be a big hassle because I don't have enough room on my other drives to move the files so that I can reformat the partition.

Somebody should fix the way linux creates fat32 partitions.

---

### Post by Nrvnqsr on 2005-11-17
damn if I only saw this topic 3 weeks early, I would of save 2 hours of my sweet time :mad:
*bookmarks for future reference*
damn you XP *shakes fist*

---

### Post by zerhacke on 2005-11-17
[QUOTE=Arktis]Somebody should fix the way linux creates fat32 partitions.[/QUOTE]
It's not a bug in Linux's implementation of fat32.  It's a bug in the way Windows reads them.

LINUX HAS NO BUGS, MAN!!!:razz:

---

### Post by manicka on 2005-11-17
[QUOTE=Arktis]

Somebody should fix the way linux creates fat32 partitions.[/QUOTE]

No, somebody should fix the way Windows reads fat32 partitions. The notion that it will only recognise a partition if it creates it is nonsensical.

It's not a Linux problem.
.

---

### Post by Arktis on 2005-11-17
This is a matter of perspective. :rolleyes:  Or maybe I've been re-tainted by windows.

---

### Post by blastus on 2005-11-18
I don't remember what the option is, but the Windows XP DM will not recognize drives unless they are "initialized." You can't do anything with the partitions in Windows XP until you "initialize" the drive. I don't remember what the option is but if you right-click on the drive (NOT on a partition) in DM there should be an option called "initialize" or something like that. After you "initialize" the drive, the partition options are no longer greyed out and you can create partitions and/or assign drive letters to NTFS and FAT partitions.

I have to do this everytime I nuke a drive and/or partition a new drive under Linux and I want Windows XP to use a partition on it. This is not a FAT32 problem or a Linux problem. Windows XP apparently needs to write something to the boot sector of the drive before it can use it for the first time (regardless of what partitions are on that drive.) This may be your problem I don't know but it threw me off the first time I had to do it because it is not obvious why the partition options are all greyed out.

---

