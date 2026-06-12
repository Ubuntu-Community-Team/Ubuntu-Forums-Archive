---
title: "TestDisk"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by dirk1965 on 2008-03-04
Hi,

I hope someone can help me out with this.  My NTFS drive is no longer bootable.  I hard shut it down before the shut down process was totally complete.  The mfg tech suggest I use Ubuntu Live CD to recreate my MBR.  However, I think that made matters worse.  When the system boots, I instantly get an "Invalid Partition Table" error.

I read that TestDisk can possibly fix this problem.  What I dont know is if it will work on Unbuntu Live or not.  Is this application already embedded within Ubuntu, or is it something that has to be installed.  If so, this newbee could really use some step-by-step help on how to initiate the application.

Thanks!

---

### Post by glennric on 2008-03-04
I don't think that testdisk is installed by default but you can install it with
```
sudo apt-get install testdisk
```
or look for the package "testdisk" in synaptic.  I used this to recover some corrupted partitions at one point, but I can't remember exactly what I did.  I know it involved analyzing the disk with testdisk and then somehow using fsck to recover the journals.  You should do a google search on the subject.

---

### Post by dirk1965 on 2008-03-04
Does that load into memory, or does it need physical space?

Thanks!

---

### Post by glennric on 2008-03-04
I am not sure what you mean.  It installs to the disk, but runs in memory just like any other application.  Oh, if you are running the live cd it installs to the live cd's ram disk, which is contained in memory.  This is how it works for any package installed while running the live cd.  Of course when you reboot all of it is lost.

---

### Post by dirk1965 on 2008-03-04
TestDisk is not listed in Synaptic.  What next?

Thanks

---

### Post by glennric on 2008-03-04
Make sure you have the gutsy/universe repository enabled.  Also, it is testdisk (all lowercase) not TestDisk.

---

### Post by dirk1965 on 2008-03-04
Okay... I got the application running.  BTW... thank you very much for you help so far.  Unfortunately, I need more assistance.  Sorry for being such a newbie :)

When testdisk first started up, it found 3 partitions.  One is a DellUtility partition.  The other two were labeled as NTFS.  From what I've read, if two are listed, that just means that the partition is corrupt... which I suspected.  I went further into the application and now it only sees the DellUtility partition (listed as Primary Bootable) and my NTFS is not listed.  My Choices are Add partition, Load backup.  Change Type, List Files, and Enter to continue.  What should I do at this point given that its not listing my NTFS?  I don't think I want to Add.  I would think that would overright my current partition that is corrupt.  I dont want to make a move unless its correct and I wont loose my data.

Thanks again!

---

### Post by dirk1965 on 2008-03-05
I got it all figured out about 2am.  The good is that testdisk rocks!  The bad is that my nerves are shot! :)

Thanks to everyones that came to my aid.

---

### Post by dirk1965 on 2008-07-23
I'm getting the following error when running testdisk... any suggestions as to how to fix this?

Thanks!

Warning: Incorrect number of heads/cylinder 64 (FAT) != 255 (HD)
 1 P FAT16 >32M               0   2  4   243 108 57    3910527

Warning: Bad ending cylinder (CHS and LBA don't match)
No partition is bootable

---

