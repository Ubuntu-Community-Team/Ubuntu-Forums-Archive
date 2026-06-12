---
title: "[SOLVED] Trying to edit fstab on client machine for NFS server mount -- need help ple"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-11-22
I have the server set up on my main computer and client setup on this one. I am trying to edit the fstab so I can mount the server files but keep getting message in terminal saying "mount point nfs does not exist". Been working on this most of the day and being a noob -- you guessed it -- lots of problems. I don't think I have the fstab edited correctly. Here is my feeble attempt, please try and keep the laughter to a minumim

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ebd5f78c-2f94-43be-a744-2a0a21cc15ef /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=0875df0c-f75c-417a-8acd-3c7d01245662 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
192.168.1.103:/home/jerrynewt/share nfs rsize=8192,wsize=8192,timeo=14,intr

Is this even close ?? As you can see I am into the hunt and peck mode so any suggestions would be greatly appreciated.

---

### Post by banewman on 2007-11-22
[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)
 was the way I got my system mounting the files from the nfs server. Hope it helps. :)

---

### Post by delphiguy on 2007-11-22
what happens it you change this line
192.168.1.103:/home/jerrynewt/share nfs rsize=8192,wsize=8192,timeo=14,intr

into
192.168.1.103:/home/jerrynewt/share /yourmountpoint nfs rsize=8192,wsize=8192,timeo=14,intr

of course yourmountpoint must exist first so you have to create a directory for that.

---

### Post by jerrynewt on 2007-11-23
The last suggestion worked like a charm. Thanks again!

---

