---
title: "Problems Mounting Windows(bleH)"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by Jaygo333 on 2005-12-29
I seem not to be able to access the files in the windows part of my partition.
I installed Ubuntu about a week ago and there was only one icon on my desktop. 
It was called hda1. I tried clicking on it and get
 "You do not have the permissions necessary to view the contents of "hda1"."
Every time I click on it, I get the same error. Any help to actually see and read the drive. There are files in windows that I want to see in ubuntu.

Also, How do I remove the "hda1" icon from showing on my desktop. I don't want it there if I can't access it.

:arrow:h34r: Jaygo333 :arrow:h34r:

---

### Post by Gimbo on 2005-12-29
[http://ubuntuforums.org/showthread.php?t=109954]("http://ubuntuforums.org/showthread.php?t=109954")

Read that thread and have a look at the tutorials that are linked from it, that should stop the error message and let you READ the files on your windows partition (writing to NTFS partitions is not advisable from Linux as it could cause serious corruption).

---

### Post by Jaygo333 on 2005-12-29
[QUOTE=Gimbo][http://ubuntuforums.org/showthread.php?t=109954]("http://ubuntuforums.org/showthread.php?t=109954")

Read that thread and have a look at the tutorials that are linked from it, that should stop the error message and let you READ the files on your windows partition (writing to NTFS partitions is not advisable from Linux as it could cause serious corruption).[/QUOTE]

I just tried the above forum but still get the same problem as before: 
"You do not have the permissions necessary to view the contents of "hda1"."
My etc table is exactly the same as the one posted in the forum except for the second last line from the bottom which does not appear in the one in the forum.Here's my table:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/windows  ntfs    umask=0222 	0	0      
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Any Help.
Also, do you know how to make the disk icon not appear on the desktop.

Thanks A Lot.

:arrow:h34r: Jaygo333 :arrow:h34r:

---

### Post by jimrz on 2005-12-30
Go [**[COLOR="Sienna"]here[/COLOR]**]("http://ubuntuguide.org/#automountntfs") it gives complete intructions. Be sure to do the unmount step on your win partition before any of the rest.

---

