---
title: "Extended Record Needed (partition problem)"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by Latish on 2006-11-26
I'm installing Ubuntu for the first time (v 6.10), and when partitioning I received this error:

ntfsresize -P --force --force /dev/hda2 -s 71183794176 --no-action
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Device name : /dev/hda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 79990845952 bytes (79991 MB)
Current device size: 79990848000 bytes (79991 MB)
New volume size : 71183790592 bytes (71184 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 42953 MB (53.7%)
Collecting resizing constraints ...
Needed relocations : 7399 (31 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1056 > 1024), not yet supported!
Please try to free less space.


Does anyone know how to resolve this?  I've already ran chkdsk on Windows and defragged the hard drive.
Any help would be appreciated.
Thanks!

---

### Post by Latish on 2006-11-26
Anyone know at all? :confused:

---

