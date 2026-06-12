---
title: "[SOLVED] Who or what loads fglrx?"
date: 2007-10-18
forum: Apple Intel Users
---

### Post by Carl Petersen on 2007-10-18
Since I'm on a an iMac I'll ask the question here:

I've installed the 8.41.7 fglrx driver from ati and it's running fine but I'd like to know what causes the kernel to load fglrx.ko when it boots? It's not specified in /etc/modules or anywhere else I can find.

---

### Post by cyberdork33 on 2007-10-18
> **Carl Petersen said:**
> Since I'm on a an iMac I'll ask the question here:

I've installed the 8.41.7 fglrx driver from ati and it's running fine but I'd like to know what causes the kernel to load fglrx.ko when it boots? It's not specified in /etc/modules or anywhere else I can find.

You specify a video driver in /etc/X11/xorg.conf

Also, if you mark a thread as solved, please make sure the solution is contained in the thread.

---

