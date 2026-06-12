---
title: "unable to mount CD-DVD drive on both laptop and Desktop."
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by kwdy on 2006-07-08
Hello, I just installed Ubuntu 6.06 on my laptop and also just a few minutes ago on my desktop. So far I have been unable to mount my CD drives on either system. 

I have done some searching and I have no idea why it won't mount my drives.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

This is the /etc/fstab of my laptop I'm not sure if there is anything wrong here? What else should I look into to fix this issue?

---

### Post by mogelhead on 2006-07-11
How do you mount them?
Did you get any error messages?

---

### Post by orb9220 on 2006-07-11
/dev/sda /media/usb0 auto rw,user,noauto 0 0

Should there be two auto in there the first auto is what a hd cdrom ?

---

