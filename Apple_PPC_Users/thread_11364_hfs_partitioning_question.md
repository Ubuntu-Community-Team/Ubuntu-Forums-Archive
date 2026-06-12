---
title: "hfs partitioning question"
date: 2005-01-16
forum: Apple PPC Users
---

### Post by Josh101 on 2005-01-16
Hello i have been using linux on x86 for about 2 years now but ive never repartitioned a disk without formating it afterwards ... i want to do just that on this g3 mac i have a spare 15 gb and i want to partition it to hfs for Mac-on-Linux (need flash and codecs and just like it but i like linux more if you get my meaning.)


In short i want to partition this ext3 partition a 10 gb chunk out of the remaining 15 gb is this possible without distroying my linux install or risking my data?

---

### Post by farruinn on 2005-01-18
I'm not sure I understand what you're asking, but this will always hold true: modifying a partition (changing filesystem or splitting into multiple partitions) won't affect other partitions as long as they're left alone, ie start/end blocks unchanged, length unchanged, filesystem unchanged.

Now, what I think you're saying is you have a 15 GB ext3 partition that you want to break into a 10 GB ext 3 and 5 GB hfs.  This will destroy the data on the partiton unless you use a partition resizing tool, which to my knowledge can be expensive.

---

### Post by adamw on 2005-01-27
I seem to recall SuSE making the claim that they have a repartitioning tool.  Whether it's only available for NTFS or FAT32 partitions, however, I am not sure.  My guess is they probably didn't have the resources or the business case to make it handle HFS+ partitions.  However, I seem to recall seeing a partitioner at the Apple store for somewhere between $50-100.

---

### Post by chascon on 2005-02-16
debian sarge's parted shrinks HFS+ non-destructively as we speak.  I ***ume that ubuntu-ppc warty alos has this option.  The trick is to disable journalling in OS X prior.    HFS+ jounalling capability is in the works too.

Now if a dev could confirm exactly how to do this and even if it is supported with warty or hoary.  

At the very least you could pick up sarge just to resize (just use the buss card size, as it fits onto on CD), and install ubuntu henceforth.

[http://mail-index.netbsd.org/port-macppc/2005/01/28/0000.html](http://mail-index.netbsd.org/port-macppc/2005/01/28/0000.html)
vaugly explains this process.
"I booted the Debian CD in expert mode (i.e. typed "expert" at the
yaboot prompt), loaded extra packages from the CD (among them parted),
and went to the shell.  Resizing my 40 GB partition to 30 GB (about 23
GB used) took 25 hours (sic).

After that, I booted the Mac OS install disk and checked the partition
with Disk Utility.  Some inconsistencies were reported, but all in all
nothing was lost.  (I had backups, of course)"

---

