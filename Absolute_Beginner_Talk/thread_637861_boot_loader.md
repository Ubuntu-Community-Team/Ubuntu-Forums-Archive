---
title: "boot loader"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by alooma on 2007-12-11
i can t use grub bacause of  my harddisk's problem therefore i installed lilo with debian and i was very happy with debian and windows. 
Yesterday i installed ubuntu(without grub) to secondary partiton.
i edited /etc/lilo.conf on debian and tried lilo command and this:

Fatal: First sector of /dev/hda7 doesn't have a valid boot signature

so how can i add ubuntu to bootloader?

lilo.conf is like this:

boot=/dev/hda
root=/dev/hda5
map=/boot/map

delay=20

default=Windows

image=/vmlinuz
    label=Linux
    read-only
#    restricted
#    alias=1

    initrd=/initrd.img
image=/vmlinuz.old
    label=LinuxOLD
    read-only
    optional
#    restricted
#    alias=2

    initrd=/initrd.img.old
other=/dev/hda7
        label=Ubuntu
#    restricted 
#    alias=3
other=/dev/hda1
    label=Windows
#    restricted
#    alias=2

---

### Post by alooma on 2007-12-12
?

---

### Post by zabien1970 on 2007-12-12
What harddisk problem?  As far as I know ubuntu needs grub to load (although I could be wrong), if you can install grub there are some good links on the thread Laptop doesn't start after using Gparted -help!
[http://ubuntuforums.org/showthread.php?t=637876](http://ubuntuforums.org/showthread.php?t=637876)

---

