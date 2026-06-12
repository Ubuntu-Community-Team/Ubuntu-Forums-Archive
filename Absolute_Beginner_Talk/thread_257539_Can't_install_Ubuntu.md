---
title: "Can't install Ubuntu"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by candlepin on 2006-09-14
Hi.  I'm very new to Linux.  I want to load Ubuntu onto my older desktop computer:
Pentium 400mHz
512Mb Ram
60Gb HDD
13Gb HDD

It runs fine off of the CD.  When I go to install the newest version of Ubuntu (desktop version = same as on disk), I get to step 6/6 and my computer freezes.  

More info:
I have Windows XP and files on the 13Gb HDD, nothing on the 60Gb HDD.  I'm trying to install Ubuntu on the 60Gb HDD.  At step 5/6 I choose to "Erase entire disk:  IDE2 slave (hdd)", since there is nothing on the drive.   Would it be better to manually partition the drive (if so, how?)

Then it step 6/6 says Ready to install.  I choose Install, and the installation begins.  I've tried this a few times and each time it freezes at 0% or 24%.

Is there any way to install from without using the CD drive?  

Please help!  this frustration is only compounding the absolutely craptacular week I've had so far.  
](*,)

---

### Post by xpod on 2006-09-14
you might need to try the alternate cd....you got more than enough oomph mind you so im suprised it aint loading.

I got a lot less.....try the alternate..save some sore heads

EDIT:...sorry..try install in safe graphics mode...THATS what i had to do

---

### Post by Metacarpal on 2006-09-14
It sounds like it might be a problem with the CD.  Did you get a pre-pressed CD through ShipIt, or did you download and burn an ISO?  If you downloaded the ISO, did you check the MD5sum of the file?

(If you don't know what an MD5sum is or how to check it, [click here]("http://www.psychocats.net/ubuntu/iso") for help.

---

### Post by xpod on 2006-09-14
If it`s running fine it should be good enough to install.
Try the safe graphics mode at boot up and then install from there.I think you might just get lucky

---

### Post by bulldog on 2006-09-14
When you boot the cd,you've got an option to check the cd if there's no faults on it.
Maybe you should burn a new one on a lower speed,that will help occasionly.

When you want to install on your 60GB disk choose manual partitioning.
Make a partition of 10 GB for /  and a 1 GB swap and make the rest of your disk /home.
Format them and install Ubuntu.

Your advantage is that whenever you blow your Ubuntu  to peaces ,and you will,you can reinstall without formatting your /home so your data is safe.

---

### Post by ajgreeny on 2006-09-14
When you get to the partitioning point, select to use the largest free space on the chosen disk, rather than erase the whole disk.  I don't see why it should make any difference, but other people have suggested all the other possibilities.  Also check that you use a cd-r, not cd-rw as that can make a difference sometimes.

---

### Post by DOD1951 on 2006-09-14
I had this problem and found the way around it was to delete the partition in Windows XP and format it as FAT32.The Ubutu install worked fine after that by letting it format the disk.

---

### Post by candlepin on 2006-09-14
what file format should I use for the three partitions?
/
swap
/home

---

### Post by r_a_trip on 2006-09-14
> **candlepin said:**
> what file format should I use for the three partitions?
/
swap
/home


Swap has its own distinct format and that is automatically assigned when labeling a partition as swap.

As for / and /home, I suggest to go with the default ext3. I'm probably going to start a lengthy discussion with this, but ext3 does the job nicely and it saves the hassles of getting familiar with all the other choices. 

The other file-systems are there when you feel like experimenting. The first thing now is to get up and running with Ubuntu.

---

### Post by candlepin on 2006-09-16
Thanks for all the help!  I'm writing this from my computer running Ubuntu.  Here was my progression:

I first tried re-installing in safe graphics mode.  This did not solve the problem.  

I next re-downloaded the Ubuntu iso file and verified the MD5sum file.  A bit tedious, but I think this was the original problem.  I also burned the CD at a slower rate to try to prevent errors at that step.  I then checked the CD at startup and it had no errors.  When I went to set it up, I manually partitioned the drive as bulldog suggested with the ext3 format as suggested by r_a_trip.  And presto-magico, it worked!  

Thanks again for all the help.

candlepin

---

