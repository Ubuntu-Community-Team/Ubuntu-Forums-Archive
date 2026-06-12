---
title: "Permanently mounting primary slave drives"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by iamshawnrice on 2008-04-21
Hey.

My primary slave drive does not automatically mount upon system start up.

Can I change this?

---

### Post by TeoBigusGeekus on 2008-04-21
Do a search about the /etc/fstab file.

---

### Post by iamshawnrice on 2008-04-21
Searching for the etc/fstab file produced this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8cb1e2d9-43fb-422b-bbfb-b91250936222 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=97d7b09d-2c2e-4ed9-b692-23ee56718101 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

And then?

---

### Post by logos34 on 2008-04-21
post the output of 

**sudo fdisk -l**

---

### Post by bodhi.zazen on 2008-04-21
LOL

Sorry the first response was a little terse.

You need to add a line in fstab for your partitions you want mounted. "normally" this configured when you install Ubuntu, but if you need to change ...

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by TeoBigusGeekus on 2008-04-22
I' m sorry for my post - I was in a hurry...
Besides, I'm Greek (lazy :))...

---

### Post by bodhi.zazen on 2008-04-22
> **TeoBigusGeekus said:**
> I' m sorry for my post - I was in a hurry...
Besides, I'm Greek (lazy :))...

LOL, no problem, I have been guilty of the same. Thank you for helping on these forums.

---

### Post by iamshawnrice on 2008-04-28
thanks guys..I am updating to 8.04 now...i'll see where I am then.

---

### Post by bodhi.zazen on 2008-04-28
The easiest way then is to assign a mount point (manually) at the time of installation.

---

