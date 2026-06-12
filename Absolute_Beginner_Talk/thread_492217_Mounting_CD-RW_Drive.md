---
title: "Mounting CD-RW Drive"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Atreus12 on 2007-07-04
------------
Edit: Resolved
I guess it was a hardware issue. I replaced the drive with one from a different computer and it works.
------------

I am using Ubuntu 7.04 with Gnome

When I installed, there was only a single CD-RW drive in the computer. Then that drive got moved down a slot to the 2nd slave IDE channel, and a DVD drive went into the 2nd master IDE channel. 

I can mount the DVD drive...sometimes, but I can't mount the CD-RW at all. Does this need to go in fstab? On my debian machine, the drives are /dev/hda  /dev/hdb  /dev/hdc  /dev/hdd. On This computer, it refers to the DVD drive as /dev/scd0  

I attempted to add another line to fstab, which now reads:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=3dc127a1-5f07-4379-b780-4abfb18d9cb8 /               ext3    defaults,error
s=remount-ro 0       1
# /dev/sdb2
UUID=cf094a83-a246-4679-807e-502e91489c06 /home           ext3    defaults      
  0       2
# /dev/sda5
UUID=e9a50ab5-43ed-41b3-bebc-b1dcdcbeecb2 none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto         0       0
```

Where /dev/scd1 is what I added. But it still won't mount. I tried putting a music cd in, and sound juicer doesn't even start.

---

