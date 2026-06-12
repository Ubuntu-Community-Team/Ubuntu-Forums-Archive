---
title: "mount program"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by srg84 on 2007-05-22
Hi, is there a way to mount partition with option choose (like read only..), with graphical interface???

---

### Post by taurus on 2007-05-22
What filesystem is that partition?

---

### Post by srg84 on 2007-05-22
ext3 i need the program because when i want to write to it i must umount it and mount again in read-write mode and then when i finish readonly mode, data in this disk is very important

---

### Post by scott_g on 2007-05-22
There is the disk mounter tool for the gnome pannel (right click on pannel and click add), but I'm not sure if that will let you mount it in read only mode or not, but at least it lets you mount/unmount the drive easily.

Scott

---

### Post by taurus on 2007-05-22
If root is the ownership of the mount point, then you can only read from it unless you change the permissions.

```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
ls -la /media
```
Assuming the partition is /dev/sda1.

---

### Post by srg84 on 2007-05-22
I need something more complicated, this doen't have the option

---

### Post by srg84 on 2007-05-22
but i need a program with graphical user interface

I want the disk to be mounted in read only mode, because I am a little bit stupid and I can delete all the disk executing a command with root privileges

---

### Post by taurus on 2007-05-22
I am not sure exactly what you mean or need.  Can you go into a little more details?

---

### Post by srg84 on 2007-05-22
OK i want a program with GUI to mount my partition ext3 and that program must have some mount options like read-only mode implemented with a checkist or something similar,

thats it ;)

---

### Post by taurus on 2007-05-22
Check out gnome-mount if you don't want to mount it from a terminal.

[http://www.linuxfromscratch.org/blfs/view/svn/gnome/gnome-mount.html](http://www.linuxfromscratch.org/blfs/view/svn/gnome/gnome-mount.html)

---

### Post by srg84 on 2007-05-22
this is not a program only a packages of commands  :(

---

