---
title: "Getting an external HD to mount"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by rmellish on 2008-03-08
So I just installed the ntfs 3g packages, and now instead of my external hard drive coming up with the unable to mount error, it will not appear. 

Btw, I've only had Ubuntu for about an hour, so any help would be appreciated.

---

### Post by rmellish on 2008-03-08
Ok, so I just searched (sorry) and did the sudo fdisk -l 

this is what i got for the freeagent drive

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

---

### Post by sattruckmark on 2008-03-08
I also have a Freeagent drive.  

I found that the drive must be unmounted using the "safely remove hardware" in windows.  If the drive isn't unmounted, Ubuntu can't mount it.  I believe that there's a command that can force the drive to unmount, but I cant' remember it.

---

### Post by herbster on 2008-03-08
A lot of these issues are indeed because people forget to hit Safely Remove in Windows before they plug the sucker in to Ubuntu.

---

