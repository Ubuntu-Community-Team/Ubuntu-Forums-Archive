---
title: "Mounting a FAT32 Partition as /Home"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by theycallmemorty on 2006-04-11
I saw an guide that some guy wrote and he suggested doing this if you are dual booting because it allowes you to have your documents and personal files accessable from both Windows and Linux.

Has anyone ever tried this before?  Is it a safe idea?

Also, is the hard drive partitioner that comes with the Ubuntu installer reliable when it comes to resizing NTFS partitions?  If not, can someone recomend a program that would do this well?

---

### Post by aysiu on 2006-04-11
Mount a data partition that's FAT32--that's a good idea.
But /home should not be FAT32.

---

### Post by theycallmemorty on 2006-04-11
[QUOTE=aysiu]Mount a data partition that's FAT32--that's a good idea.
But /home should not be FAT32.[/QUOTE]
Why Not? :)

---

### Post by aysiu on 2006-04-11
[QUOTE=theycallmemorty]Why Not? :)[/QUOTE] FAT32 doesn't support Linux permissions. The /home directory is where personal settings and such are stored.

---

### Post by theycallmemorty on 2006-04-11
[QUOTE=aysiu]FAT32 doesn't support Linux permissions. The /home directory is where personal settings and such are stored.[/QUOTE]
Okay that makes sense.  Thanks.

---

