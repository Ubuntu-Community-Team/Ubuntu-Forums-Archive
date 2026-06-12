---
title: "internet keeps coming on and off..."
date: 2005-09-23
forum: Absolute Beginner Talk
---

### Post by taseal on 2005-09-23
I have eth0 and eth1

both sometimes seem to work, and sometimes they dont feel like working...

pretty random...

anyone know a cause to this?

i noticed that everytime this happens, i go to network tools and select the eth i want and go to configure and press ok sometimes it'll make it work again ?

---

### Post by FLeiXiuS on 2005-09-23
[QUOTE=taseal]I have eth0 and eth1

both sometimes seem to work, and sometimes they dont feel like working...

pretty random...

anyone know a cause to this?

i noticed that everytime this happens, i go to network tools and select the eth i want and go to configure and press ok sometimes it'll make it work again ?[/QUOTE]

Default route set?

---

### Post by mlomker on 2005-09-23
> i noticed that everytime this happens, i go to network tools and select the eth i want and go to configure and press ok sometimes it'll make it work again ?

Is it a wired and wireless connection that go to the same place?  That can cause trouble.  Do an **sudo ifconfig ethX down** on the one that you don't want to use.

---

