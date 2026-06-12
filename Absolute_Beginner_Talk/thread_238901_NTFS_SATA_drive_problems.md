---
title: "NTFS SATA drive problems"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by jaybmx on 2006-08-18
I just installed Ubuntu on another machine... lub it!
This machine has 3 drives, 1 system(Unbuntu), 2 media drives (NTFS from old win system)
The Ubuntu install went fine and everyting works great except my 2 NTFS media drives...
In Nautilus i can see the 2 drives and they retained thier windows names, but when i double click to browse the drive i get an error saying "You do not have the permissions necessary to view the contents of "disks-conf-sda1""

Can someone point me in the right direction? I would like to have full access to these drives...

Thanks
jaybmx

---

### Post by ciscosurfer on 2006-08-18
Please post your /etc/fstab```
cat /etc/fstab
```

---

### Post by jaybmx on 2006-08-18
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by givré on 2006-08-18
You will have to add your NTFS partition to this file so it'll be mount at boot time.
Look at one of this how to :
[https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html](https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html)
[http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php)

---

