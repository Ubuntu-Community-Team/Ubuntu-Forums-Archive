---
title: "Best Partition Arrangement"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by Archgarth on 2007-01-21
My situation:  Two hard drives, the first drive with NFTS for Windows XP, the second for general media storage and Ubuntu.

My Goal:  To format the second hard drive with a linux swap file, 50 GB for Ubuntu, and set aside the rest in Fat32 format so I can access my media from both Ubuntu and Windows XP.  So, I'd like to have three partitions on this second drive, and I can't seem to figure out the best way to do/mount/configure this setup.

Help is appreciated and welcomed, thank you.

---

### Post by mikewhatever on 2007-01-21
Ubuntu partition is mounted as root (/), Swap is not mounted, and Fat32 is mounted by default in /media/sdb3. Doesn't LiveCD have those by default?
Since I am no expert, you might want to wait for confirmation from others.

---

### Post by ComplexNumber on 2007-01-21
have about 1GB or less for swap partition, about 30GB for your home partition, and about 19GB for "/"(root) partition. thats what i would suggest. your home partition can then be used as a permanant storage area.

---

### Post by Buck2348 on 2007-01-21
How big is the drive?  Notice that ComplexNumber is suggesting four partitions instead of three:
/ (Ubuntu system, or "root"), /home (for your documents and settings), swap, and Fat32.  These will show up in Gparted or whatever partitioner you're using as /dev/hdb1, /dev/hdb2/ /dev/hdb3 and dev/hdb4.  (sdax instead of hdax if they're sata drives).  I strongly agree with his suggestion--with your personal data in its own partition, you can reinstall the whole system without losing it.  One thing--you won't need more than 10 gig or so for the system unless you plan on installing most of the software available.  Mine is only 4 gig and I'm using 2.5.  I can enlarge it if necessary.  Post again if you're having problems--someone will help.

Buck

---

### Post by Archgarth on 2007-01-21
The drive is 200GB.

---

### Post by Bachstelze on 2007-01-21
10 GiB for Ubuntu's root
1 GiB swao

the rest is all up to you, make a 1 GiB /home for Ubuntu if you don't intend to store anything on it and format the rest as FAT32. Be careful though, FAT32 can't have files bigger than 4 GiB. If that's a concern use ext2 instead, there are pretty good drivers to access it from WIndows nowadays.

---

