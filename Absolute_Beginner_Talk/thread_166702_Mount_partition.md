---
title: "Mount partition?"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by arsenik on 2006-04-26
I installed my ubuntu following the dual-boot guide where you partition 10gig of fat32 space for share between linux and windows.  This is a great idea, however, I can't access that partition in linux. I'm not sure how to "mount" the partition?

Sorry I'm really a huge newb to linux.

---

### Post by macdo on 2006-04-26
System > Administration > Disks

Choose your Hard drive to the left, then click on Partitions
Find the Partition formated with Fat32, and click "enable"

---

### Post by olsonar on 2006-04-26
We were all newbs at one point. It's nothing to be ashamed of.

macdo's solution works, but if you want it to mount at boot, you'll need to edit your fstab file:

```
sudo gedit /etc/fstab
``` 
and add a line for your fat32 partition like this:

```
/dev/hda7 /media/fat32 vfat iocharset=utf8,umask=000  0 0
``` 
you'll need to change /dev/hda7 to point to your fat32 partition, and /media/fat32 to where you want the partition mounted. Then, to mount the partition, do

```
sudo mount -a
``` 
Now it'll be mounted and will mount automatically at startup.

---

### Post by arsenik on 2006-04-27
i added the above info to /etc/fstab and when i do mount -a i get:

mount: mount point /media/fat32 does not exist

---

### Post by arsenik on 2006-04-27
Update: I did sudo mkdir /media/fat32 and then type sudo mount -a and I didn't get any errors.  Did this work?> 

---

### Post by wh0rd on 2006-04-27
[QUOTE=arsenik]Update: I did sudo mkdir /media/fat32 and then type sudo mount -a and I didn't get any errors.  Did this work?[/QUOTE]

Goto the location /media/fat32 and see for yourself.

---

### Post by delta32 on 2006-04-27
Oops. :x Can't find the delete button. Ignore this post, sorry. x_<

---

### Post by masonfoley on 2006-05-07
Linux noob here.

I've been successful in mounting the partition however none of the files can be opened.  The icons representing the files have a red "x" overlayed on them.

Any suggestions?

---

### Post by Iarwain ben-adar on 2006-05-07
I had that problem too :-)

Try as root (only way i could access them)


Iarwain

---

### Post by aysiu on 2006-05-07
[QUOTE=masonfoley]Linux noob here.

I've been successful in mounting the partition however none of the files can be opened.  The icons representing the files have a red "x" overlayed on them.

Any suggestions?[/QUOTE] [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by masonfoley on 2006-05-10
[QUOTE=aysiu][http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)[/QUOTE]
Excellent.  Thanks for the pointer.

---

### Post by masonfoley on 2007-05-21
> **aysiu said:**
> [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

```
sudo mount -a
``` did the trick for me.  Just need to get that into my startup scripts so I don't have to do it manually.

---

