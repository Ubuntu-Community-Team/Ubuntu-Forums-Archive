---
title: "Permission to play dvds"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by gusoceros on 2007-03-26
Hi guys- I seem to be unable to play dvds- I get an error from totem that says:

[B]Totem could not play 'dvd:///media/cdrom1'.
Could not open location; You may not have permission to open the file.[/B]

How do I adjust the permissions for this- as a newbie, Im guessing it is in the etc/fstab- so here is what it looks like:

[list]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hda2 /media/hda2 ntfs defaults,utf8,umask=007,gid=46 0 1[/list]

Your help is appreciated

G

---

### Post by crispy_420 on 2007-03-27
My guess is one of two problems:

No DVD decoder installed (libdvdcss).

or

No optical drive permissions. (Are you primary user?)

---

### Post by octoberdan on 2007-03-27
Can you access it as root? Try a sudo ls of the drive and let me know if it's succesful or if you need clarification

---

