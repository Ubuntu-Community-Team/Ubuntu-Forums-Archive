---
title: "fstab and iTunes"
date: 2005-04-10
forum: Apple PPC Users
---

### Post by godsunderstudy on 2005-04-10
I recently discovered how to mount my Mac OSX partition with the 12 gigs of music we have on it, and would like to know two things:

1) What to put into the fstab file to automatically mount the partition. I tried the following:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /mnt/macos               hfsplus    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

But it comes up with an error (can't C+P, it's on startup), something about wrong type. Is it hfs+?

2) A good iTunes replacement. Is there any that can read the iTunes Music Libraby.xml file? Any, however, that can organise and play the iTunes Music folder will be good.

Thanks in advance.

---

### Post by Francesco on 2005-04-12
1) I am not an mount/fstab expert so I dunno why your configuration does not works... anyway my line for the hfsplus partition on fstab is this

/dev/hda3       /mnt/valis      hfsplus auto,user,rw    0       0

It works fine... when I start ubuntu linux it automount the partition with no problem.. 

2) Do not know any program that can read xml library of itunes, btw on my ibook the sound still does not work.... :roll:

---

