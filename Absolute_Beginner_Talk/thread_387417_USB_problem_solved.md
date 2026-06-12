---
title: "USB problem solved"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by francesco44 on 2007-03-18
I had some problems related to the impossible auto mount of USB devices. I wandered through the forums for more than a week, just seing that many others had the same problems. I read a lot about fantasies solution.

In fact it was easy to solve.....just a missing line in fstab.

My present fstab is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=9c362dc3-4d23-40a7-8f9c-699e5c047248 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=2e429432-7ba9-4921-8e21-49619d82c321 none            swap    sw              0       0
/dev/sda1       /media/usb      auto user,rw     0       0
/dev/sda2       /media/cdrom0   udf,iso9660 user,noauto     0       0


my older fstab was:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=9c362dc3-4d23-40a7-8f9c-699e5c047248 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=2e429432-7ba9-4921-8e21-49619d82c321 none            swap    sw              0       0
/dev/sda1       /media/cdrom0   udf,iso9660 user,noauto     0       0

As you can see the line related to the automount of USB key was not there


GENERAL LESSON: usually when a problem is encountered most people rely to auto diagnosis....the interpretation of which is never evident

It seems much better to look directly at the files which are known to be involved in a problem USB mount FIRST LOOK AT FSTAB!

I solved also this way a problem with keyboard config.....A keyboard config? FIRST LOOK AT XMODMAP

I suggest very strongly to the "beginners team]" to build a correspondance between

PROBLEMS...........USUALLY INVOLVED FILES
+
Examples of files with comments.....

This obviously do not works for all problems but seems to me much more efficient that  
walking trhough the labyrinth of the forums

Viva UBUNTU

Piero Francesco

---

### Post by buuntuu! on 2007-03-18
i agree with you there!
what should be done more explicitly by the community in my point of view is to promote the understanding of how linux works. i know that you can find it out by yourself browsing the forum and reading the wiki, but newbies converting from window$ might need a little help as they are used to not understanding how their computer works and might not even try to get to know their system at first. if they run into serious trouble before they get to this point and do not find an answer in the forum immediately they might switch back to M$...

---

