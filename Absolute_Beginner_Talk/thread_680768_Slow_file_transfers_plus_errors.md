---
title: "Slow file transfers plus errors"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by rwrouns on 2008-01-28
I have two computers running Ubuntu 7.10 both completely updated.  They are both connected to my network through gigabit nics and switches.  The first machine (acting as a media center) has two hard drives, one containing the file system, swap , etc. and is mostly ext3.  The second hard drive is all NTFS from its days in a windows box.  The second machine acts as the home file server and has a large raid 5 array formatted in ext3.  

I have been trying to transfer a large music file (created by Sound Juicer)  from the media center to the server with two problems: first, it is very slow, and second, it stops every 30 files or so with an error (some problem with a directory, or some form of invalid data).  The only alternatives are to retry (no luck), cancel, or skip.  I have been taking the skip option.  Checking the transferred files shows garbage or incomplete files in folders where errors were reported.  The source file created by Sound Juicer has no known errors when played on the media center.

Next I tried to copy from the first hard drive to the second hard drive on the media center, even though the second hard drive was formatted NTFS.  The entire music file of 125 gb transferred with no error halts, but it did take about 2 hours.  At least I have a backup even though it is on the same machine.  

My question is, how do I transfer this file to the server?  I have even tried to transfer to a USB external hard drive, but it is even slower than the ethernet connection.  Thanks in advance for any help.

---

### Post by mattismyname on 2008-01-28
Sounds to me like it might be HW issues.  Have you tried switching the NICs down to 100Mb instead of 1Gb and see how that goes?

Also, have you tried swapping out the NICs?

---

