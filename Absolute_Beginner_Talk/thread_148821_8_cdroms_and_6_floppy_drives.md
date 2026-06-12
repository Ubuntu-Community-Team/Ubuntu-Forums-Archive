---
title: "8 cdroms and 6 floppy drives?"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by bfreas on 2006-03-22
Hi all,

Just finished a new install of Dapper. Opened fstab to set up automounting my NTFS partitions and saw all of these entries. I've got 2 DVD drives and 1 floppy....can I delete cdrom2, 3, 4, 5, 6, 7 and 8 and floppy1, 2, 3, 4, 5 and 6? I've also got a Sandisk memory card reader. Is this what some of the cdrom entries are?

Thanks!

[edit] Here's the contents:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom2   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom3   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom4   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom5   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom6   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom7   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom8   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy1  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy2  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy3  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy4  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy5  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy6  auto    rw,user,noauto  0       0
/dev/hda5       /media/windows1 ntfs    nls=utf8,umask=0222 0       0
/dev/hdb1       /media/windows2 ntfs    nls=utf8,umask=0222 0       0

---

### Post by ssam on 2006-03-22
its a know bug [https://launchpad.net/distros/ubuntu/+source/udev/+bug/27926](https://launchpad.net/distros/ubuntu/+source/udev/+bug/27926) and marked as fixed.

did you install from flight 5 or a recent daily?

also [http://ubuntuforums.org/forumdisplay.php?f=111](http://ubuntuforums.org/forumdisplay.php?f=111) is probably a better forum for you to post in with dapper questions, as its not a final release yet

update:
it seems that the bug was fixed on the 15th of march, so flight 5 will still have the bug, but dailys after the 16th should not. if you think the bug still exists on cd images from after the 16th repoen the bug report.

---

### Post by bfreas on 2006-03-23
Thanks ssam.

Sorry for posting in the wrong forum. I didn't want to post in the developer forum with a newb question so thought that here would be more appropriate.

I installed from a flight 5 image that I downloaded two days ago (3-21). I'm having problems with System Monitor also as it doesn't show graphs (resources tab), only color selection boxes, even though the applet works correctly. I guess a newb should know better than to install a developer release and not expect problems....

Anyway, I'm assuming that it is safe to delete the extra entries in the fstab?

Thanks

---

