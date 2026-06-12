---
title: "Write permissions to USB HD"
date: 2005-07-21
forum: Absolute Beginner Talk
---

### Post by senshisteph on 2005-07-21
Idiotic question time I'm afraid... I have an external USB hard disk. I have followed the instructions in the wiki on formatting and mounting it - it is formatted as ext3 and appears to be mounting OK - I can see it in file manager, even the 'lost and found' folder that has appeared inside it... but I can't write to it. I just get an error message saying I don't have the right permissions.

I searched the wiki and the forums but can't find out how to give myself permission to write into my disk! I noticed most people with this kind of question posted their fstab file, so here's mine:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0


The external device is sda  ;-)

---

### Post by [pl]ice on 2005-07-22
have you sorted out? i had similar problems but with normal fat32, try adding to the fstab's hd line your  exec,rw,user,uid=??? my helped when i put the uid.

---

### Post by ubuntp on 2005-07-23
/dev/sda /media/usb0 auto rw,user,noauto,umask=0 0 0

should work.

---

