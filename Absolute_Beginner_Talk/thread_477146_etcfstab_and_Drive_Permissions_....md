---
title: "/etc/fstab and Drive Permissions ..."
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by dpneal on 2007-06-18
Ahh, permissions -- they're driving me nuts.

I'm able to mount my new internal hard drive.  The problem is that (a) I don't have write permission to it; and (b) I'm not sure if my /etc/fstab options are correct.

Here's my /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bef42bcd-1a4f-4ba7-a734-cc8f11b8615b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=796119f3-86b6-4126-8f90-4514bae02810 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

/dev/sdb1	/media/invault	ext3	defaults	0	2

```

Here's my fdisk -l:

```
Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       47505   381583881   83  Linux
/dev/sda2           47506       48641     9124920    5  Extended
/dev/sda5           47506       48641     9124888+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19452   156248158+  83  Linux

```

What is the best practice if I want to create a directory, readable by my login only, in which rsync drops a mirror of my home directory nightly?  Chown the entire hard drive to me?  Chown a single folder to me (that I can't create)?  Do I need to try to figure out the UUID thing for the drive instead of merely mounting /dev/sdb1?

Thanks for reading!

-- Dan

---

### Post by bodhi.zazen on 2007-06-18
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

How you set up your back up from there is up to you, but you have the right general idea.

Permissions for the backup directory 700 are most secure.

---

### Post by dpneal on 2007-06-18
Thank you!

---

