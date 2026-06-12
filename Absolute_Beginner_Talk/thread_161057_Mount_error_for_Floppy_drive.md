---
title: "Mount error for Floppy drive"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by csk on 2006-04-16
hi all
everytime i try to run my floppy drive from "computer" i get this error
"Warning: device /dev/fd0 is already handled by /etc/fstab, supplied label is ignored
mount: I could not determine the filesystem type, and none was specified
Error: could not execute pmount"

i tried using "Floppy Formatter" using both filesystems FAT & Linux Native (ext 2) but got following errors - 
"The filesystem creation utility (/sbin/mkdosfs) reported the following errors:

mkdosfs: failed whilst writing FAT
 (35)" 

and for linux native

"Problem reading cylinder 0, expected 18432, read 8192" 

could someone please tell me how to fix this. 

thanks 
csk

---

### Post by simonn on 2006-04-16
Show us your fstab! :)

cat /etc/fstab and paste here.

---

### Post by Mustard on 2006-04-16
Looks like the same errors I was getting the other day when putting some old pre-formatted floppies in my drive.  I have no idea what was going on.  It seemed to depend on whether they were empty or not.  The system would be hunting around for ages one some of them, and while I was browsing through my logs, I noticed a ton of errors relating to the attempt to access them.

I recall making a few attempts to mount them manually, specifying the filesystem type in one attempt and using 'auto' for the -t option on other attempts.  Oftentimes I could see the cpu load going on for ages with no result.

---

### Post by csk on 2006-04-16
my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/Windows  ntfs    nls=utf8,umask=0222 0       0

---

### Post by Mustard on 2006-04-17
[QUOTE=csk]my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/Windows  ntfs    nls=utf8,umask=0222 0       0[/QUOTE]

I'm thinking the 'noauto' option might mean no automount?

---

