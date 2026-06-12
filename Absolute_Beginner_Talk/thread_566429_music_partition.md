---
title: "music partition"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by arkara on 2007-10-03
ok i have a dual boot system with windows xp and ubuntu linux 7.04
and i have patitioned my hd like this

1)----->windows xp 100gb
2)----->a seperate fat 32 patition 32gb (mostly for music)
3)----->20 gb ubuntu linux partition

i want my fat 32 patition to be automaticaly mounted after my login with root rights?
what should i write to my fstab??
my fstab looks like this:  ...   

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=6f5f2320-6c5b-4a72-8543-8db276fff924 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f7924eac-0181-4f52-bbf1-e25ec100cd45 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by nest on 2007-10-03
you can find your answer [here]("https://help.ubuntu.com/community/AutomaticallyMountPartitions").

---

