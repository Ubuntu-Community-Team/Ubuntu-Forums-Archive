---
title: "unable to access extra hard drives ubuntu dapper"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by Shug98 on 2006-08-27
Hello all 
I have just installed ubuntu on my box and this is the 1st time with a linux os well i have a lil problem i have 3 hd's one is an 80 gig that is the file system drive this one i can access. the other two are ntfs ( under Microsoft Xp) one is a 100 gig and the other is 120 gig I am unable to mount or access these drives this is the error that i get on both drives
 
error: device /dev/hdd1 is not removable
error: could not execute pmount

error: device /dev/hdg1 is not removable

error: could not execute pmount



Could some one please tell me or show me how to get to my music and music files on these drives thank you for your support:confused:

---

### Post by anaconda on 2006-08-27
pmount is used only for removable disks. And you obiviously are trying to use  fixed disks.

You can add your disks to /etc/fstab -file, so that they will be automatically mounted each time you boot your machine

Or

you can mount them manually (from command-line, ie. terminal)
```

sudo su    -- get root rights
mkdir /mnt/temp   -- make a directory, where you will mount your hdd1
mount -t auto /dev/hdd1 /mnt/temp  --do the actual mount
``` 
Now your hdd1 will be accesible in /mnt/temp, you can access it as user root (administrator)
to get root rights, you can type 'gksudo nautilus' in command-line.

---

### Post by podunk on 2006-08-27
I used the instructions on this page:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

and they worked like a charm.

---

### Post by swkiller on 2006-08-28
I also seem to be having the same problem

error: device /dev/hda1 is not removable
error: could not execute pmount

I've followed the above guide to be sure I did it correctly, and can access my fat32 partition if i manually go to the folder that I created (/mnt/shared for me) but If i go to Places -> Computer and select the drive, I recieve that error.  The drive also does not appear under Place in the menu and am not sure why.

fdisk -l

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4833    38821041    7  HPFS/NTFS
/dev/hda2            4834        6254    11414182+   c  W95 FAT32 (LBA)
/dev/hda3            6255        7165     7317607+  83  Linux
/dev/hda4            7166        7296     1052257+   f  W95 Ext'd (LBA)
/dev/hda5            7166        7296     1052226   82  Linux swap / Solaris


in my /etc/fstab I have

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2    /mnt/shared vfat  iocharset=utf8,umask=000  0    0
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

where /dev/hda2 is the Fat32 shared drive I'm trying to mount and get correctly working.

Any ideas or things I should try? :confused:

---

