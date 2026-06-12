---
title: "[SOLVED] what happened to my cdrom dir"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by tropdoug on 2008-03-30
What happened to my CDRom drive in /media/

This morning I had an icon indicating a folder labeled CDROM. now I have an apparently broken link to my cdrom, how do I re link it 

when I put a cd in the drive, it brings up soundjuicer and can play the disc. Amarok also, so obviously its just a link.

Fraid I don't know how to do these simple things yet.

---

### Post by c-ron on 2008-03-30
from the terminal:
[HTML]mount /media/cdrom[/HTML]

---

### Post by tropdoug on 2008-03-31
It looks like a utility called diskmounter might have stuffed things up, when I went to use the command as written, I was told that the drive did not exist in my etc/fstab file, so I opened that and this is what I find
[I][COLOR=Blue]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=2df7cb62-b191-40a2-b367-966345a1e8b9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=5f56a80b-dd7c-4fa0-af4d-79fa75d3128e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#Added by diskmounter utility
/dev/sda1 /media/sda1 ntfs ro,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
#Added by diskmounter utility
/dev/sdc1 /media/sdc1 vfat rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0

[/COLOR][/I][COLOR=Blue][COLOR=Black]I also tried using mount media/cdrom0 

and got the same reply.. Looking at the above I can see the cdrom0 line but for some reason it won't find it. I used the diskmounter simply to make it quicker to mount my external vfat drive sdc, rather than having to do it manually every day. perhaps I should remove the diskmounter lines?

[/COLOR][/COLOR]

---

