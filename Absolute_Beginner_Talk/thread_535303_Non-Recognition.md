---
title: "Non-Recognition"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by ashvala on 2007-08-26
I use Debian etch & there is a certain problem that i face,

I try to mount /cdrom & then it says 
 bash:/dev/hdd doesn't exist

And in /etc/fstab:
 /etc/fstab: static file system information.                                   
#                                                                               
# <file system> <mount point>   <type>  <options>               <dump>  <pass>  
/dev/hde3       /               ext3    errors=remount-ro       0       1       
/dev/hde2       none            swap    sw                      0       0       
proc            /proc           proc    defaults                0       0       
/dev/fd0        /floppy         auto    user,noauto,exec        0       0       
/dev/hdd        /cdrom          iso9660 ro,user,noauto,exec     0       0       
/dev/hdc        /cdwriter       iso9660 ro,user,noauto,exec     0       0       
/dev/hde5       /usr            ext3    defaults                0       2       
/dev/hde6       /home           ext3    defaults                0       2       
/dev/hde7       /var            ext3    defaults                0       2       
/dev/hde8       /work           ext3    defaults                0       2       
# /dev/hdb8     /oldroot        ext3    defaults                0       2       
# /dev/hdb6     /oldhome        ext3    defaults                0       2       
/dev/sdb1       /usb            auto    user,noauto,exec        0       0       
/dev/sdb2       /ipod           vfat    user,noauto,exec        0       0       
/dev/hde1       /win            vfat    user,noauto,exec        0       0       
/dev/sda1       /new1           auto    defaults                0       0       
/dev/sda2       /new2           ext3    defaults                0       0       
/dev/sda3       /new3           ext3    defaults                0       0       


Can anyone help me?

---

### Post by PriceChild on 2007-08-26
This is an Ubuntu Support forum.

---

