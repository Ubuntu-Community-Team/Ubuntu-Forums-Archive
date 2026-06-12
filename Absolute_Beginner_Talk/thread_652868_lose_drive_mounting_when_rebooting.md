---
title: "lose drive mounting when rebooting"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by davidexe on 2007-12-29
I have the Ubuntu server set up with two sata drives installed on a sata controller card. When I reboot the machine the drives lose their mounting and come up mounted in the tmp folder.  How can I lock the drives so they maintain their mounting when rebooting?

Thanks.

---

### Post by cmnorton on 2007-12-29
You've got to make sure they're listed in /etc/fstab, but be sure you first make a backup copy of /etc/fstab, and study what's already there before editing the file.  This is an /etc/fstab from a desktop that has a default volume and the sata I added later: Notice the sata is sdb1.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=ec94d7ad-6480-443f-bbe7-44c6fa1e2e96 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=5b16941c-1903-426b-9375-afc5e60ccadc none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1 /media/sdb1 ext3 defaults,errors=remount-ro 0 1

---

### Post by davidexe on 2007-12-29
that worked with one problem.  Well, maybe not a problem. The message came up that the drive had been mounted 60 times and not checked, forced check.  And that took awhile. But now they mount when rebotting.  I guess I "assumed" that when I mounted them the info would be put in and it would be mounted on reboot.  So, Again, learned something.

THANKS..

---

