---
title: "Beginner Trouble with Mounting CD drive"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Krextyl on 2007-10-25
I've read several other threads and tried to piece it together but Im just not getting it right.

I just installed 7.10 64bit from scratch. Now I want to install my printer but the drivers are not listed under the system>admin>printing setup, but I have a cd that came with my printer which has linux drivers on it. (new printer is Samsung ML-3050) By accident I stuck in the window Driver disk instead of the Linux disk and went through the forums of learning how to mount the CD drive since it apparently didn't automount (not sure why thats not default on install). Also in Places>Computer> right click my CDRW/DVD+-RW drive Mount Volume doesn't work - had to sudo mount it. Anyway I tried to eject it and it will not let me because it says it needs to be unmounted by root (screen shot attached). I read about a sudo unmount command in another thread but it gives me a unknown command when I try it. Obviously I could just reboot and eject but I would like to learn how to fix this, also I saw post about etc/fstab to make it automount, I would like to edit mine so it automatically works each time in the future, here is my files text:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=15ebbdaa-8215-4b95-bb59-9a87e4a76597 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=efef3ac7-c330-4baf-ae65-2e096d129650 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Thanks

---

### Post by Krextyl on 2007-10-25
Ok that was wierd, I needed to swap CD's in the mean time so I went ahead in hit restart so I could eject the CD after exiting. And now its all working correctly - CD's insert and eject correctly - Why??

---

