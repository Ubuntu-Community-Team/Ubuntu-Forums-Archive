---
title: "Partition Query"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Jaydos on 2007-01-16
Hello All!
After a recent fresh install I manually set up the partitions during installation. My question is, how do I view these partitions? I want to ensure that /home is indeed linked to a partition of it's own in order to save my documents if I need to do another install (Or more importantly, backing up my precious new Beryl!!!).

---

### Post by rai4shu2 on 2007-01-16
In my case, I always make different partitions different sizes. The swap is always 2 GB, the root partitions are always 30 or 40 GB, and the home partition is always 100 GB. Windows always wants the first partition, so I always leave that NTFS.

If you're running the Ubuntu Live CD, you can start up the Gnome Partition Editor, or run the install and choose the "manual" method for install. Either way will give a graphical view of your partitions.

Otherwise, if you have them mounted, you can type "df" in a console. Type "sudo fdisk -l" otherwise.

---

