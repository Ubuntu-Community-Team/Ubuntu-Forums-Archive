---
title: "Is it safe to resize partitions"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by trav1085 on 2006-01-02
I have a 40GB harddrive and originally windows had 40GB, I have 5GB to Ubuntu, but I want more for Ubuntu, is it safe to use partitionmagic 8 and make my windows partition smaller (about 5 gb) and make my ubuntu partition 5gb bigger with the allocated space? 

I'm just worried about damaging the file system for ubuntu, is there a defrag program for linux?

---

### Post by mazelado on 2006-01-02
Typically, yes, it is safe. I've done it several times without issue. However, anytime you alter the file system you risk losing data. Making backups is never a bad idea.

Partition Magic should be able to take care of moving the data for you. Don't worry about defragging Linux.

---

### Post by TeeAhr1 on 2006-01-03
I would advise against Partition Magic, I've heard tales of people having serious problems partitioning ext filesystems with it.  I used GParted last week to do this very thing, and it worked beautifully.  You can find it in the repository.  -p.

---

### Post by dueY on 2006-01-03
I have done that several times with Partition Magic 8, never a problem.

---

### Post by comshock25 on 2006-01-03
I'm a long-time user of Partition Magic 8 but came across problems lately. So I've switched to using Acronis Disk Director instead. Never had problems so far.

---

### Post by Gray. on 2006-01-05
Would I lose any data if I resize an ext3 partition, so that I can create another one? I'd be using Gparted that is in the Breezy repos.

---

### Post by ubuntu27 on 2006-01-05
And also it is recommended to not use the drive/device/partition which you are going to resize.....  It is better to run gparted or qtparted from the LIVE CD

---

### Post by Gray. on 2006-01-05
So if I run Gparted from the LiveCD then I won't lose any data on the ext3 partition?

---

### Post by zahidism on 2006-01-05
i was wondering the same thing.  i havent installed linux yet but im only installing it temporarily until i go back home and i have a clean system to run it on, so i want to be able to delete the linux partition and resize the windows one to the original hard drive size.  is this easily done with Gparted on LiveCD?  are there any problems?  my windows xp is under ntfs

---

