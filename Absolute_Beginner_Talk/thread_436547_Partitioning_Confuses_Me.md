---
title: "Partitioning Confuses Me"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by Wiggles on 2007-05-07
I have Windows Vista and an Ubuntu 7.04 Desktop disc.  I want to dual-boot Windows Vista and Ubuntu.  There is 79 GB on the drive that Windows is on (only 48 GB being used).  I want to take 20 GB off of the drive that Vista is on and install Ubuntu on that.  I have no idea how to do this.  Please help.:(

---

### Post by mattva01 on 2007-05-07
I haven't used Vista , but you should first defragment the Vista partition and then use Vista's partition manager to resize it. I've always found that the safest under XP. You'll have to Google for where those are though (or hopefully a Vista user will post)

---

### Post by jiminycricket on 2007-05-07
Hi, the Ubuntu installer has a built-in partitioner that should let you allocate that much space to Ubuntu.  mattva is right though, I think you should use Vista's built in resizer.  It's under Computer Management -> Disk Management and you right click on the drive you want to resize.

Just be aware that Vista's file system forces you to do this before booting into it if you resize using Ubuntu: [http://ubuntuforums.org/showthread.php?t=398122](http://ubuntuforums.org/showthread.php?t=398122) YOu don't need to make it anymore though, ntfsprogs is in the repository

---

### Post by Sef on 2007-05-07
To Dual Boot read 

1) [Psychocat's installing]("http://www.psychocats.net/ubuntu/installing") for installs with the Desktop CD.

2) The [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/") for installs with the alternate cd.

---

