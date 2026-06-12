---
title: "FAT32 not automatically mounting"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by aridus on 2007-04-09
Dear All

I would appreciate advice on why my FAT32 swap drive (for Windows/Ubuntu) is not mounting automatically. Here is my /etc/fstat file

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4 -- converted during upgrade to edgy
UUID=fb2fb857-3e3b-4c19-ad0c-53fe8d53f7bc / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=07D5-080C /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda2 -- converted during upgrade to edgy
UUID=32A402D6A4029D0B /media/sda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=443A-4D95 /media/sda5 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda6 -- converted during upgrade to edgy
UUID=129261fc-0d0a-4be7-8cc8-dc638114563a none swap sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

With thanks, Martin

---

### Post by lukew on 2007-04-09
> **aridus said:**
> Dear All

I would appreciate advice on why my FAT32 swap drive (for Windows/Ubuntu) is not mounting automatically. Here is my /etc/fstat file

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4 -- converted during upgrade to edgy
UUID=fb2fb857-3e3b-4c19-ad0c-53fe8d53f7bc / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=07D5-080C /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda2 -- converted during upgrade to edgy
UUID=32A402D6A4029D0B /media/sda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=443A-4D95 /media/sda5 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda6 -- converted during upgrade to edgy
UUID=129261fc-0d0a-4be7-8cc8-dc638114563a none swap sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

With thanks, Martin

I would not call it swap drive; swap is something different under linux and making it fat is total impossible.

Check dmesg when you plug it in and see if you are getting any errors!

Luke

---

