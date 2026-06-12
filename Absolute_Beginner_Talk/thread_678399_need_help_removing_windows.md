---
title: "need help removing windows"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by deportes on 2008-01-25
New to Ubuntu and here is what i need if possible to accomplish with freeware.
I inherited a desktop pc from my son that left for college, he bought a laptop. I need to remove the windows partition because I don't want to try registering 2 computers with the same windows registry. 
I installed ubuntu but my 160MB disk only shows 140MB available for ubuntu partition.
How do I completey clean the HD, remove everything related to windowsn.  
I will use this comp for music and video files, Ubuntu can handle my needs easily.
Thanks.

---

### Post by taurus on 2008-01-25
Boot with the LiveCD.  Then, run gparted, System -> Administration, and delete all the partitions on that harddrive.  Then, format it to fat32 or ext3.  Now, click the install icon on the desktop to install Ubuntu.  When you get to the partition screen, tell the installer to use the whole harddrive unless you want to create the partitions yourself first.

---

### Post by deportes on 2008-01-26
Thank you taurus, 
I still only get 149.05 GB instead of 160 GB which is the size of the drive. Any ideas how I can get the rest back from windows or ? that has confiscated my drive.
Thanks again.

---

### Post by JCMS on 2008-01-26
This is normal, 149.05GB is the actual size of the drive. 160GB is "marketing" size, wich uses the "10" base so 1KB=1000ko, 1MB= 1000MB, 1GB= 1000MB

But unfortunately, computers work with binary so 1GB is actually 1024MB, wich gives you 149.05GB.

I'm pretty sure there are better infors on wikipedia though. I know I'm not that much clean >-<.

---

### Post by deportes on 2008-01-26
Great info, thanks. I will install Ubuntu and get rid of windows for good.

---

### Post by deportes on 2008-01-26
I'm still unsure of what is going on. After installing Ubuntu my file system has 132GB of space available.
How much space that Ubuntu takes? I went from 149.05 to 132 +o_. Any ideas.
Thanks.

---

### Post by perlluver on 2008-01-26
Ubuntu takes usually 2 GB for swap and another 2 GB for an Extended Partition.  This is normal.  I have a 200GB hard drive with only 169 GB available in Ubuntu and Gentoo.

PS. You can run in a terminal sudo fdisk -l. And that will show you what is being used.

---

### Post by defenestratos on 2008-01-26
> **deportes said:**
> I'm still unsure of what is going on. After installing Ubuntu my file system has 132GB of space available.
How much space that Ubuntu takes? I went from 149.05 to 132 +o_. Any ideas.
Thanks.

Thats still plenty of space to work with

Any new questions we can help you with?

---

### Post by deportes on 2008-01-26
Thank's, Ill try fdisk and see what info I get.

---

