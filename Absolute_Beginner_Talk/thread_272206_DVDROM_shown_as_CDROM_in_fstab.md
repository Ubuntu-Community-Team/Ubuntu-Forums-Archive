---
title: "DVDROM shown as CDROM in fstab"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by space_boy on 2006-10-05
Hi! Just loaded Ubuntu Dapper, and I really like it. I am having one configuration problem with my DVDROM drive. I have a DVDROM (master) and a CDRW (slave) drives installed. The DVDROM is listed as a cdrom0. Both will auto detect and mount ant CDs inserted, but the DVDROM will not detect or mount and DVD that I insert. I noticed that my fstab on list it as a cdrom. WHat changes do I need to make to mount DVDs? 

My fstab is as follows:
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0

Thanks in advance!

---

### Post by d_morgan on 2008-03-22
I have the same problem but I'm using version 7.10 (Gutsy Gibbon).  I may have contributed to the problem by installing with 2 DVDROM drives in the system and latter removing the 2nd drive.  Now when I play a DVD totem treats it as audio only and plays the sound track and shows a visualization.  My fstab file is below.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9251a252-04c3-426f-9f6d-7b020993995c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID=32c22f26-e1bc-4d8e-a1ab-e2422ffecb44 /var/lib        xfs     defaults        0       2
# /dev/sda2
UUID=b1d04219-94b5-45e7-a864-54d4f589a085 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

Any help would be appreciated.

---

### Post by logos34 on 2008-03-22
> **d_morgan said:**
> I have the same problem but I'm using version 7.10 (Gutsy Gibbon).  I may have contributed to the problem by installing with 2 DVDROM drives in the system and latter removing the 2nd drive.  Now when I play a DVD totem treats it as audio only and plays the sound track and shows a visualization.  My fstab file is below.
... 

UUID=b1d04219-94b5-45e7-a864-54d4f589a085 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

You should have symlinks in /dev something like this:

$ ls -l /dev | grep dvd
lrwxrwxrwx 1 root   root           3 2008-03-21 19:29 dvd -> **scd0**
lrwxrwxrwx 1 root   root           3 2008-03-21 19:29 dvdrw -> **scd0**

Or maybe it's a codec issue.  Use the totem-xine backend if you're not already:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

