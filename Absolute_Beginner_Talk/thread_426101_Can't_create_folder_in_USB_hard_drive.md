---
title: "Can't create folder in USB hard drive"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Charlie Chick on 2007-04-28
Hello Everybody,

I have what I believe to be a permissions problem. I connected my USB 2 hard drive and want to create a new folder, but Ubuntu won't let me. The option is greyed out. Looking at the properties for the drive, the owner (me!) is listed as root. I know enough to know that ordinary users in Ubuntu do not have root permissions as standard. 

My question is: how do I enable permissions to allow me full control over my own drive?

Many thanks, as always, for your help.

---

### Post by Najand on 2007-04-28
Can you copy/paste the output of following commands here:
```

$ mount
$ sudo fdisk -l

```

---

### Post by Biochem on 2007-04-28
The problem is probably due to the fact that your hard drive is formattted with NTFS.  Ubuntu cannot write out of the box to these partition. Fortunately it is easy to solve.

In feisty you just enter those following line in terminal:
```
sudo apt-get install ntfs-3g ntfs-config
gksu ntfs-config
```

In Edgy & Dapper things are a little more complicated. However if you follow the instruction of this post it will work
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by Najand on 2007-04-28
Well, if his problem is writing on NTFS, he should be very careful, because writing on NTFS Filesystem is still on its beta version and might cause some problems and data loss.

---

### Post by PilotJLR on 2007-04-28
No, the problem here is ownership. All you need to do to make yourself the owner.

First see what directory it is mounted as in the /media directory. For example, my LaCie USB disk is /media/Lacie

Then do a chown with your username. So let's say your username is charlie:
```

sudo chown -R charlie:charlie /media/Lacie

```

Obviously use your real username and directory name.
Might need to click "Reload" in Nautilus (the file browser), and then it should let you do whatever you want with the usb disk.

---

### Post by Najand on 2007-04-28
Well, we all don't know what is the problem; that is  why I asked for mount an fdisk output... LOL

---

### Post by PilotJLR on 2007-04-28
Ownership is ONE of the problems... though, yes, there certainly may be more than that.

> 
The option is greyed out. Looking at the properties for the drive, the owner (me!) is listed as root.


---

### Post by Najand on 2007-04-28
Agreed.... I just mean NTFS, mounting options etc might be other reasons.

---

### Post by Charlie Chick on 2007-04-29
Thank you all for your suggestions. I'll try them out in the next day or so.

---

### Post by Charlie Chick on 2007-05-14
Right, firstly, I converted the USB drive from NTFS to ext3 using GParted, as I want to use this disk as a backup disk. I then tried PilotJLR's suggestions to make myself the owner of the disk. They worked and I now have a working backup drive. Thanks to all of you and especially to PilotJLR.

---

