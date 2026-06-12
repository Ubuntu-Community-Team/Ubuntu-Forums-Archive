---
title: "FAT32 or NTFS/Ext3"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2007-10-05
I just got a 80GB HDD and external enclosure.  I love my Ubuntu but I do some sidework for friends and others.  I did some research and found that I can use FAT32 and access it with both Winblows and Ubuntu.  I want to be able to back up PC systems and keep all kind of windows apps on the external drive, but also my ubuntu stuff.  I was told by another guy that the FAT will work but it does not support files greater than 2GB (will that give me a prob when backing up systems?)  Also there are some issues with extra long path filenames.

Would you suggest 2/3 ext3 1/3 NTFS or just all FAT. 

Also FAT does not support unix permissions schemes, how do you think this will affect my ubuntu files I have now? Do I lose permissions on existing files if I move them to my external HDD to another computer?

Any ideas would be appreciated...

---

### Post by overlord.gaurav on 2007-10-05
You can install ntfs-3g in Ubuntu 7.04 (Feisty Fawn) now. NTFS-3g gives you read-write support on your computer. And if your system is installed on ext3 then the system works faster (personal experience).
So, what I would suggest is:

1 partition of ext3 for Ubuntu
1 partition as NTFS for you Windows. *with ntfs-3g*

---

### Post by rsambuca on 2007-10-05
If you are going to be backing up windows based PC's, then definitely just format it as ntfs and be done with it.  Just load the ntfs-3g drivers for your own personal use with Ubuntu.

---

### Post by Presto123 on 2007-10-05
Eh...I have my 320gig external with no extra modifications (Western Digital). It's set up on a vfat(FAT32).

It works on all three OS's I have: WindowsXP, Vista, and Ubuntu.

---

