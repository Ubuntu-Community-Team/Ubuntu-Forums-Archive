---
title: "Can't Access Hard Drive Partition"
date: 2018-03-20
forum: Apple Hardware Users
---

### Post by dev.anthony on 2018-03-20
Hello!

Since I switched to Linux, I can't access files (such as images) on the hard drive partition with my original Mac installation.  The file manager recognizes that partition, but when I try to click into it I get the following error message:

[B]Unable to access "Macintosh HD"


[/B]> Error mounting /dev/sda2 at /media/dev/Macintosh HD: Command-line `mount -t "hfsplus" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda2" "/media/dev/Macintosh HD"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

I'm not sure what I'm looking at when I look at the system log there, so that doesn't get me any closer to figuring it out.  Any guidance you can offer will be greatly appreciated!

Thanks!
-Dev

---

### Post by kevin160 on 2018-03-21
It's been a while since I tried this.  I seem to remember there being an issue with journaling, and having to turn off journaling in order to get a partition to mount properly.  Or maybe that was just for write access.  

A quick google suggests that running a disk repair under macOS might help.  

There are two packages that give you hfs access from Linux.  hfsprogs seems to be the built-in solution in Ubuntu and there is also an hfsfuse driver you could try.  

In any case, mounting hfs partitions with valuable data on them under Linux makes me nervous.  On my Mac mini, I have a separate "data" partition which I use to store data that I need to access from both Linux and macOS.   That partition is currently in ZFS format, but I've used exfat and plain old FAT32 reliably as well.

---

