---
title: "installing linux on 300GB HD"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by surushm on 2006-10-03
Hi Guys
I have 300gb HD and want to install linux(redhat,xandros) but it not installs while I installed these linux on my 80GB HD.
anyone know limitation of installing or any comments??

Thanks
surush

---

### Post by ian.l on 2006-10-03
There shouldn't be a size limitation that would affect a 300GB hard drive, however you may be having a controller driver issue. I am guessing the 300GB drive is SATA, whereas the 80GB drive is IDE?

Please provide the error you are receiving while trying to install on the 300GB drive.

---

### Post by bodhi.zazen on 2006-10-03
[Boot 100+ OS](http://www.justlinux.com/forum/showthread.php?threadid=143973)

---

### Post by anaconda on 2006-10-03
are you trying to boot to a partition that is more than 130GB from the beginning of the hd..?

Several years ago there was a problem with that. Don't know if it's still a problem.. propably not.

---

### Post by surushm on 2006-10-04
Dear ian.l
My 300Gb Hd Is IDE.

---

### Post by surushm on 2006-10-07
Dear Anaconda
>are you trying to boot to a partition that is more than 130GB from the beginning of the hd..?
My Hard is 300GB but the first partition is 20GB.

---

### Post by sister_clamp on 2006-10-17
This is also a question near and dear to my heart. 

Originally had IDE 250GB. Linux installation crashed.
Swapped out IDE for 320GB SATA II. Linux installation crashed.
Bought 80GB SATA II and installed Windows 2000. Worked.
Used Windows Partition Manager to slice 320GB HDD into 3x100GB slices.
Installed Linux installation on one of these partitions. Linux still crashes but further along! (topic for another thread) :)

Would be VERY interested to know the root cause.

Regards,
S_C

AMD64 3200+ Socket 939
DFI LanParty UT-4 SLi-D
80GB SATA II
320GB SATA II
1GB RAM

---

### Post by bodhi.zazen on 2006-10-17
> **sister_clamp said:**
> This is also a question near and dear to my heart. 

Originally had IDE 250GB. Linux installation crashed.
Swapped out IDE for 320GB SATA II. Linux installation crashed.
Bought 80GB SATA II and installed Windows 2000. Worked.
Used Windows Partition Manager to slice 320GB HDD into 3x100GB slices.
Installed Linux installation on one of these partitions. Linux still crashes but further along! (topic for another thread) :)

Would be VERY interested to know the root cause.

Regards,
S_C

AMD64 3200+ Socket 939
DFI LanParty UT-4 SLi-D
80GB SATA II
320GB SATA II
1GB RAM


What version of Linux? 32 or 64 bit? error message?

I have no problems with my large HD.

---

### Post by MRCeltic on 2008-02-21
I had a similair issue with Ubuntu 7.10 Gutsy, It would not install at all so I never got to the crashing part.  The first time i installed it i didn't use almost 100GB on the drive cause i reserved it for windows.  But i decided to just use win4lin and try to reinstall Ubuntu and use the entire 300GB of the hard drive.  After numerous attempts which all failed the installation.  I ended up using 145GB for the main Partition, then using another 145GB for RAID, and the remaining 10GB for swap file (which) will never get used entirely, But since i have done that i have not had a problem at all.  Performance is better than using just one primary drive also, So my suggestion would be that if you have a larger hard drive that you are using for your installation, just partition it and make two large partitions and set one of them as RAID, also I would use the Alternate CD as for me I couldn't even boot using the Live CD,  This computer is one that is at work 3.0GHz Core 2 Intel Desktop board 1GB ram on board vid & sound

---

