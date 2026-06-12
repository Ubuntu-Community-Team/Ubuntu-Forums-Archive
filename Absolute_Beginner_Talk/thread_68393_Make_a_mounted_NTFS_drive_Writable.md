---
title: "Make a mounted NTFS drive Writable"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by clueo8 on 2005-09-22
I have successfully mounted my NTFS drive with windows on it, and also a storage partition in my fstab file.  heres what I got:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext2    defaults        1       1
/dev/hda1       /d              ntfs    auto,users,exec,rw,umask=0222 0 0
/dev/hda5       /c              ntfs    auto,users,exec,rw,umask=0222 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I changed was was just "r" to "rw" thinking it will be read/write access... Is this even possible for linux to write to these partitions?

Also, I would like to share the NTFS with other Windows computers, is this possible?

---

### Post by 23meg on 2005-09-22
as far as i know, NTFS write support is still experimental in linux, which means it's not enabled by default (you need to install additional software; the name escapes me) and that it shouldn't be used for sensitive data.

sharing must be possible as long as it's read only. refer to the unofficial ubuntu guide for instructions on how to set up samba for file sharing with windows computers.

---

### Post by drogoh on 2005-09-23
No, you just have to compile your own kernel with it enabled.  It's far too buggy to be used on anything but data that is backed up in triplicate.  In short, don't use it.  Shuffle your data around and format your NTFS stuff to ext3 (if you don't think you'll have it mounted outside of Linux) for best results and then set Samba up to share with the Windows machines.

---

