---
title: "Problems mounting disks"
date: 2007-01-10
forum: Apple PPC Users
---

### Post by samden on 2007-01-10
I have a dual-boot OSX / Xubuntu dapper iMac G3 500Mhz. I have a 20GB hard drive with a 9GB OSX partition, 7.5GB Xubuntu partition, and 1.5GB shared hfs+ partition.

I am having problems mounting my shared partion, cds and USB pen drives.

Shared partition:
This will work fine now, after a lot of tinkering(!), except I cannot get it to mount at startup. Every time I start up I must enter "sudo mount  /dev/hda12" to mount the partition.

/etc/fstab
```
/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda13      /               ext3    defaults,errors=remount-ro 0       1
/dev/hda14      none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda12      /mnt/share      hfsplus  user,noauto   0       0

```

CDs and USB pen drives:
These I can access only as root. If I attempt to mount a pen drive or cd through thunar normally, I get the error:

"Error: could not execute pmount."

If I open thunar as root through a terminal, I can mount these drives without any problems.

If anyone has any suggestions to try I would be very grateful.

EDIT:
By the way, once I access my shared partition from Xubuntu, OSX decides that this partition belongs to root. Each time I want to write onto this partition from OSX I have to modify the permissions through the information window in OSX. I am not sure why this is, if anyone has any thoughts on this it would be helpful as well.

---

### Post by samden on 2007-01-15
If anyone has any ideas on this I would be very grateful, my problems accessing USB pen drives are becoming extremely frustrating. Thankyou.

EDIT:
I have started a new thread on this subject in the General Help section, which is a busier section of the forum. If you have any thoughts feel free to post either in this thread or in the new one
[http://www.ubuntuforums.org/showthread.php?p=2015667](http://www.ubuntuforums.org/showthread.php?p=2015667)

---

