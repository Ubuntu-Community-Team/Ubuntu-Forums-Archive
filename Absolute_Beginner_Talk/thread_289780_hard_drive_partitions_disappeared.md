---
title: "hard drive partitions disappeared"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by LeftyMills on 2006-10-31
Old computer - around 1999.  Bios limit - 32 MB.  Hard drive 40 MB - jumpers on hard drive and bios set to 32 MB. Dual boot - Windows 98 SE and Ubuntu.  When trying to install/upgrade from 6.06 to 6.10 I messed up the partitions in gnome partition editor.  It shows my partitions as "unallocated 37.31 GB" and nothing else.  But this is not right - the partitions are still there, and Windows 98 runs fine.
When I "sudo fdisk -l", I get a "warning: invalid flag 0X2020 of partition table 8 will be corrected by w(rite)". I then can see all partitons.  
How can I correct this situation so that I can work ahead with  GParted?

---

### Post by x64Jimbo on 2006-10-31
Windows is only still working on a fluke. I highly suggest you back up all your data in Windows and do clean installs of both before something bad happens.

---

