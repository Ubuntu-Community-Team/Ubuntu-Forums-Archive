---
title: "Access to external HD"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by Wittgenstein on 2007-09-14
I have two laptops. The first is running XP and for that machine I have used a Maxtor external hard drive for backing up my files. Now I'm mostly using another laptop, a ThinkPad R 60, running dual boot XP and Ubuntu Feisty - and all my personal stuff is moved to the Ubuntu partition. When trying to backup these files to the same external harddrive I'm not granted access from Ubuntu (but from the XP-partition theres no problem). What do I do? Anyone?

---

### Post by startherepodcast on 2007-09-14
It is probably that your Hard Disk is formated in NTFS. Ubuntu cannot write to that Filesystem, there are certain plugins that enable that, but they are often unstable. I would reommend Copying all your Data from your External Drive to a secure location and using Ubuntu or XP to partition in FAT32, whic Ubuntu can read and write to without problems!
In XP, right click the drive in my computer and select Format)

Hope that helped!

---

### Post by shearn89 on 2007-09-14
As startherepodcast says, there are plugins for Ubuntu that allow reading of NTFS partitions. The most popular one is NTFS3G, which is finally in stable development status after "12 years of development". Have a look [here]("http://www.ntfs-3g.org/"). Although i'd recommend trying to back up data before changing anything...

---

