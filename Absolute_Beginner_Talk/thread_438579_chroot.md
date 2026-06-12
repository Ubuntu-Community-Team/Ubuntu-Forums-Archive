---
title: "chroot?"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by shayshay on 2007-05-09
Hi everyone,

I'm trying to edit some files in an attempt to boot ubuntu 7.04 off my external USB drive. I'm using the LiveCD at the moment, and I want to change the root in the terminal so I'm editing files on the external drive in super user mode.

Can anyone tell me how to do this?

:popcorn: 

Cheers,

Shay

---

### Post by taurus on 2007-05-09
Why chroot?  Just mount your external drive and edit it using sudo or gksudo.

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
(assuming /dev/sda1 is your external drive)
gksudo gedit /mnt/ubuntu/**filename**
```

---

### Post by shayshay on 2007-05-09
Oh, amazing. I'm editing away now :)

Thanks!

---

