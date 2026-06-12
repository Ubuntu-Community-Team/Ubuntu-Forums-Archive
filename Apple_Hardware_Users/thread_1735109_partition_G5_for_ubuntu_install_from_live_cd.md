---
title: "partition G5 for ubuntu install from live cd"
date: 2011-04-20
forum: Apple Hardware Users
---

### Post by winston99 on 2011-04-20
I get to step 4 in the install and it tells me i don't have enough free space.  I go to "specify partitions manually" and i'm lost.  Mac osx partition leaves has all the space and it wont let me shrink it nor have i been able to create a free space partition.  Anybody recognize where my problem is?

---

### Post by nevius on 2011-04-22
Are you using the 'Disk Utility' app in the OS X Partition to change its size? What installation guide are you using (include link)?

---

### Post by winston99 on 2011-04-22
No I was gparted.  Sorry I cant find the tutorial link again, it was just  graphical on how to install/partition using gparted or install ubunta 10.4 LTS.
From reading should I have first parttioned using osx 10.5 disk utiility?  If so what file type should I choose.  This is a g5 ppc.
I might have to put the partitioning on hold as i got click happy the other night and clicked on "erase free space" in the macosx diskutility and it worked for about 4 hours and my system was lockedup the next morning and being the idiot i am i inserted the original version 0sx 10.3 install disc to reinstall the system and am now on a lockedup 10.3 version system. I had no 10.5 install disc and had to order one from apple, so i am now thinking of trying to install ubunta on one of my external drives until i get 10.5 back up and running.
Do you know exactly why "erase free space" was not a wise decision? 

I tried to resize the Osx partiton with gparted and it will not complete the operation, I can't create a screen shot but here are errors
Calibrate seems to have been successfull
Checfile system= checking is not available for the file system
growfile system to fill the partiton+ growing is not available  for the file system
libparted messages
     Input/ouput error during read on /dev/sda
     An error occurred during extent relocation
     Data relocation has failed
     Resizing the HFS+ volume has failed

Thanks

---

### Post by winston99 on 2011-04-22
In step 5 "Prepare parttions" of Install Ubuntu 10.04 LTS on a G5 powerpc do I need to prepare 3 partitions?
If so is this close?
1.. type ext3   bout 30GB   Mountpoint=  "/"   or  "/boot"
2 swap    size=???
3 Neworld or neworld boot?  size = 1mb-????

---

### Post by cfr42 on 2011-04-22
> Do you know exactly why "erase free space" was not a wise decision?

I don't quite remember this but does this write zeros to the free space? Or did you choose to have it do that? If so and if you have quite a lot of free space, it could take a long time. I wasn't clear whether it had completed in 4 hours and the lock up happened after that or if you meant that it was still going and that was locking up your system.

I've read conflicting things about whether it is possible to resize HFS+ partitions on PPCs non-destructively using gparted. If it is possible, I think it probably requires disabling journaling on the file system first (if it is enabled).

Did you succeed in reinstalling 10.3? Or did the lock up occur during the install process?

---

### Post by winston99 on 2011-04-22
ItI did not say anything about zeros, I just chose erase free space because after ubuntu install told me I did not have enough Free space I went looking around apples disk utility and sawthe option just luring me to clickit.
I did so and I told me it was doing it and it would take 4 hrs, I looked at the progress are about 2hrs later and it said 2hrs left,  went to bed and osx 10.5 was lockup in the morning.
I pretty surely instructed to reinstall is from original osx cd. I stupid and inserted original which was 10.3 and do not have 10.5 install cd and it will boot but it not good but will letme do a few basics
I saw something in a 2008 post about disabling journal and a bunch of sudo terminal commands but was hoping that in 2011 an easir way be available.  I would rather learn terminal commands later like after my initial 30 hr of time just trying to install
I have 2 external drives, one at least that I could wipe ou and install ubuntu, would that simplify this process or will I still have partition issues trying to install?

---

### Post by B_Free on 2011-04-25
If you have a Mac os X to install, do it. When you start up from the Mac OS CD, partition the drive with half Mac Extended and the other half free space (or whatever sizes you want). Install the Mac OS (or not). Restart with the 8.0.4 Ubuntu and install to the free space.

---

