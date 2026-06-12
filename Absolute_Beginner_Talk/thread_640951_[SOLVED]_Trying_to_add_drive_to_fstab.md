---
title: "[SOLVED] Trying to add drive to fstab"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by lakelovers on 2007-12-14
I've been trying to mount a second internal drive following all the post I've read. on editing fstab. Not understanding the the protocol in stab, I've tried following the various examples in posts but, so far, have been unsuccessful in mounting the drive. Here the response to fdisk -l.  


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9542    76646083+  83  Linux
/dev/sda2            9543        9729     1502077+   5  Extended
/dev/sda5            9543        9729     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         784     6297448+  83  Linux

And here's my latest edit of stab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=76b1e510-344e-4b15-aa52-1d73e8550169 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d420cfca-37c1-4c6d-8bd8-f56cd0035148 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1       /media/sdb1     ext3    defaults       0        2

I'll appreciate any guidance you can give me.
Jerry

---

### Post by diatribe on 2007-12-14
and?

---

### Post by dwblas on 2007-12-14
It looks like you have sda1, sda2, sda5, and sdb1.  Are you wanting to add one of these or all of them?  Post the contents of /etc/fstab and what you want to mount.  Note that you can mount them manually with mount /dev/sdx /mount_point.   /mount_point is usually /media/something but can be any directory.  Keying 
man mount
into a terminal will give more details than you want to know.  To mount automatically you will have to alter /etc/fstab/

---

### Post by lakelovers on 2007-12-15
I want to mount sdb1 automatically through stab. I posted /ect/stab in the first post, at the bottom of the page. I've added: **dev/sdb1 /media/sdb1 ext3 defaults 0 2**. However, that doesn't work so I don't have the correct line.

---

### Post by dwblas on 2007-12-15
> I've added: dev/sdb1 /media/sdb1 ext3 defaults 0 2. However, that doesn't work so I don't have the correct line.You want to add a slash at the beginning
/dev/sdb1  /media/sdb1  ext3  defaults  0  2
Make sure that /media/sdb1 exists as well-it will not mount if /media/sdb1 does not exist (mkdir sdb1 will create it, if you are in the /media directory).  I don't have SATA drives, but that should work.  If not, post back.  BTW, man fstab will tell you what all of the paramenters mean if you want to know.

Edit: I'm assuming that this is a typo and you are editing /etc/fstab
I posted /ect/stab

---

### Post by mackrackit on 2007-12-15
This worked for me.
[http://ubuntuforums.org/showthread.php?t=635561](http://ubuntuforums.org/showthread.php?t=635561)

---

