---
title: "mounting 2nd ext3 partition in fstab."
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by BurgesS on 2007-03-09
I would like to mount an ext3 partition from my 2nd hard drive and have full r/w exec privelages as a user.  Here is what I have:


Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7476    60050938+   7  HPFS/NTFS
/dev/hda2            7477       14639    57536797+  83  Linux
/dev/hda3           14640       14946     2465977+   5  Extended
/dev/hda5           14640       14946     2465946   82  Linux swap / Solaris

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       26108   209712478+   7  HPFS/NTFS
/dev/hdb2           26109       38913   102856162+  83  Linux



This is what I have come up with after reading a bit :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=fcf4517d-d3b5-4b75-ab1e-2b35d1e8691b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=112a676d-4af2-458b-971c-0227409c7bc5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1   /media/hda1   ntfs   nls=utf8,umask=0222   0   0
/dev/hdb1   /media/hdb1   ntfs	 nls=utf8,umask=0222   0   0
/dev/hdb2   /media/hdb2   ext3   auto,rw,exec,user,async   0   0

Am I on the right track here?  Any suggestions?

---

### Post by seshomaru samma on 2007-03-09
Read [this ]("http://www.psychocats.net/ubuntu/mountlinux")

---

