---
title: "fail to restart after install (dual g5)"
date: 2006-12-09
forum: Apple PPC Users
---

### Post by bahbo on 2006-12-09
I installed a second sata drive in my boy's mac, and partitioned it so that there was 100gb free space at the beginning of the drive (the second half was hfs+).  I then turned off the power, disconnected the original sata drive with osx on it, and installed ubuntu using the alternate install cd.  Everything went fine, and I made a 1mb new world bootable partition at the beginning of the free space, which yaboot was installed in.  The install seemed to go fine, but when I came to the point where you restart the machine, yaboot isn't found.  I went into open firmware (ctrl opt o f) and tried typing various options (such as, boot sda2,yaboot, boot sda2:2, yaboot, etc.), but nothing seems to work.  yaboot is installed in partion 2 on the sata drive, but I don't know how to get it to be recognized by the firmware when starting up.  Any suggestions?  I really don't want to start over if possible.  Thanks

---

### Post by stream303 on 2006-12-10
I'm kind of lazy so wonder why you needed to take out the drive?  I'd just tell the partitioner when it came time to install to just install on the second disk (/dev/sdb) and use "largest free space".

I know you don't want to hear it, but it might be the fastest way to go.  Maybe someone else can suggest a quicker workaround.

---

### Post by bahbo on 2006-12-10
This morning I booted in with a live cd, copied the yaboot and yaboot.conf files elsewhere, then ran ybin, telling it to use the original yaboot and yaboot.conf files.  It said it was installing it on /dev/sda2, was blessing the folder with penguin pee, etc.  But i still can't figure out how to find it when booting up; I can't find it when holding down the option key and booting, or through the openfirmware.  

I may have to go the route of a completely new install, but I keep thinking the solution should be easier than that.  Thanks.

---

