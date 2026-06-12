---
title: "help with ntfsresize!"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by jpgv on 2007-09-27
So, this is what ntfsresize says.  I have done chkdsk several times and it doesn't report bad sectors, so I decided to run the -b option.  Is this a hardware problem, any ideas?

ubuntu@ubuntu:~$ sudo ntfsresize -n -b -s 14G /dev/sda2
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name        : /dev/sda2
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 19962753536 bytes (19963 MB)
Current device size: 19962754560 bytes (19963 MB)
New volume size    : 13999993344 bytes (14000 MB)
WARNING: This software has detected that the disk has at least 5 bad sectors.
WARNING: Bad sectors can cause reliability problems and massive data loss!!!
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 10009 MB (50,1%)
Collecting resizing constraints ...
Needed relocations : 100842 (414 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Failed to empty $FILE_LogFile/$DATA : Input/output error
Fallo de segmentación (core dumped)

This last line says "segmentation fault" btw.

Thanks for your help,

jpg

---

### Post by Clay_Banger on 2007-10-01
have you tried using gparted instead?

---

