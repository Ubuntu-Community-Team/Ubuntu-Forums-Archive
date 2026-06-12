---
title: "access to HFS+"
date: 2014-02-10
forum: Apple Hardware Users
---

### Post by southpaul on 2014-02-10
Hi
I'm doing due diligence prior to installing one of the ubuntu clan, I plan to dual boot on a mid2007 imac. In my looking through the forum and other information the most recommendations are to unjournal HFS+ to enable read and to force to write to a HFS partition when in ubuntu. wikipedia mentioned problems with 2+GB drives in HFS and linux, hence the caution and use of unjournalled HFS. (Still trying to grasp this stuff, so please excuse any inaccuracies) 

I am interested to know if anybody has used the drivers from Paragon software. Paragon NTFS & HFS for Linux Express? They claim full read/write to HFS+ partitions (or volumes as Apple calls them).  being proprietary software it is closed source I guess, however it does seem to offer a significant advantage at the moment, and the express version is free. 

The web page I looked at was here, [http://www.paragon-software.com/home/ntfs-linux-per/features.html](http://www.paragon-software.com/home/ntfs-linux-per/features.html)

I would be interested in any knowledge/experience about this as there does not seem to be much comment about the Paragon drivers for Linux on the web that I could find.

---

### Post by DiagonalArg on 2014-06-21
I'm interested in this myself, if anyone's had any experience.

Also, I'm not clear on the status of hfsprogs regarding >2TB disks and journaling for hfs+ volumes.  Does anyone know?

---

### Post by DiagonalArg on 2014-06-21
Some mention of the issue (patch to get it to work on 14.04), here: [http://ubuntuforums.org/showthread.php?t=2217794&p=13034712#post13034712](http://ubuntuforums.org/showthread.php?t=2217794&p=13034712#post13034712)

---

