---
title: "Can Ubuntu install cope with bad blocks?"
date: 2005-10-29
forum: Absolute Beginner Talk
---

### Post by Terrycymru on 2005-10-29
For several days I've been trying to install Ubuntu on a PC with 1 partition only with WinME on it. Unfortunately, during install the partitioner fails to resize the partition to free space for Ubuntu.

I've been trying various solutions to my partitioning problems in the last few days. Now when I try to resize during install I get this error:

**Input/output error during read on /dev/ide/host0/bus0/target0/1uno/disc**

The disc does have some bad blocks which pose no problem in Windows but perhaps Ubuntu's partitioner doesn't like this. **Is it possible to use Ubuntu on a disk with some bad blocks?**

---

### Post by poptones on 2005-10-29
Those bad blocks will pose a problem on windows, too - the only reason they have not is nothing has been stored in them yet (at least that you know).

Go the drive manufacturer's website and download their disk diagnostic tool. Tell it to do a thorough (complete, comprehensive - whatever word they use) disk test and if it offers to correct the errors let it. This might allow you to get the disk back to nominal function, but odds are good if it's so old it's running winme and has a failing hard drive you're not going to get ANY new operating system to install properly.

---

### Post by Terrycymru on 2005-10-29
[QUOTE=poptones]Those bad blocks will pose a problem on windows, too - the only reason they have not is nothing has been stored in them yet (at least that you know).

Go the drive manufacturer's website and download their disk diagnostic tool. Tell it to do a thorough (complete, comprehensive - whatever word they use) disk test and if it offers to correct the errors let it. This might allow you to get the disk back to nominal function, but odds are good if it's so old it's running winme and has a failing hard drive you're not going to get ANY new operating system to install properly.[/QUOTE]

OK. I used the Maxtor diagnostic tool to fix the disk errors and Ubuntu install proceeded to resize my partition to allow free space for the install. Installing the base system proceeded to retrieve the files but failed to retrieve the last file - didn't catch name - and then displayed this error:

[B]Base system installation error

The debootstrap program exited with an error (return value 1)
Check target/var/log/bootstrap.log for details[/B]

I've gone back to try the base installation again (currently retrieving files.)
If it doesn't work second time what should I do?

---

### Post by Terrycymru on 2005-10-29
Still having problem with the base system installation!

I've started a new thread in Ubuntu Breezy Badger 5.1>Installation and Upgrade Help which I now realise is the appropriate place.

If you can help me out please reply there!

---

