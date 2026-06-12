---
title: "mount point not found problem fixed"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by bratliff on 2007-04-08
OK, I fixed my mount point problem by putting the fstab.bak in the fstab, but when I boot there is only a yellow Ubuntu screen, no menu system.  Thoughts?

Here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=3beea3b5-a9f4-4094-a43f-d74da4fae931 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=FCE1-1A6C  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=8133-5984  /media/hda4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=4cf07afc-1516-4490-889f-2fa342a4f862 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Ratliff

---

### Post by rajeev1204 on 2007-04-09
Hi

could u be more specific?

---

### Post by bratliff on 2007-04-09
I had two problems. The "mount point does not exist" error scrolled by as I booted. And there was no menu after booting, just a background screen. I replaced the fstab with it's backup and now I do not have the "mount point does not exist" error. (I had edited the fstab) However I still do not have a menu, just the background screen and the hard drive lights up about once a second. 

I do not know how to repair the lost menus. The problems occured when I installed the virus scanner fprot.  If I can't repair the missing menus I will lose all my configurations, etc. but will reinstall with the next release. 

BEWARE FPROT.

Ratliff

---

