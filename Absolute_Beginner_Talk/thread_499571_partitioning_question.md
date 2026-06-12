---
title: "partitioning question"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by darmot7 on 2007-07-12
my question is, i formated my hard drive to have a large partition for storing video recordings in /var/lib, however since then ive decided that i do not want to allocate that much space to /var/lib. how would i go by removing the binding on the partition /var/lib/ and moving it back to the root partition? 

could i just copy /var/lib and then move that to /home and then remove the binding in fstab? then go back and place the copied /var/lib to /var?

also when i boot from the livecd and try to use gparted it tries to mount the volume while its supposed to be executing an action.. this of course stops gparted and im left with no result, is there a way around that?

thank you,
darmo t:KS

---

### Post by petedct on 2007-07-12
Try using gparted (Gnome Partition Editor) to resize /var/lib and then reallocate the unused space into the root partition. You can find all the gparted info you'll need there: [http://http://gparted.sourceforge.net/]("http://http://gparted.sourceforge.net/")

---

### Post by BobCFC on 2007-07-12
Copying to home is only worth it if you want to delete /var/lib partition (and home is big enough!)

You can get a special [Gparted LiveCD]("http://gparted.sourceforge.net/livecd.php") only 50mb iso.  That will resize partitions without mounting problems.

---

### Post by darmot7 on 2007-07-13
thanks alot for the responses.

---

