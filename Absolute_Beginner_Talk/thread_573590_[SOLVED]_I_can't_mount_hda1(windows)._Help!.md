---
title: "[SOLVED] I can't mount hda1(windows). Help!"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by offline on 2007-10-11
I loaded Administration > Disks and noticed the partition number and filesystem for my Windows partition. 
 
/dev/hda1 vfat

Then using terminal:


```
$ sudo mkdir /media/win1
$ sudo gedit /etc/fstab

```

At the bottom of the file added a line like this for the mount point:

/dev/hda1 media/win1 vfat users,rw,owner,umask=000 0 0

Then in terminal:

```
$ sudo mount -a
```

It replied that mount point win1 does not exist. I went to /media/win1, it's  there but blank. I went to computer there is an icon of my windows master disk with it's name "such and such" but 0 bytes. Won't mount grom GUI either

I checked /dev and something strange happened. Every hd* has as a default application for opening it: "vlc".

---

### Post by finer recliner on 2007-10-11
> 
/dev/hda1 media/win1 vfat users,rw,owner,umask=000 0 0



you need a slash (/) in front of media

---

### Post by offline on 2007-10-11
Thanks...thanks...and...thanks

---

