---
title: "Gnome-backerred CD-RW"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by evieP on 2007-07-20
HELP, please!

I tried to add a short video to a CD-RW disk using GnomeBaker and quit before completion (mea culpa:().

I can no longer access the other 20 videos on the disk either in Windows or Ubuntu, and I DON'T want to have to reFormat.(fstab & detail)> 
evie@athlon:/etc$ cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=5c0259cd-fc43-4107-be94-117a800b986b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=401be558-7287-4b56-95fa-24ab46486553 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
evie@athlon:/etc$
                   Unable to mount the volume 'GnomeBaker data disk' 
                Details
                    mount: block device /dev/hdc is write-
                    protected,mounting read-only
                    mount:Not a directory
I'm good with GUI's, poor with bash terminal, can anyone point me in the right direction, please??

---

### Post by Atomic Dog on 2007-07-20
The only program I can think of that may be able to help you is isobuster.  It has rescued a few hosed discs for me.

---

### Post by evieP on 2007-07-20
Thanks!, Atomic Dog.

Isobuster is an Exe file.  It does actually recognise  the 'GnomeBaker disk' but generates GiB's of files which don't reconstruct (not for me, anyways). I'm pretty sure that the files are there, intact, on the disk, and that it's an ISO mount problem basically which I haven't yet solved.

Thanks again!....more suggestions, anyone, PLEASE!

---

