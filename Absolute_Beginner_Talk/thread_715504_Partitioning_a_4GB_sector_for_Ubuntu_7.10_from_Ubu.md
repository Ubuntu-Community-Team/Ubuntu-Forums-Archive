---
title: "Partitioning a 4GB sector for Ubuntu 7.10 from Ubuntu CD"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by halberdier25 on 2008-03-04
OK.  I have a 50GB HDD in my laptop, with a little over 10GB free, and I would like to partition somewhere from four to five GB for Ubuntu 7.10 on it.  On my desktop, there was a handy little disk partitioner that came with the machine, but my laptop has no such program.  From within the Ubuntu CD Installer, once I get to step four (or whichever step gives the partitioning options), what do I do?  I don't want to lose any of my data already on the HDD.

Thanks in advance,

---

### Post by Madman6510 on 2008-03-04
I'm assuming you already have some version of Windows on the laptop, right?

You will need to choose the manual option and manually partition the drive. Resize the NTFS partition so you have about 7GB of free space, then create a 5GB / (formatted ext3) and a 2GB swap partition (formatted swap).

However, 5GB is JUST enough to run Ubuntu. You should try to get at least 10GB on the / partition.

---

