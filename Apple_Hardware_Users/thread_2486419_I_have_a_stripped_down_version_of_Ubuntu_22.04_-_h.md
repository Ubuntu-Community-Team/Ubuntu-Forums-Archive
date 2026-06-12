---
title: "I have a stripped down version of Ubuntu 22.04 - how to add additonal software"
date: 2023-04-29
forum: Apple Hardware Users
---

### Post by zonkers on 2023-04-29
I installed Ubuntu on a 2018 Mac Mini and could not get the wi-fi working.  However, following the excellent instructions on [https://t2linux.org/](https://t2linux.org/), I was able to get the wi-fi and bluetooth working.  However, the [https://t2linux.org](https://t2linux.org) website has a ubuntu 22.04 ISO image built for Macs with the T2 chip but it does not include most of the typical apps (software center, firefox, vim, etc.). 

Is it recommended to do a "sudo apt-get install gnome-software"?

Thnaks

---

### Post by ajgreeny on 2023-04-29
Moved to ***Apple Hardware Users*** forum for a better fit.

---

### Post by BBQdave on 2023-04-29
> **zonkers said:**
> Is it recommended to do a "sudo apt-get install gnome-software"?

You can, and have a graphical user interface to load applications. Or you can load applications with: sudo apt-get install *application*.

Although Ubuntu default should include **Ubuntu Software**, with which you can load .*deb* or *snaps*.

---

### Post by zonkers on 2023-04-29
For some reason **Ubuntu Software** is not installed but I was able to install **gnome-software**.  Is there a way to install Ubuntu Software?  Thanks.

---

