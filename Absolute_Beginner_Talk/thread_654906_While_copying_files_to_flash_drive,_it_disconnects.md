---
title: "While copying files to flash drive, it disconnects"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by darkchest on 2007-12-31
When i copy large files like movies from my ubuntu dapper to my flash drive, the flash drive disconnects and then the movie file would be half copied.  I also have an xp (as a dual boot on the same machine) and this problem doesnt happen to it.  What can i do to solve the problem... I want to move movies from ubuntu to the xp.

I also tried mounting the windows drive, but it comes in as read-only.

---

### Post by (((X))) on 2007-12-31
You can create a share partition(fat32 or so) and share movies.
I am able to read/write to my xppartition, try to remove password from xp and see if it works..

---

### Post by hums07 on 2007-12-31
Gutsy by default is able to read and write on Windows partition (NTFS). If you have Ubuntu from older version, you need to install ntfs-3g [here]("http://www.ntfs-3g.org/about.html") to be able to access your Windows partition, or you may find it on repository depending on which version of Ubuntu you have.

---

### Post by darkchest on 2007-12-31
I dont have password on my xp...and i dont know how to create a partition without formatting the drive again.  I dont want to loose anything i already have on both operating systems.

---

### Post by darkchest on 2007-12-31
I am using Ubuntu dapper and it still doesnt work.  Is there any reason why dapper can not copy large files to my flash?

---

### Post by Paqman on 2007-12-31
Have you tried installing ntfs-3g like Hums07 suggested? That will allow you to copy the files straight to your Windows partition. No flash drive required!

---

### Post by darkchest on 2007-12-31
thank you guys very much, i have installed ntfs-3g and i can copy files. But is there any particular reason why the flash drive disconnects while copying large files?

---

### Post by Majorix on 2007-12-31
Some file systems have max file size limits. For example, FAT32 won't allow anything larger than 4GB's as a single file. One solution is to split the file.

---

### Post by mmb1 on 2007-12-31
Is your flash drive linux compatible?

---

### Post by darkchest on 2008-01-02
i have a png 8g flash drive. I can copy small files, but when i copy large files the flash drive ejects

---

### Post by Jayferd on 2008-04-20
bump.

This is happening to me now, I have 2 very large (200G/250G) Toshiba external hard drives, and I'm trying to back up my music collection (about 50G of .flac files, plus album covers) from one to the other.

It goes fine for a while, but then one of my drives disconnects (always the copy-from drive).  They're both ntfs, so no afaik there's no max file size.

This seems pretty buggy, but I stumbled across this thread through Google and thought I should ask here first before going to Launchpad.

edit:  Just thought I should mention that afaik there's no problem with either drive, I've used them both extensively with my ubuntu setup, including large-scale file operations, and this is the first time I've run into this sort of problem.

---

