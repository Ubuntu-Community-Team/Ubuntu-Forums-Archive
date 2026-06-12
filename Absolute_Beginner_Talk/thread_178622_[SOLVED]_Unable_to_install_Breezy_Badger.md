---
title: "[SOLVED] Unable to install Breezy Badger"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by ithaka on 2006-05-18
Hi,


I am not unexperienced in Linux but I can't get Ubuntu 5.10 working. I searched for similar posts on this list put all I tried did not help.
The problem is that the installation step "Copying remaining packages to disk" (or something like that) stops at about 34% claiming that something is wrong with the cd or that I may have run out of space on /var.

I indeed created only one partition (20GB) containing the root and one swap partition (2GB, on a 512MB workstation). These 2 partitions are situated at the end of my 80GB hard disk. The other partitions are assigned to WinXP (no slapping please!).

All the stuff I already tried:
  - burning at different speeds (down to 2x speed)
  - burning TAO and DAO
  - downloading the ISO from another location HTTP/FTP
  - selecting another filesystem (ext2/ext3)
  
Perhaps I should create different partitions e.g. /home /var... but I have no idea how I should split up the 20GB. The installation will only serve for day-to-day 'normal' use. I also plan to run the Apache/MySQL/PHP setup that currently run on my Windows partition.

Any ideas or reference to some pages/documents very welcome!


Thanks in advance.

---

### Post by Sef on 2006-05-18
> All the stuff I already tried:
- burning at different speeds (down to 2x speed)
- burning TAO and DAO
- downloading the ISO from another location HTTP/FTP
- selecting another filesystem (ext2/ext3)

Did you do an md5sum?

[https://wiki.ubuntu.com/HowToMD5SUM?highlight=%28md5sum%29]("https://wiki.ubuntu.com/HowToMD5SUM?highlight=%28md5sum%29")

---

### Post by nalmeth on 2006-05-18
Yes, you could try downloading another image, and checking it's integrity with md5sum check.

You might want to give the upcoming dapper drake 6.06 release, set to be out in < 2 weeks.

---

### Post by ithaka on 2006-05-18
[QUOTE=Sef]Did you do an md5sum?

[https://wiki.ubuntu.com/HowToMD5SUM?highlight=%28md5sum%29]("https://wiki.ubuntu.com/HowToMD5SUM?highlight=%28md5sum%29")[/QUOTE]

Sef, that is one thing I forgot to mention, I did indeed an md5sum. On the single ISO file and on the individual packages.

---

### Post by ithaka on 2006-05-18
[QUOTE=nalmeth]Yes, you could try downloading another image, and checking it's integrity with md5sum check.

You might want to give the upcoming dapper drake 6.06 release, set to be out in < 2 weeks.[/QUOTE]

I could indeed wait another week or two but the weather out here is no good so I thought I gave I a try...

---

