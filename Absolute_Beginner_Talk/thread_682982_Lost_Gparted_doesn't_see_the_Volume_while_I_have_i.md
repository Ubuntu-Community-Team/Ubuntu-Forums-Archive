---
title: "Lost? Gparted doesn't see the Volume while I have it on the desktop?"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Desperate on 2008-01-30
As I happily reported here -- [http://ubuntuforums.org/showthread.php?t=682096](http://ubuntuforums.org/showthread.php?t=682096)  --  I have my windows disk on the desktop now, So I thought I'll make some room for my Ubuntu installation there, but Gparted can't find it?? All I see is a Volume of the right size, mounted from the right info with a warning sign that spells out

 " Failed to startup volume:Invalid argument
 Couldn't mount device '/dev/mapper/isw_blahblah_RAID0
 Unable to find mountpoint
 Unable to read the contents of this filesystem!
 Because of this some operations may be unavialable. "

ubuntu@ubuntu:~$ fdisk -l

Disk /dev/sdc: 2048 MB, 2048728064 bytes
64 heads, 63 sectors/track, 992 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x000251aa

   Device Boot      Start         End      Blocks   Id  System *** my 2gig USB stick
/dev/sdc1   *           1         992     1999749+   6  FAT16

Disk /dev/sdd: 65 MB, 65798144 bytes
4 heads, 32 sectors/track, 1004 cylinders
Units = cylinders of 128 * 512 = 65536 bytes
Disk identifier: 0x0d0c0b0a

   Device Boot      Start         End      Blocks   Id  System *** my 65MB USB stick
/dev/sdd1   *           1        1004       64240    6  FAT16

** And that's it ?
I can browse the windows SATA RAID disk without a problem though, so I need a hint again to figure this out before I can think about installing Ubuntu on a "cleared" partition.


Thanks again for reading this.

Richard

**Edit:**
And unmounting it gives me this warning ?  
"umount: only root can unmount /dev/mapper/isw_bccebhcagd_RAID01 from /media/windows" so should I start Gparted as root to be able to change it?

---

### Post by dstew on 2008-01-30
Gparted will not work properly on mounted disks. To unmount the disk, you can right-click and pick unmount, or on a command line use the sudo command to give yourself root privileges:```
sudo umount /media/windows
```Also, you need to use sudo for fdisk to see all the volumes. Without sudo, it will only show the partitions owned by the user.

---

### Post by Desperate on 2008-01-30
Thanks, but Gparted can not recognize the ATA RAID volume when not mounted either It shows it as a device in /dev/sda1 and /dev/sda2 and claims that I have no rights to mount it while showing a warning

[http://ubuntuforums.org/showthread.php?t=675038](http://ubuntuforums.org/showthread.php?t=675038)
and
[http://ubuntuforums.org/showthread.php?t=671246](http://ubuntuforums.org/showthread.php?t=671246)

So how would I start Gparted as Root? 

Thanks for your time

Richard

BTW: I shut down Ubuntu live as normal, beeped a bit, but windows is still working :)

---

### Post by dstew on 2008-01-30
If you want to partition a RAID, gparted will not work very well. See [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

But maybe I don't understand what you want to do...

---

### Post by Desperate on 2008-01-31
@dstew,
Thanks, working on that, report back here as soon as time allows :(

Richard

---

