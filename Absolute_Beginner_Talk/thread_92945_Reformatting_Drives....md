---
title: "Reformatting Drives..."
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by Todd_Z on 2005-11-20
Is there a linux alternative to partition magic?  Heres the drive's setup:

NTFS - 50 gigs/30 free
NTFS - 12 gigs/3 free
Ext3 - boot drive
Ext3 - 14/7
Swap - 1gig

I want to truncate the Ntfs drives to have no overhead, put them to the beginning of the drive and then clear all the other space and turn it into a reiserfs partition.  How do i do this?

---

### Post by LuxoDave on 2005-11-20
You can get QTparted, I believe it is called. It is in the repositories and is easy to use. I used it a few days ago.

---

### Post by aysiu on 2005-11-21
QTParted
GParted
DiskDrake (I personally recommend this, even if you're not installing Mandriva)

---

