---
title: "Add XP/New Hard Drive after installing Ubuntu?"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by anagnost68 on 2007-01-08
I installed Ubuntu 5.1.  Now I want to install XP on a new (not yet installed) slave hard drive.  I've been reading the other posts but haven't seen this exact scenario.  What are the detailed steps I should follow to add the second drive and then install XP on it?

Thanks!

---

### Post by scottness on 2007-01-08
You may want to check out a [thread of mine]("http://www.ubuntuforums.org/showthread.php?t=332175") from a couple days ago.  I had a similar issue with Ubuntu on the master drive and Windows on the slave.  Adding the slave drive was pretty easy, there is a good walkthrough on it [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows").  You'll have to find out the exact location of the second drive... mine was different than listed in this walkthrough.  This Terminal command will list all partitions and other hard drives:
```
sudo fdisk -l
```

  But other than that the mounting was straightforward.

If you eventually want to dual-boot, read louieb's response to my initial post.

As far as just setting up the Windows install on the blank hard drive, the simplest way may just be to unplug the hard drive with Ubuntu on it and install Windows on the other drive first...then set it up as a slave after the Windows install is finished.

---

