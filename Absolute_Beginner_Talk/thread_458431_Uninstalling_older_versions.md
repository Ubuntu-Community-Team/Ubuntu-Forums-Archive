---
title: "Uninstalling older versions"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-05-29
I've done a clean install of Feisty, and I'd like to remove my old Dapper which is on another drive. Can I just delete the partitions, and resize the (Windows) partitions on that drive, or do I have to uninstall Dapper first?

Can't find anything much on uninstalling - not surprising, as I don't imagine that option will be used much! :)

---

### Post by bodhi.zazen on 2007-05-29
Depends ...

When you installed feisty, where did you install grub ? I assume you re-installed grub to the MBR when you installed feisty. In that case you can do as you say. You might need to update fstab (/etc/fstab) on feisty as your partitions changed.

If you did not install grub when you installed fiesty, you will need to reconfigure or re-install grub after you remove the old Ubuntu install. Otherwise, as you say, delete away.

---

### Post by freesitebuilder on 2007-05-29
I let the installer install the grub, I think? Here's my fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=e27c3bdd-f406-4b36-bce0-43194b8f60d6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb3
UUID=fc54f5d1-d567-4ef2-ab68-9bf356d1facd /home           ext3    defaults        0       2
# /dev/hda3
UUID=ACA6-45C0  /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=CCE9-0485  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=7e37592d-06d7-4dfd-bc27-2d507385d7df /media/hda6     ext3    defaults        0       2
# /dev/hda8
UUID=d604cebf-6454-4408-8e62-36eb79fe84bb /media/hda8     ext3    defaults        0       2
# /dev/hda7
UUID=1906c7b3-5404-4007-b673-cb047aa688db none            swap    sw              0       0
# /dev/hdb2
UUID=9bc9d7f8-c39b-4915-9802-fa3665f71fe5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by bodhi.zazen on 2007-05-29
You will need to comment out / delete the partitions in fstab you are planning to delete.

If you need help with fstab : [https://nothlit.servehttp.com/fluxbuntu/documentation/](https://nothlit.servehttp.com/fluxbuntu/documentation/)

If you have questions, FEEL FREE TO ASK

---

