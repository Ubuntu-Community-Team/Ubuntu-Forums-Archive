---
title: "Wifi not working - module wl not found"
date: 2017-02-12
forum: Apple Hardware Users
---

### Post by defranos on 2017-02-12
Hi,

I recently installed ubuntu 14.04 alongside my mac os on a mac book pro. I'm experiencing the same issue than a lot of users : the wifi is not working. I've been browsing a lot and tested a lot of things but I can't get it to work.

I've got a BCM 4360 and the adapter is a 14e4:43a0.

I've updated the headers

After installing (and re installing multiple times ) bcmwl-kernel-source aswell as the dkms, I'm still unable to run the command ```
modprobe wl
``` which returns FATAL: Module wl not found.

And this error appears aswell when I run the command ```
apt-get install --reinstall bcmwl-kernel-source
```.


Any help would me much appreciated.

---

### Post by howefield on 2017-02-13
Thread moved to the "*Apple Hardware Users*" forum.

---

