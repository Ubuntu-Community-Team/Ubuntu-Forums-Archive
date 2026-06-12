---
title: "access a new partition with a new OS"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-12-30
Hi everybody

I've installed a new distro - Slackware - on my PC; just I was wondering how can I access to it when I boot from Dapper. :confused: 

Thanks for any hint

---

### Post by rlozano on 2006-12-30
you have to inlcude that in your /etc/fstab so that you'll be able to access it. see [www.psychocats.net/ubuntu](www.psychocats.net/ubuntu). there's a guide in working with the fstab.

hope this helps...

---

### Post by helphope on 2006-12-30
Thanks for your speedy reply. 
I've checked out the guide you suggested

> **rlozano said:**
> you have to inlcude that in your /etc/fstab so that you'll be able to access it. see [www.psychocats.net/ubuntu](www.psychocats.net/ubuntu). there's a guide in working with the fstab.

hope this helps...

but now I'm stuck. This is my fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdd        /media/floppy1  auto    rw,user,noauto  0       0



I've got one hard disk with hda1 ubuntu; hda2=hda5 (swap); whereas hda3 cannot be seen from fstab.
Moreover I see errors in hda1

Any more hint? thanks a bunch

---

