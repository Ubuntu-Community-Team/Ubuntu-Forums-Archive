---
title: "Partitions for Dual Booting"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by Stusi on 2006-10-19
I have 2 SATA drives, one 80 gig and one 120 gig.  I want to install both ubuntu and windows on my system but i was wondering a few things first.

Is it better to install both OS's to one drive or one to each? And if i want to install both to my 80 gig drive and use my 120 as a storage space would linux be able to read it ok (and should i format it for NTFS or just leave it unformatted?).  And 2 random questions, can people get high end videogames working in wine such as HL2 or BF2? And why does my volume in ubuntu seem to be less that of windows (with all my settings turned up).

Thanks

---

### Post by Bachstelze on 2006-10-19
Hi and welcome to Ubuntu :)

Personnaly, I'd install both OSes on the 80 GiB drive and use the 120 GiB for storage. If it is NTFS-formatted, Linux will read it without a problem but writing to it will be a bit more tedious. Better use FAT32, both Windows and Linux can read/write it natively.

---

### Post by gn2 on 2006-10-19
I definitely prefer the option of each OS with it's own bootloader on it's own hard drive.

Each OS can read the other's data, it's writing that's the tricky part.

Here's my how-to thread: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

