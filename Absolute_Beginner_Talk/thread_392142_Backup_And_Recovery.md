---
title: "Backup And Recovery"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by hobo on 2007-03-24
What is the best way to backup my Dapper image? I am thinking about making some changes to Dapper that could cause me to reload it if it fails. I have worked very hard to get my Dapper image to where it is now and really don't want to go through that again if I can help it.

---

### Post by PartisanEntity on 2007-03-24
The best method is to download the [System Rescue CD]("http://www.sysresccd.org/Main_Page") iso and burn it to CD and use it to make a backup of your image.

Good instructions can be found [here]("http://www.psychocats.net/ubuntu/partimage")

---

### Post by Kobalt on 2007-03-24
I use [sBackup]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite") to create restore points and/or backups of specific folders, and I love it. You can plan backup creation, you can specify filters for files/folders backups such as size, file type, etc.

---

### Post by PartisanEntity on 2007-03-24
I don't think you can do a backup of an entire image with sBackup?

---

### Post by Kobalt on 2007-03-24
Maybe not (even though selecting your entire / folder is possible, hence making a complete backup) but if it's a complete image backup you want, you should actually use partimage, I agree on that.

---

