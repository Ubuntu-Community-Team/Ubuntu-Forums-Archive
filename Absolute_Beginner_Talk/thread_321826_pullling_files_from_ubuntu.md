---
title: "pullling files from ubuntu"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by madhatter434343 on 2006-12-19
how can i pull files from the ubuntu partition of my hard drive to my windows desktop?

---

### Post by wadebiyi on 2006-12-19
> **madhatter434343 said:**
> how can i pull files from the ubuntu partition of my hard drive to my windows desktop?
Try explore2fs [http://www.chrysocome.net/explore2fs]("http://www.chrysocome.net/explore2fs") for ext3 partitions or YAReG [http://yareg.akucom.de/]("http://yareg.akucom.de/") for reiserf partitions

---

### Post by BarfBag on 2006-12-19
What filesystem is Ubuntu using?  If you don't know, it's probably EX3.  What version of Windows do you have?  If it's XP, you have NTFS.  NTFS support is still experimental, so all you can do is read the files in your Windows partition.  There's a driver that adds EX2 support in Windows, but it isn't EX3.  This is a tough one.  How big is/are the file(s) you want to move?  If they're small enough, you could zip them and email it to yourself.

I used to have problems like this.  That's why I shrunk my Windows partition to the same size as Ubuntu, and created a giant FAT32 partition to store all of my data on.  FAT32 works out of the box in both Windows and Ubuntu.  It's been one of the best things I've done to my PC since installing Ubuntu.

---

### Post by madhatter434343 on 2006-12-19
thank you, i think that i can just email them to myself its just a .daa or i can flash drive it to myself

---

### Post by wadebiyi on 2006-12-19
If I got your initial question right, the file is on your ubuntu system and you want to get the file from your windows systems.

Ext3 file system is used by default in Ubuntu.  You can access ext3 linux partition from windows using explore2fs.  However, if you have a reiserf filesystem for your linux partition YAReG will be able to read the partition from windows.

---

