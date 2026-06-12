---
title: "Hard drive recognition?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by try2lickurelbo on 2007-06-21
I just did a clean installation of Ubuntu Feisty Fawn, with two physical hard drives.  I have the /, /home, and swap partitions on the first one.  The second drive (slave) is just a large single partition.

Installation went by perfectly, but when I run it, I can't seem to find the second drive on the file viewer.  It is seen on the hardware information, but can't get to it.  Can someone help me?

Regards,
Mitch

---

### Post by atria on 2007-06-21
Depending on the location of your second disk partition, execute these in your terminal:

Create a mount directory (do it only once)
```
sudo mkdir /media/disk2
```

then mount the disk
```
sudo mount /dev/sdxx /media/disk2
```

where /dev/sdxx is the location of your second disk partition. For example /dev/sdb1.

If you want it to mount automatically check out fstab (Do a search on the forums for that since i'm rushing for time)

---

