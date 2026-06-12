---
title: "Back already"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by IsleOf on 2007-05-20
Well ive installed ubuntu. Was really easy. Now i need to get set-up for what i want to do so some more questions.

Mount windows - What exactly does this do? I presume it means i can access the other hard drives? 

Firefox - Its allready installed but how do i get my bookmarks from the firefox i was using in windows.

Is there a way to check all my hardware is installed correctly?

Ill have more questions later on downloading from newsgroups and cd/dvd burning probably but one step at a time.

Cheers again
IsleOf

---

### Post by raeb on 2007-05-20
To get started, you'll need to be able to access your windows partition on the hard drive (what you referred to as mounting windows, you mount partitions.)  If you have dapper/edgy, here's a guide to install ntfs-3g, which enables you to read ntfs partitions from linux.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

If you have the latest version of ubuntu (fiesty fawn), I'm pretty sure it's in the repositories.  Go to System -> Administration -> Synaptic Package Manager.  Enter your password and find the package ntfs-3g.  You may have to enable the extra repo's by going into Settings -> Repositories.  Select the ntfs-3g package and ntfs config.

---

### Post by Ozeuss on 2007-05-20
> **IsleOf said:**
> 
Mount windows - What exactly does this do? I presume it means i can access the other hard drives? 

Firefox - Its allready installed but how do i get my bookmarks from the firefox i was using in windows.

Is there a way to check all my hardware is installed correctly?

Ill have more questions later on downloading from newsgroups and cd/dvd burning probably but one step at a time.

Cheers again
IsleOf
 out of the box, you can read the windows partition. if you want to write to it, install ntfs-3g.
for firefox, you can either export your your bookmarks, and/or use a bookmark syncing extension, or create a new profile on ubuntu and point to your profile folder (howto for that in firefox site)
best way tp check your hardware, is, i think, to try and use it ,no?

---

### Post by overdrank on 2007-05-20
> **IsleOf said:**
> Well ive installed ubuntu. Was really easy. Now i need to get set-up for what i want to do so some more questions.

Mount windows - What exactly does this do? I presume it means i can access the other hard drives? 

Firefox - Its allready installed but how do i get my bookmarks from the firefox i was using in windows.

Is there a way to check all my hardware is installed correctly?

Ill have more questions later on downloading from newsgroups and cd/dvd burning probably but one step at a time.

Cheers again
IsleOf

HI if you look up at the top of the screen by the firefox on my system there is some great help there. Its also on system, help. Good luck and welcome! :popcorn:

---

### Post by IsleOf on 2007-05-20
Trying to mount the partitions. This is what i get view the partition table. 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4055    32571756    7  HPFS/NTFS
/dev/sda2            4056       12511    67922820    f  W95 Ext'd (LBA)
/dev/sda3   *       12512       30401   143701425   83  Linux
/dev/sda5            4056       12133    64886503+   7  HPFS/NTFS
/dev/sda6           12134       12511     3036253+  82  Linux swap / Solaris

Disk /dev/sdb: 514 MB, 514981888 bytes
173 heads, 57 sectors/track, 102 cylinders
Units = cylinders of 9861 * 512 = 5048832 bytes

My hard drive was allready partitioned before linux into C and D drives. Why is there 5 partitions now. I thought Linux has a linux and a swap partition. Whats the extra partition? Does this make sense?

---

### Post by Ozeuss on 2007-05-21
look at your setup in gparted, it'll be much easier to understand since it shows it graphically.
basically, /dev/sda2 is just an extended partition that houses your other NTFS partition and the swap. so basically you have 2 NTFS partitions, one ext3 (your linux installation), and one swap.

---

### Post by jiminycricket on 2007-05-21
I recommend installing ntfs-config since it's a really nice GUI for ntfs-3g.

---

### Post by Talon2 on 2007-05-21
> **IsleOf said:**
> 
Firefox - Its allready installed but how do i get my bookmarks from the firefox i was using in windows.

IsleOf

From Windows:

Firefox > Booksmarks > Organize Bookmarks > File > Export

This should create a file called "bookmarks.html".  You should copy this file to a flash drive or floppy or whatever then fire up Ubuntu and go through the above process again but Import instead of Export.

Good luck.

---

