---
title: "Convert NTFS to Fat32?"
date: 2005-11-15
forum: Absolute Beginner Talk
---

### Post by Todd_Z on 2005-11-15
Is there anyway to convert a partition made in windows [ntfs] to a linux r/w filesystem [probably reisferfs or fat32]?  I don't want to lose the data however :???:

---

### Post by nitricacid on 2005-11-15
There is no way to convert an NTFS format to FAT32 without using a 3rd party program with without loseing some\all your data that is on it.

There is a way to convert from a fat32 to NTFS by just using the RUN program but since you are not asking that then the simple answer is NO.

---

### Post by az on 2005-11-15
No.  NTFS is closed-source so nobody can develop tools for it unless they reverse-engineer it.

There are tools to convert fat32 to NTFS, but not the other way around.  You are going to have to copy the data onto another disk or cd/dvdrom to back it up and then create a proper filesystem on your harddrive.

---

### Post by earobinson on 2005-11-15
how much free space do you have? you could try this

1. resize ntfs partition to as small as possiable.
2. make fat partition
3. move as many files to fat partition as possiable.
4. go back to step 1 untill you have moved all your data.

ALWAYS BACK UP ANY IMPORTANT DATA

---

### Post by Todd_Z on 2005-11-15
Fair enough.  I have a slave drive that looks like this:

Windows [ntfs] - 44 gigs [35 free]
Windows [ntfs] - 20 gigs [5 free]
Linux Swap [400 megs]
Reiserfs - 11 gigs

Is there a way to resize the first windows partition [while in linux] to be only 12 gigs and have the remaining 32 gigs be fat32/reiserfs?

---

### Post by linbetwin on 2005-11-15
If you want to make the second one FAT32 you can move the data to the bigger NTFS partition.

---

### Post by lmandrake on 2005-11-15
You can do this. But before using ntfs-resize you have to defrag your partition and don't use the tool bundled with windows. Use something like Raxcco PerfectDisk (there is a trial version available at [http://www.raxco.com/products/perfectdisk2k/](http://www.raxco.com/products/perfectdisk2k/)).

But I would suggest you move the data from the second partition somewhere (other partition, dvd-r, network) and use the whole second one as new fat32/whatever disk.

---

