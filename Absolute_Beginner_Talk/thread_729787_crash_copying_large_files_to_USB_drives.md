---
title: "crash copying large files to USB drives"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by linux_believer on 2008-03-20
I have a problem copying large amounts of data to USB drives. Seems like it crashes everytime. 
I have 2 USB drives:
80gig Western Digital
500gig Western Digital

I have not changed the file structure of the drives so I assume its NTFS.  When trying to transfer a 7 gig iso they both crash. When copying several smaller files ranging from 1-10megs each, total about 2 gigs it crashes during this process also

Currently running 7.10
Someone please advise

Thanks

---

### Post by ajgreeny on 2008-03-20
That's wierd!  NTFS file system has a huge (in practical terms, unlimited) size limit of 16 Exabytes, so there should be no problem with 7GB.  Have you tried using rsync or grsync to do the copying?  I see no obvious reason why it should make any difference but it's worth a try.

However, as you haven't looked to see the file systems on the drives, perhaps you should, as they may be fat32 or even fat16 which will not accept files that large.  Plug in the drives and run ```
sudo fdisk -l
``` to see what file systems are there.

---

### Post by notwen on 2008-03-20
If it comes down to it, you could always split the 7GB iso into smaller .rar files and transfer it, then unrar.  =]  Good luck w/ your moving files.

---

### Post by linux_believer on 2008-03-20
Thanks ajgreeny

Looks like both  drives are W95 FAT32 (LBA)
Is there a way to convert it to NTFS without destroying the data. I still want to be able to share data with windows machines.

---

### Post by Jerry N on 2008-03-20
I think WinXP has a utility to convert from Fat32 to NTFS without destroying the data but I have never tried it.  Gparted , System Rescue, Partition Commander, and Knoppix would convert from Fat32 to NTFS but I don't know if any of them would do that without destroying the data.

Jerry

---

### Post by ajgreeny on 2008-03-20
If there's space just copy all the data from one of the external disks to the other so it's all on one, or onto the internal disk, then reformat the one to ntfs and copy data across and do the other.  I would feel very nervous doing it without some backup of some sort.

---

