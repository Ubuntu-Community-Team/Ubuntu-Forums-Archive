---
title: "I/O error at start up"
date: 2004-12-28
forum: Apple PPC Users
---

### Post by xico on 2004-12-28
Hello,
I get about 30 error messages during the booting of Ubuntu:

I/O error, dev sda, sector xxxxxxx
Buffer I/O error on device sda
SCSIO: Error on channel0, id 6

I guess it's bad block in the tree. 
Here's my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda2 / ext3 defaults,errors=remount-ro 0 1
/dev/sda3 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 ro,user,noauto 0 0

How do I run fsck? 
Not on a mounted partition!
A running partition can't be unmounted!
Then how? Is there a kernel argument in BootX?


 Thanks for helping

Francois

__________________
Beige MT G3 266/640/2x4.5 scsi 
Ati Rage II 64 on motherboard

---

### Post by xico on 2004-12-28
Here's my /etc/fstab:


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>      <options>       <dump>      <pass>
proc                          /proc               proc       defaults                   0                0
/dev/sda2                 /                      ext3  defaults,errors=remount-ro 0         1
/dev/sda3              none                  swap            sw                     0                0
/dev/hda          /media/cdrom0   udf,iso9660       ro,user,noauto   0                0

---

