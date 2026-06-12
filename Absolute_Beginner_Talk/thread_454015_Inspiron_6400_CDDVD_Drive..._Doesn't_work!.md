---
title: "Inspiron 6400 CD/DVD Drive... Doesn't work!"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by joshb86 on 2007-05-25
Hi. I installed ubuntu for a family member on a Dell Inspiron 6400. It installed from the CD fine and  now that it's installed it will not see and cd's / dvd's. The drive starts to spin up for about 10 seconds but never get anything. Here are the results of fstab...


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=46b9b13b-2a06-497e-9bfb-31b3161b472e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=96ff3bf9-6361-46e7-9044-4461ea667049 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0



I tried editing the scd0 to various names but no luck. Any help will be greatly appreciated. Thanks!!

---

### Post by n8bounds on 2007-05-25
do this:

boot ubuntu, log in, open a terminal and say

tail -n 35 /var/log/messages

save that somewhere

insert the cd, wait a few minutes, then in a terminal say the same thing, post here the differences

you might also want to repeat the process for the /var/log/syslog file  

(this is like looking at event viewer in NT5.1

---

