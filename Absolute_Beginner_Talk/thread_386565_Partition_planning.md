---
title: "Partition planning"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by Europa2010AD on 2007-03-17
Quick question:

Usually where does Ubuntu install its applications by default, in /(root), or /home?

I'm asking this because I'm trying to figure out the space allocation for the 4 partitions in my 80Gb HD -- /(root), /home, swap, and FAT32 (where I will put the files that need to be accessed by winXP)...

---

### Post by dstew on 2007-03-17
Applications usually end up under root. They go in the /usr and /bin directories mostly.

---

### Post by Kateikyoushi on 2007-03-17
It installs the apps in /(root) only small config files go to home,
You can use this driver from windows so can read directly the ubuntu ext partitions. [LINK]("http://www.fs-driver.org/")

For the system you do not need more than 10GB I maxed around 7 with Xfce gnome and kde installed so you still have lot of space to install things.
For swap I would recommend 1GB the rest can go to /home.

---

### Post by Europa2010AD on 2007-03-17
> **Kateikyoushi said:**
> It installs the apps in /(root) only small config files go to home,
You can use this driver from windows so can read directly the ubuntu ext partitions. [LINK]("http://www.fs-driver.org/")

For the system you do not need more than 10GB I maxed around 7 with Xfce gnome and kde installed so you still have lot of space to install things.
For swap I would recommend 1GB the rest can go to /home.

If only small config files go to /home, do you think 100mb is a good size for it? or may be 500mb just to be safe?

Usually how big are are linux/ubuntu apps? Judging from what you said about your setup, that only leaves you with 3Gb in your system to install apps other than the core system files (Xfce+gnome)... is that really enough? (From a windows point of view... 3Gb of empty space for apps is no where close to being enough!)

---

### Post by Bartender on 2007-03-17
I'm hoping someone else will jump in and confirm this, but if I were to leave extra room anywhere, it'd be /home.  Your documents, music files, all your personal stuff goes there by default.  500MB way too small!!

---

### Post by dstew on 2007-03-17
Bartender is right. If you are going to have a separate /home partition, make it big.

---

### Post by Europa2010AD on 2007-03-17
Well I'm planning to have a huge FAT32 partition for my docs, music files and whatnot that will need to be accessed by my winXP which is installed on a separate HD. So for my /home partition I don't see I'll have much things in it other than config files...

---

### Post by dstew on 2007-03-17
OK, that will also work.

---

### Post by Europa2010AD on 2007-03-17
> **Europa2010AD said:**
> If only small config files go to /home, do you think 100mb is a good size for it? or may be 500mb just to be safe?

Usually how big are are linux/ubuntu apps? Judging from what you said about your setup, that only leaves you with 3Gb in your system to install apps other than the core system files (Xfce+gnome)... is that really enough? (From a windows point of view... 3Gb of empty space for apps is no where close to being enough!)

So.. does anyone have any suggestions for the two questions above?

---

### Post by dstew on 2007-03-17
Lots of time, programs use the /home directory to put stuff in by default. If you have a small /home partition mounted there, you will need to continually move things to your storage disk, which will be mounted somewhere else. You can have a small /home partition, but be aware when you are using your system that when a program asks you where you want to save something (your word processing document, for example) you will select your storage partition's mount point, and not your /home directory.

In terms of space, I have Xubuntu running on an old Compaq Presario. Here is my partition table:
Disk /dev/hda: 10.0 GB, 10005037056 bytes
240 heads, 63 sectors/track, 1292 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         620     4687168+   c  W95 FAT32 (LBA)
/dev/hda2            1013        1292     2116800    f  W95 Ext'd (LBA)
/dev/hda3             621        1012     2963520   83  Linux
/dev/hda5            1035        1292     1950448+   c  W95 FAT32 (LBA)
/dev/hda6            1013        1034      166257   82  Linux swap / Solaris

My whole linux system occupies about 3Gb. It is a little tight, but functional.

---

### Post by Kateikyoushi on 2007-03-17
Sorry I wasn't clear enough programs do not go there just their config files but that's the equivalent of Documents and settings of windows, so all your music images documents emails will reside there. That for me is much more than my system.

I do not need more than what the basic system and a few programs which are around 10MB to do all my tasks.

---

