---
title: "Partitions"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by bigal1932flying on 2007-04-27
[SOLVED]I recently used g4l to image my Ubuntu 10GiB hard drive to an 80GiB drive. When I looked at my hard drive details I noticed that I had 65.41GiB of unallocated space. So without having a clue I used gparted to change my partitions. When I check my hard drive details now it shows that I have a dev/hda1 of 9.12GiB flagged as boot, and a dev/hda2 extended of 65.41GiB as well as a dev/hda5 linux-swap of 65.41GiB. Is this setup anything like it shoud be? And if not, what do I need to do?

---

### Post by antoz on 2007-04-27
You cetainly don't need all of that for swap, 1.5 times your Ram is enough. You can shrink that and then create an other partition for your files like music and pictures (all stuff that takes a lot of room) or you could make it your home partition.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Sef on 2007-04-27
> a dev/hda1 of 9.12GiB flagged as boot,

No problems there.

> dev/hda2 extended of 65.41GiB

ok too.

> dev/hda5 linux-swap of 65.41GiB

As antoz said, swap should be 1.5 your ram.  However, there is an exception to that.   If you have GB or more of ram, then you really don't need swap unless you do movie editing, heavy photo editing, or play games that are graphics intensive.

---

### Post by keithcausey on 2007-04-27
I am having similar problems. I am trying to install Ubuntu on the upper partition of a soon-to-be dual boot Ubuntu/XP system. The 40gig hard drive was initially split into two 20gig sections. I took the upper partition and divided that into three partitions thinking that would be enough. I intended one to be /, another to be /home, and another to be swap. When I tried to install from the live CD I assigned each of the partitions to the corresponding file names and I get stuck there. The error report is that there is 'no root file system'. Here is what the layout in the install window looks like...

/media/hda1        19Gb       Partition 1 Disk IDE/ATA (Primary) [HDA1]
swap                        2Gb        Partition 6 Disk IDE/ATA (Logical) [HDA6]
/home                    12Gb       Partition 7 Disk IDE/ATA (Logical) [HDA7]
/                                 5GB       Partition 5 Disk IDE/ATA (Logical) [HDA5]

By the way, directly before I got to this screen I right clicked Partition 5 and declared it to be /root.
Thank you for your help.

---

