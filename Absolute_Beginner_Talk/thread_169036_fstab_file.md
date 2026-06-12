---
title: "fstab file"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by BrandNuUbantu on 2006-05-01
Hi there,
Could someone share their ideas about this fstab file:
proc            /proc                       proc      defaults                   0         0
/dev/hd3      /                ext3       defaults, errors=remount-r      0  1
/dev/hda1    /media/hda1  ntfs       defaults                  0         0
/dev/hda2    /media/hda2  ntfs       defaults                  0         0
/dev/hdc     /media/cdrom0   udf, iso9660  user, noauto  0          0

I was trying to install oraclexe. To do that i needed a swapfile ( as ididnt like to do swap partition). I have created swapfiles and turned the same. But to make changes in fstab file, i tried as sudo but the file says "static file". I am thinking probably the ext3 has errors, so i wouldnt be able to configure fstab file.
If so, what are available options for me?


TIA
BNU

---

### Post by htinn on 2006-05-01
Here's what my fstab looks like:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

Of course, I use a whole partition for swap. I'm not sure how to do a swap file in Linux.

---

### Post by BrandNuUbantu on 2006-05-01
To create a swapfile:
step 1. 
#dd  if=/dev/zero   of=/swapfile bs=1024 count=614400
step 2.
#mkswap /swapfile
step 3.
#swapon /swapfile
step 4.
editing fstab file to turn the swapfile while booting
/swapfile      swap      swap     defaults    0   0

HTH
BNU

---

