---
title: "Gparted LiveCD questions"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by marioguy on 2007-07-10
Hi, I would like to partition my drive so I have part for windows and part for ubuntu and I think I could use gparted to do this if it can resize and create a partition without data loss.  So, basically my question is, does Qparted (the livecd version) resize WITHOUT data loss and is this a good idea?If not can I have some suggestions?

---

### Post by macogw on 2007-07-10
Well um...if you resize it so that it's smaller than where the last bit of your info is, that part will be cut off.  You have to defrag Windows (a few times) first, it'll move everything to the front so then you can resize and just don't resize so that you cut off any of the part that's colored in to show where data is.  It *might* complain about resizing NTFS and give an error telling you to boot into Windows and use chkdks /f then reboot twice (you will be scheduling chkdsk to run on reboot).  If it tells you that, do it, and don't forget the /f part of the command.  Other than that, should be fine.

---

### Post by marioguy on 2007-07-10
Well I'll defrag until its all to the left then I'l try resizing and see if it works, if I screw up, I have windows XP pro ready =)

---

### Post by macogw on 2007-07-10
If you don't have any stuff on there (or it's little enough to backup to a flash drive), it's actually easier, IMHO to partition it all up before installing anything than to resize NTFS.  The XP installer has a partitioner to do it if you wanted to just start it clean.

---

### Post by sundol on 2007-07-10
In my case, I had no data loss when I did resize with gparted live cd.
However, for in case, I always backed up my data before using gparted(or any other partition program) and I think that you should, too.

---

### Post by marioguy on 2007-07-10
Wait, so you really only loose data if your disk isnt defragmented? 
P.S.
Any data besides Windows itself is nothing I can't just download again so if it doesn't hurt Windows I don't care(lol)
EDIT:Also when I have everything installed, will my BIOS let me choose which OS I want at startup?

---

### Post by macogw on 2007-07-10
That's not the BIOS's job :p Ubuntu will install a new bootloader on your system called GRUB, and it'll give you options of Ubuntu (with all kernels that are currently installed, so if you have a kernel upgrade and it breaks something you can use the old one) and Windows at startup.

If you don't defrag or if the filesystem gets messed up or if you try to make a 4GB partition out of one that had 5GB of data, data loss can happen (will in the last case).  Since Windows can do weird stuff to the file system, if GParted tells you to use chkdsk on Windows, do it.

---

### Post by marioguy on 2007-07-10
Good =) My computer is defragging now...

---

### Post by marioguy on 2007-07-10
sorry about the double post but what filesystem should the partition be to install ubuntu?

---

### Post by macogw on 2007-07-10
ext3 is the usual.  Some people use ReiserFS.  I don't know Reiser's merits and deficiencies, so I can't comment on it.  The + ext3 has over Windows filesystems (FAT32, NTFS) is that it doesn't need to be defragged and it is journaled so if you lose power or forcefully shut down the computer, it should (keyword "should"...there've probably been times that things were so messed up it was beyond help) recover the journal on next boot (or next time fsck is run, I forget which...fsck is run on Ubuntu after every 30 mounts, which is usually the same as every 30 boots) and fix the journal, whereas FAT32 and NTFS would become corrupted.

---

