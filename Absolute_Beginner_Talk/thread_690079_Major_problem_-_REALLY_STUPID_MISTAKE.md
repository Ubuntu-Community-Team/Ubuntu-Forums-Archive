---
title: "Major problem - REALLY STUPID MISTAKE"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Antidisestablishmentarian on 2008-02-07
Things were going so well, I was installing 7.10 from the live CD with help for the GraphicalInstall page on the documentation. I was on step 5, and I clicked on the first one, thinking that this would create a partition with my available disk space. It turns out, I think I wiped my hard drive, without backing up (I know, ALWAYS back up). What do I do? I had some important files in there, is there any way to get them back? Arrgh, I can't believe my stupidity!

---

### Post by marufaberlin on 2008-02-07
Did you write data on your new partition? if not, the data could be restored.

---

### Post by Rocket2DMn on 2008-02-07
In all reality, it's not possible to get your data back after formatting without paying somebody large sums of money to try and recover data (and there are no guarantees, of course).  There are programs out there to "undelete" things but this really only works if you haven't actually reformatted the drive.  
Sorry to shatter your hopes, but I think you're out of luck.  This is one of many reasons we always suggest keeping complete and up to date backups.

---

### Post by marufaberlin on 2008-02-07
Well, it depends if the data was overwritten or if just the file system was erased. If you did a quick format, then only the file system was erased and you could recover some of your data.

---

### Post by Rocket2DMn on 2008-02-07
The problem is that when he formatted, it did ext3 filesystem which rewrote the file system table and reorganized disk sectors (probably had ntfs before).  That makes it nearly impossible to recover data.

---

### Post by Kasyx on 2008-02-07
If indeed the drive has been partitioned with ext3 or any other filesystem for that matter, you probably don't stand a chance. If not, or if you still wish to give it a shot, try using "Activ@ Partition Recovery" (you can find it on Hiren's Bootdisk), which will locate all your previously-deleted partitions and, Cthulu willing, restore it.

---

### Post by nemilar on 2008-02-07
I agree with the poster directly above.  If you've already written a new filesystem, chances are slim, but that particular tool was able to recover some -almost- lost data for me a couple of times.  If you haven't overwritten the filesystem, and it's just unallocated space, you should be gold with that tool.

Good luck!  If you are really, truly desperate, there are companies out there that can get data back from HDDs.  Just **don't write anything else to the hard disk**!!!  The more you write over those old files, the less of a chance of getting anything back.

---

