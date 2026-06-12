---
title: "Problems with using my second partition"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by Momiji on 2006-01-21
When i installed Linux i made two partitions on my computer. One smaller for the actual OS (plus that extra swap thing) and also a bigger one for files and other stuff like that. 

The first partition seems to be working fine but i can't figure out how to use the other one. The small one is mounted as root and the second one is mounted as /media/hda1.

The problem is that i cannot create new folders or anything in /media/hda1. there is just some folder there named lost+found. How can i make it more like the home folder?

/jonas

---

### Post by Susana on 2006-01-21
Hi,
can you paste the contents of /etc/fstab here?

---

### Post by Momiji on 2006-01-21
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Seems to be what's in there :O

---

### Post by Susana on 2006-01-21
try: sudo chown -R your_user:your_user /media/hda1

make a copy of /etc/fstab: sudo cp /etc/fstab /etc/fstab.save
change the line of fstab: /dev/hda1 /media/hda1 ext3 defaults 0 2
to: /dev/hda1 /media/hda1 ext3  auto,user,owner,rw 0 2
then: sudo mount -a

---

### Post by Momiji on 2006-01-21
Hmm i can't seem to save fstab. I don't have the authority to do that :(
Do i need a special command to be able to save systemfiles, as it is not possibly through the menu?

---

### Post by Momiji on 2006-01-21
Thanks! I managed to get it to work!

Thanks again for the help, I love this community :) Everyone is so helpful!

---

