---
title: "Mounting a second ext3 partition"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by crazybrit4967 on 2007-01-08
I want to mount a second ext3 partition (other than the one that's used as root in Ubuntu) in Edgy.  I'd like for all users to have full access to all the files on it and for it to be mounted at startup.  Does anyone know how to do this?

---

### Post by Bachstelze on 2007-01-08
Just create a mountpoint for your parittion and use /etc/fstab to have it mounted as boot. If you have permissions problem, a simple CHMOD will let you set them as you wish.

---

### Post by aysiu on 2007-01-08
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) should help you.

---

