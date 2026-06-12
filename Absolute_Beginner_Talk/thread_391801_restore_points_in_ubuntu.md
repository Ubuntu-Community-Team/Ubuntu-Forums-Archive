---
title: "restore points in ubuntu?"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by CraniumDesigns on 2007-03-23
hey folks,

i was wondering if ubuntu has any way of setting restore points, similiar to the way windows does? cuz what if i go in to a ton of files, make a ton of changes trying to get something working, it doesnt work, so i want to go back to where i started. how do i do that without reinstalling the whole OS?

---

### Post by ardchoille42 on 2007-03-23
> **CraniumDesigns said:**
> hey folks,

i was wondering if ubuntu has any way of setting restore points, similiar to the way windows does? cuz what if i go in to a ton of files, make a ton of changes trying to get something working, it doesnt work, so i want to go back to where i started. how do i do that without reinstalling the whole OS?

There aren't any "restore points" in Ubuntu. However, there are ways to make an image of your partitions and then restore them later if needed.

I make weekly images of my root partition and then burn those images to DVD for safekeeping. I recently had to restore my root partition from a recent image and the partition was restored so well that the system never even know the difference. It would be trivial to set up a file server to hold these images instead of using up blank dvd's to store them.

For imaging and restoring entire partitions, I recommend [System Recue CD]("http://www.sysresccd.org/Main_Page"). This is a very nice LiveCD and has lots of admin tools on it including PartImage - which is what I use to image/restore partitions. I recommend this rescude cd to everyone who uses Linux.

[SystemRescueCD screenshots]("http://www.sysresccd.org/Screenshots")
[SystemRescueCd downloads]("http://www.sysresccd.org/Download")
[SystemRescueCd how to]("http://www.sysresccd.org/Howto")
[SystemRescueCd FAQ]("http://www.sysresccd.org/FAQ")

---

### Post by CraniumDesigns on 2007-03-23
awesome. thanks. restore points would be sick though. wonder how hard it would be to add?

---

### Post by Kobalt on 2007-03-23
I personnaly use [sBackup]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite") to create restore points and/or backups of specific folders, and I love it. You can plan backup creation, you can specify filters for files/folders backups such as size, file type, etc.

---

### Post by CraniumDesigns on 2007-03-23
that's nice. would allow you do just the parts you're affecting. wasting a dvd every week seems like  a pain.

---

