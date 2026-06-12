---
title: "BOOT ERROR: dev/disk/byuuid/verylongnumber does not exist"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-10-28
sometimes but not always I get the following boot error

dev/disk/byuuid/verylongnumber does not exist

I assume the verylongnumber is my HDm which is partitioned into winXP and linux

should I worry about my HD? And what could I do the check it?

---

### Post by ginestre on 2007-11-02
<bump>

---

### Post by Zorg-it on 2008-04-05
Hey try having look at this [http://ubuntuforums.org/showthread.php?t=414903](http://ubuntuforums.org/showthread.php?t=414903)
I've the same problem right now!

---

### Post by ginestre on 2008-04-11
Thanks for the link. I'm trying to understand it all. Did you solve your version of the problem?

---

### Post by bodhi.zazen on 2008-04-11
Boot the ubuntu desktop CD and post the output of these commands :

```
sudo fdisk -l

sudo blkid
```

We then need to look at /etc/fstab and /boot/grub/menu.lst (in your ubuntu partition) and make sure the proper disk is listed by the proper uuid is listed.

If you know how , please mount your Ubuntu partition somewhere ( /mnt ?) 

See these links for some info :

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

