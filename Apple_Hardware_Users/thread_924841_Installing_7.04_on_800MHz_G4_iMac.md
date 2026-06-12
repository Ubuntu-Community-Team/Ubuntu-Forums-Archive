---
title: "Installing 7.04 on 800MHz G4 iMac"
date: 2008-09-20
forum: Apple Hardware Users
---

### Post by renichms on 2008-09-20
I have an 800MHz iMac (G4) with 512MB SDRAM.  It currently has an 80GB HDD and Mac OS 10.3.9 installed.  Connected to it, I have a 250GB external (obviously) Lacie FireWire HDD.  I used Carbon Copy Clone to copy the internal to the external and now can boot the identical systems from either HDD.  I have experimented with different partitioning of the external and found Ubuntu does not want to go on it.  So that brings me to what I actually want to ask.

Since the Lacie has had no problems for a number of years now, would you consider it safe to boot from the backed up copy on the external, wipe and partition the internal, copy 10.3.9 back to the bigger internal partition, then try to install Ubuntu (7.04) to the internal as well?  And not only is it safe (as in low risk of losing both drives in some fashion), will the Ubuntu install program run properly if it will be installing on the internal?

I've started off the CD a number of times and the installer definitely does not like the external.  I just don't want to wipe my internal HDD only to find out that Ubuntu still doesn't want to install.

Has anyone done an install like this or have most of you just switched 100% to Ubuntu or did you get a new computer, then reinstall OS X and Ubuntu at the same time?

I know asking if it's safe may seem a little silly but I have little experience in setting up dual boot systems (to be honest, the only I've tried so far and still have is the PS3).  Plenty with networking, building the machines themselves and long-term archival but not with Linux or dual boots, and since I've had the computer a long time, I hesitate to jump into this.

RN

---

### Post by mkvnmtr on 2008-09-20
First of all there is no reason to use 7.04. 8.04 is a long term support version that you will be able to use with no more problems than 7.04. I have a dual boot on my G4 Ibook. You don't need to wipe or reinstall your mac os. I would defragment using something like Drive Genius  Then you can use the installer on the live disk to install Ubuntu. The first time I installed 6.06 I believe I made a partition with Mac disk utilites for Ubuntu and then picked install the largest space. In later instalations I just went back in the same partitions to upgrade. It is safe but you should backup everything to your other disk. I think it is possible to use your other disk to boot and some people may chime in to help but it is easier to use your external disk to back up both systems and for storage for big things like movies.

---

### Post by renichms on 2008-09-20
So what is the name for 8 (since Feisty is 7, I think)?  I have never seen it anywhere before, though 7 ran better off the CD than 6.

I'm open to any and all suggestions on good, free software for creating the new partition on the internal without wiping out everything.  I have 60GB free on the internal and wanted to give 10-20 to Ubuntu.

RN

EDIT:  Downloading 8.  Once I have the right tool for making the new partition safely, I guess I'll try to install.  Everything is backed up on the external.

EDIT2:  Tools I found:  VolumeWorks, iPartition and Drive Genius.  Drive Genius says it's for 10.4/10.5 (I have 10.3.9).  Anyone have recommendations?

---

### Post by mkvnmtr on 2008-09-20
You can get 8.04.1 for ppc from the second thread pinned at the top of this forum for apple users. It's name is hardy. I believe in Mac os 10.3.9  you can use disk utility to create a partition. I think that is what I did the first time but it was a long time ago and I am old and don't remember for sure. You can also use the live disk of Ubuntu to do the job. You don't have to use bought software. I believe the program on the disk is Gparted. I did this before I tried to install and then  installed in the largest free space. In this way you don't have to manually make swap and boot partitions. Don't make your space for Ubuntu too small. I didn't know how much I would like it and left to much in my mac partition. Later when you get to like it and learn more about using it there is almost nothing you can't change to suit yourself. After you get your disk burned you might have some trouble getting it to boot the first time. My 8.04 went to a black screen and did nothing. It's no big deal with each problem just post here and somebody will see it and help.

---

### Post by renichms on 2008-09-20
Looks like we used similar methods.  I split the external into 2 partitions and just for kicks, cloned the internal startup disk to each one then copied one of those to another computer entirely, then started up from the external in 10.3.9.  Opened Disk Utility, partitioned the internal so Ubuntu would have at least 15GB, then slapped Mac 10.3.9 back onto the bigger partition.  Restarted to be sure that one would work then started from the CD, told it to use the biggest free space and on it went.  Ubuntu 8.04.1 started up, I messed with the settings to get it online and then restarted to make sure I knew how to select systems.

Right now Ubuntu only wants to connect to the closed wireless network with no password (same as Yellow Dog on the PS3) and not the WPA2 closed Airport network, so I'll have to work on that.

So thanks for tips and it's all installed now!  Just gotta tweak it and use it.

RN

---

