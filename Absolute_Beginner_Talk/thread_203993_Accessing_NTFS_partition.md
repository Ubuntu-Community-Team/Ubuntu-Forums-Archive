---
title: "Accessing NTFS partition"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by En Sabah Nur on 2006-06-26
I'm trying to access some files on my NTFS partition (listen to music, videos, etc.) but when I go to the disk manager under 'system' and try to enable the partition it won't let me. I don't know exactly how to do it and don't want to mess anything up. 

Here is a copy of my fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Should I just add /dev/hda1 under 'proc,' /c under '/proc'?

---

### Post by glinsvad on 2006-06-26
First create the directory /media/winxp (or an equivalent name if you don't like winxp).

Then, add the line (between the two lines proc.. and /dev/hda2 should be fine):
```

/dev/hda1       /media/winxp    ntfs    nls=utf8,umask=0222      0       0

```

Of course you should make sure that the NTFS partition is actually /dev/hda1 in the disk manager...

EDIT: Also check out the [Ubuntu Guide]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only") on this subject

---

### Post by aysiu on 2006-06-26
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Apple 101 on 2006-06-27
The NTFS partitions should have been automatically mounted, shouldn't they?

---

### Post by shoot2kill on 2006-06-27
i had to go through the same procedure to access my windoze partition....

Sorry, not partition but seperate HDD.. dont think theres any difference...

---

### Post by harishg on 2006-06-27
Check this [http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

---

