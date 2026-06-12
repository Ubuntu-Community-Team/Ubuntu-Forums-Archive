---
title: "Very large problem. Harddrive completely missing."
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by guitarfreak2765 on 2007-12-11
Alright, something not so good happened on my laptop. I was starting up GPlaced (I think that's the name, can't think too straight right now). When it started up though, it said my entire hard drive was unallocated space, all 111GB of it. I turned off my power and restarted the laptop, but then it wouldn't start Windows. It kept saying I needed to repair, but it couldn't fix the problem, and just got stuck in a loop. I just decided to reinstall Vista. When I went to install it, it gave me the choice of installing on a 10GB Recovery drive or the 99GB drive that it used to be on. When I selected the 99 drive, it stated that Windows couldn't be installed on a NTFS or something like that. My only option was to use the Recovery drive. Now that it's installed, the 99GB drive is completely missing. I can't find it anywhere, and now I can't install anything due to lack of space.

What the hell am I supposed to do now? I was just trying to install Linux, and now my laptop is barely running.

---

### Post by rockinlinux on 2007-12-11
i think you mean gparted, and that is exactly what you need to use now. please boot from the gparted disk and come back and tell me what you see. The 99GB is still there you just need to find it. Also do you have recovery disks? if i were you i would try to make the lap top how it was when you first got it....i hope you have disks and not just the partiton..... :)

---

### Post by meborc on 2007-12-11
so you did something wit GParted (i'm guessing here)... are you sure you didn't erase some partition information?

what you need is a partitioning tool for vista... there should be something on the net... you most probably have messed up the partitioning data and vista just can't see your drive... that does not mean it is not there :)

oh, and WHY ON EARTH would you use any GPxxxxx for installing linux anyway? :) the ubuntu livecd installer (or alternatecd installer) has a built in partitioning tool...

---

### Post by rockinlinux on 2007-12-11
meborc is right....partitions dont just disapear. did you do anyhting in gparted?

as for using gparted for installing linux, some people do this but if it your first time installing linux i would not recomend it. ubuntu live cd will do it all for you in a very easy way. 

and i was just thinking about how you installed vista on you 10GB partition....im pretty sure vista takes like 20GB so im not sure its ont that 10GB partition.  can you just do a compleat system restore? this would allow you to start compleatly over.

---

### Post by guitarfreak2765 on 2007-12-11
Everytime I boot up GP, it just shows 111gb of unallocated space.

---

### Post by rockinlinux on 2007-12-11
ok well then...

try to go back and restore your computer form the partition or disks (whatever you have). leave the 111gb unalocated and if it wont put vista there try to format it to NTFS and try again.

---

### Post by meborc on 2007-12-11
turn that allocated space into a ntfs partition... if you do that, vista will see it... of cource if you had some data on it you want to recover, you would have to use some spesific soft to do that before you partition it...

---

### Post by 2n01cal on 2008-07-09
Hey, I have similar problem, now I am writing from LiveCD Ubuntu 8. My GParted is showing that whole my 250GB disk is unalocated with no partitions, but this is wrong. I have 4 partitions there and Windows is working fine.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a93b30f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20480000    7  HPFS/NTFS
/dev/sda2            2550       15298   102400000    7  HPFS/NTFS
/dev/sda3           15299       30402   121316160+   5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda4           15299       17847    20474811    7  HPFS/NTFS
/dev/sda5           17848       30402   100835328    7  HPFS/NTFS


But Gparted is showing all space Unalocated, so I can't install Ubuntu =/ Ubuntu 7 was fine and 6 also.

---

