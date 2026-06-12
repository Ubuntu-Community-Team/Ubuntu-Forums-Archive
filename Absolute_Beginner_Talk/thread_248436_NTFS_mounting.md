---
title: "NTFS mounting"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by eurostyle360 on 2006-09-01
hey.. im a linux newb and i was wondering if there was any way for me to mount my ntfs partitions for read/write access?  this is really the only thing holding me from using ubuntu full time:(

---

### Post by eternalis on 2006-09-01
Check this link:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by jorn on 2006-09-01
Also this may help you:
[http://ubuntuguide.org/wiki/Ubuntu_dapper#Windows](http://ubuntuguide.org/wiki/Ubuntu_dapper#Windows)

---

### Post by catlett on 2006-09-01
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)
That will guide you through the process of mounting read/write. By default ntfs volumes will be mounted read only. NTFS is a closed source file system. Microsoft owns it and does not release it. This project (like the other ntfs read/write applications) does not have the source for ntfs. They "reverse" engineered the ntfs driver. What that means is, use of read/write support in linux is not without risk. Although this application claims to be low risk, you should be careful when using read/write support. It is best to avoid writing to ntfs from linix. You should create a small fat32 partition to use as a transition area for files betweem your OSs or use the ext2 driver for windows and access your linujx files fropm windows and copy over what you want from linux to windows.[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by sleepingdragon on 2006-09-01
Thanks psychocats.net - i got instant access to my windows drive.

---

### Post by eurostyle360 on 2006-09-01
hey well.. is there any way for me to convert my filesystems somehow? like a software that automates the transferring of files, resizing of partitions, and possibly formmating them so i can have a filesystem converted from ntfs to ext3 (and vice versa in the event linux just can't work out for me)

my situation is as follows:

**drive one**approx 80 gb
18 gb for linux (ext3)
1.5 for swap (swap)
approx 50 gb for random things (ntfs)
10 gb for windows media center (ntfs)

**drive two**250 gb
approx 250 gb for more random stuff (ntfs)

i can successfully back up my first internal drive's 50 gb partition on my second external drive and restore it on an ext3 partition.. in this sense i accomplish this psudo-conversion, however i have over 100 gb of data already stored on my external drive and nowhere to back it up if i wanted to manually switch file systems for that, which is crucial for my total OS  switch..

thank you for putting up with another newb btw.. im sure you're already bombarded with them, and if i reposted a common question i apologize..

---

### Post by jorn on 2006-09-02
The application "gparted" is able of rezising partitions and convert filesystems. It's also avaiable as a live-cd. A live cd is necessary when you want to rezise the patition on which your os is located.
There is also the app "cfdisk" inside terminal:
> sudo cfdisk

---

