---
title: "trying to figure out what to put in fstab"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by bcdeck on 2006-12-07
Can someone help a poor noob?

I'm trying to figure out what to put in the fstab file to allow me to access an NT-formatted disk in Edgy. I am working my way through the instructions at [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows), but I'm not what sure what changes I need to make in fstab. Here's my fdisk information (/dev/hdc1 is the one I want to access):

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9541    76638051   83  Linux
/dev/hda2            9542        9729     1510110    5  Extended
/dev/hda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/hdc: 20.5 GB, 20576747520 bytes
255 heads, 63 sectors/track, 2501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        2500    20081218+   7  HPFS/NTFS






Thanks. :)

---

### Post by bscbrit on 2006-12-07
Try 
[https://help.ubuntu.com/community/MountNtfsOnBoot](https://help.ubuntu.com/community/MountNtfsOnBoot)

which suggests:

  /dev/hdc1 /mnt/ntfs1 ntfs ro,nls=utf8,umask=0222 0 0


Note: hdc is an entire drive, you can only mount 1 partition with each fstab statement.  So you will have to mount hdc1, then perhaps hdc2 etc.

---

### Post by groggyboy on 2006-12-07
where do you want to mount it?  if you haven't already created a directory to mount it, you should.  I mount my windows partition at /media/windows - the psychocats tutorial suggests using /windows.

once you have the directory in place, edit your fstab - in a terminal type "gksu gedit /etc/fstab" or (for Kubuntu) "kdesu kate /etc/fstab".

you need to create a new entry at the bottom of the file.  for you, it should look like this: ```
/dev/hdc1 /windows ntfs defaults,nls=utf8,umask=007,gid=46 0 1
```
i used /windows in that line above, but you should change it to the name of the directory you are using.

edit - i see bscbrit has already posted - just so you don't get confused, my reply is based on the psychocats method - i'm guessing his reply is based on the method of the link he posted (the Ubuntu Wiki).  i'm sure either will work.

---

### Post by bcdeck on 2006-12-07
Thanks groggy, that was exactly what I needed. Have the drive mounted and can access now. :-D

---

