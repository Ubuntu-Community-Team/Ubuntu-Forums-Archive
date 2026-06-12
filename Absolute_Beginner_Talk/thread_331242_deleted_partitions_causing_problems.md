---
title: "deleted partitions causing problems"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by ieee488 on 2007-01-04
I used GParted to delete my partitions as suggested by others on this message.
The partitions had OpenSUSE  (/hdb2  and   /hdb3).
Now when I try to boot into Ubuntu 6.06, it won't let me.

It looks like during boot-up it's doing an integrity check of the hard drives.

I tried  **update-grub**.

I can still boot into Windows 2000 which is how I'm on the internet so
Grub isn't broken.

Any ideas?

---

### Post by bulldog on 2007-01-04
If you delete partitions,the names will change,look in your menu.lst if it points to the right partition.
You can see how it should be pointing using```
sudo fdisk -l
```
You can open your menu.lst with```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by ieee488 on 2007-01-04
The problem wasn't with GRUB.

The problem was that when Ubuntu starts booting one of the things it does is check the filesystem which I think has something to do with  /etc/fstab  file.
The temporary fix was to use GParted to re-create  /dev/hdb2  and  /dev/hdb3  and format it to reseirfs.

I suppose I could have investigated   /etc/fstab  further.

I think I might be misunderstanding how I am suppose to be using GParted, but thankfully my system is booting fine again.  :)

---

### Post by taurus on 2007-01-04
Just put a # in front of the two entries for /dev/hdb2 & /dev/hdb3 in /etc/fstab...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```

---

### Post by ieee488 on 2007-01-05
Wow, that is easy. Thanks!

Learn something new every day. 

Nobody mentioned having to change  /etc/fstab
so I was a little worried when I couldn't boot into Ubuntu.

---

