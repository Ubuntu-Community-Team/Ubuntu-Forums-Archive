---
title: "Partitions for 7.04"
date: 2007-04-23
forum: Apple PPC Users
---

### Post by burobaaje on 2007-04-23
System INFO:  iMac 17"   1GHZ   80G HD

I have one HD on my iMac and it had an old version of ubuntu.  I used iPartition and removed the linux partitions and now have 13 GB free space.  I don't understand how to use this free space without destroying my OSX partition.  7.04's partition manager only sees the entire drive and will only attempt to set up partitions seemingly ignoring the OSX formatted partition.

I have free space and can format it to almost any system out there before going to live CD of 7.04.  So how do I install 7.04 on this unused space without having to destroy and re-install OSX?

Help!

---

### Post by ssam on 2007-04-24
having it as free space is best.

there should be a manual option on the installer that lets you make partitions. if not you may have to use the alternate install cd

---

### Post by grazie on 2007-04-24
I'd be a little concerned that the partition tool doesn't see the OS X partition. Have you tried
```
$ sudo mac-fdisk -l
```
in a terminal.

---

### Post by burobaaje on 2007-04-24
System INFO:  17" iMac   1GHZ  80G HD

Strange strange.  iPartition only shows 3 partitions on the iMac's HD.  2 are Mac partitions and the other is free space or at times I have made it a Linux partition hoping that the ubuntu installer would see it.  Using manual I get weird partitions, like 77.7 G for a mac partition and then 80 G free space when the drive is only 80 G.

using mac-fdisk it gives 11 partitions.  A bunch of small unknown partitions and then the 2 mac partitions at hda09 and hda10 and finally hda11 is the free space or the linux partition.  But, I cannot get the installer to see them.  Maybe having so many partitions is the problem.  I don't know why all those little ones are there.  iPartition does not show them!!

I guess I am going to have to be willing to trash the OSX and reload everything if I want to install ubuntu.

---

