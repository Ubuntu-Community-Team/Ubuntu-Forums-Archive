---
title: "Ubuntu Newbie"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Scubastev013 on 2007-03-13
Hey everyone.  I have a few questions for you guys.  I will be switching to Mac to college, and in the meantime, I need something other than windows.  Its driving me nuts.

1. I am trying to install ubuntu to a seagate external hard drive (~205GB USB).  Everytime I go to install it, the install process hangs when I try to have it automatically divy up the hard drive to install linux in a separate partition (I want to give it ~80 GB)  I have other stuff on the hard drive I want to keep.  How do I do it? haha.  I've tried a few other things, but none seemed to work, and I don't want to give the whole hard drive to linux (as I need somewhere to back my stuff up to)


help!

---

### Post by gangrelsurf on 2007-03-13
What Ubuntu version are you installing? Are you doing this through gparted, the one that lets you resize and move partitions and all that? I think that became available in the installer with 6.10.  If that is what you have, are you getting to the point where it shows you your drives and you move stuff around, then hit OK? Is that where it freezes, or does it fail to recognize the drives?

Ah! usb, therein may lay the rub

---

### Post by Scubastev013 on 2007-03-13
Would this problem have anything to do with the filesystem?  Its FAT32.  Should I change it to NTFS or another one?

---

### Post by dstew on 2007-03-13
You have the whole 205 Gb drive as a FAT32 file system? I didn't think that was possible.

---

### Post by Scubastev013 on 2007-03-13
The whole 250 GB drive was FAT32.  That's how it was right out of the box.  Willl it make a difference

---

### Post by DaveyG on 2007-03-13
It should be ok.. wich version of Ubuntu are you trying to install?

---

### Post by Scubastev013 on 2007-03-13
6.10.  See my first post.  If it doens't make sense let me know.  The whole idea is to give ubuntu 6.10 around 80 GB of space and leave the rest open to back up stuff from windows and such.  The utility built into the setup always hangs, resulting in nothing.  I wouldn't know how to manually do this either.  I tried using partion magic from windows to make a new partition, but it didn't work.  I also tried Gparted as well, and it didn't even boot.  What else can I do?  I don't want to touch the hard drive with windows on it.  I've heard there are sometimes problems with it.

---

### Post by dstew on 2007-03-14
I am still a little suspicious of the huge FAT32 disk. It seems that the different partition tools cannot handle it. Is it possible that the disk requires some software to access it from Windows? Did you have to install a driver to install the disk on your Windows system?

---

### Post by Scubastev013 on 2007-03-14
The drive didn't come with any software or anything.  Just the Hard Drive and some papers saying make sure you plug it in to the right ports and stuff.

---

### Post by Scubastev013 on 2007-03-14
The drive didn't come with any software or anything.  Just the Hard Drive and some papers saying make sure you plug it in to the right ports and stuff.  Could I reformat it with windows as NTFS?  Will I run in to problems later on?

---

### Post by ajeffreys on 2007-03-14
I also have the seagate 250GB and mine is also FAT32 if that helps, however I am probably going to install Ubuntu to my internal hardrive and use the external as a place for storage of media (both for windows and linux).

---

