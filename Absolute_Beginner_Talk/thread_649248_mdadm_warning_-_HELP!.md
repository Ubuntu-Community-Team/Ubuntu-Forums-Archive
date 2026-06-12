---
title: "mdadm warning - HELP!"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by matadorpw on 2007-12-24
Hi all,

I'm hoping someone out there has come across this before and can help.  Google has apparently never heard of this message before.

I have a server running Ubuntu, kernel 2.6.20-15-server that has a RAID 1 array of 2 500GB SATA drives.  Everything has been running smoothly until one day last week when we lost power for longer than the UPS could take.  When I started the server back up, the following message scrolls up the screen:

mdadm: WARNING /dev/mapper/nvidia_adcdaagb1 and /dev/sda1 appear to have very similar superblocks.
[INDENT]If they are really different, please --zero the suberblock on one.[/INDENT]
[INDENT]If they are the same or overlap, please remove one from the DEVICE list in mdadm.conf[/INDENT]

This message zips up the screen forever and nothing I do (other than reboot) can make it stop.

If I boot up off the CD and choose the repair a broken system option, I can get a shell on /root.  Running mdadm --misc --detail /dev/md0 gives:
[INDENT]/dev/md0:
Version : 00.09.03
Creation Time : Wed Dec 19 16:14:53 2007
Raid Level : raid1
Array Size : 488383936 (465.76 GiB 500.11 GB)
Device Size : 488383936 (465.76 GiB 500.11 GB)
Raid Devices : 2
Total Device : 2
Preferred Mirror : 0
Persistence : Superblock is persistent

Update Time : Mon Dec 24 05:27:51 2007
State : clean
Active Devices : 2
Working Devices : 2
Failed Devices : 0
Spare Devices : 0

UUID : 59e496cb:681bf036:dcdaea22:5e5711f5
Events : 0.36

Number     Major     Minor     RaidDevice     State
0                  8             1             0                      active sync  /dev/sda1
1                  8             17          1                       active sync  /dev/sdb1[/INDENT]


I checked /etc/mdadm.conf and all it has in it is:

[INDENT]DEVICE /dev/sda1 /dev/sdb1
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=c6887a7d:9e2afeb3:4632517e:30d10b16[/INDENT]



I tried deleting this file to see if that would make any difference, but the exact same thing happens.  I also tried the --zero-superblock on /dev/sda1, but that didn't make any difference either.  I would try it on /dev/mapper/nvidia_adcdaagb1, but there is no such file in the /dev/mapper.

If I physically disconnect both sda1 and sdb1, the machine will boot up, but with either or both drives connected, I'm back to the eternal warning message.  I was able to mount one of the drives in another machine, so I know that at least one of the drives is perfectly fine.  All files there, no errors, etc.

I'm way out of my depth here and really, really hoping that someone out there has some idea of how to recover from this.

Thanks!
Phillip

---

### Post by blueridgedog on 2007-12-29
This thread has had a lot of views, but no real help.  Perhaps you should post it in the hardware forum as its complexity is a bit beyond the beginner level.

---

