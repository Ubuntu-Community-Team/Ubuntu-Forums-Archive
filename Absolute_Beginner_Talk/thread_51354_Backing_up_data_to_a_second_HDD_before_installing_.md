---
title: "Backing up data to a second HDD before installing Ubuntu."
date: 2005-07-23
forum: Absolute Beginner Talk
---

### Post by Aardark on 2005-07-23
As I understand, in the process of installing Ubuntu all the files currently on my HDD will be deleted. However, if I have two hard drives (C and E), and I am installing Ubuntu on C, could I transfer all the files that I need from drive C to drive E before installing, and move them back to C afterwards, or will *both* drives be formatted? Thanks!

---

### Post by super on 2005-07-23
yes, that is a good idea to put you data on a second hard drive.

no, both drives will not be formatted if you specify this in the disk partitioning section of the installation. make sure you set a mount point for the second hard drive so you can retrieve you data afterward.

---

### Post by Aardark on 2005-07-23
[QUOTE=super]no, both drives will not be formatted if you specify this in the disk partitioning section of the installation.[/QUOTE]
Okay, those are good news. Another question: how do I set a mount point for the second drive, and what precisely will I have to do to retrieve the data after the install is finished? I understand this must be a very obvious thing to ask, but this is my first time trying to work with Linux, so I'm kinda scared I'm going to lose all my data, or something like that.

---

### Post by super on 2005-07-28
sorry for taking so long to reply.

the partitioning tool in the installation will allow you to set the mount points of all your hard drives and partitions. then it's as easy as finishing the installation and navigating to the directory in nautilus, from there you can copy the information.

*tip* use a fat32 filesystem for windows if possible since linux can read/write to it. ntfs is read-only in linux.

---

