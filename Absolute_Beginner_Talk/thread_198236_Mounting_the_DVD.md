---
title: "Mounting the DVD??"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by elder70 on 2006-06-16
Following is my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

I would like the DVD to mount as well. It will  not automount. When I put a disc in the DVD drive, it blinks away happily but then goes silent. When I tried to play a movie on DVD it came back with it cold not find /dev/hdc. I would appreciate any help. Thank you.

---

### Post by u.b.u.n.t.u on 2006-06-16
```
/dev/hdd     /media/cdrom0    udf,iso9660 user,noauto   0  0
```

This is a Liteon DVD RW. 


```
/dev/hdd     /media/cdrom0    udf,iso9660 user,noauto   0  0
```

This is a SONY CDROM.

In both cases, ubuntu has set this up and it works well.

Your setting seems to be fine. Perhaps there is a lose ribbon connection?

---

