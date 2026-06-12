---
title: "power off issue kernel 3.7rc2 ubuntu 12.10 ux32a"
date: 2012-10-22
forum: Asus Ubuntu Support (CLOSED)
---

### Post by tadaz on 2012-10-22
When i booting kernel 3.6.x my laptop is able to boot only on external monitor.

Kernel 3.7 fixed it somewhat that it's possible to boot without external monitor, but power off do not work (stays at screen with message something about shutdown now..). Also wifi switch and sleep buttons do not wrok anymore (3.6.x they work, well at least do something).

Did you have similar issues and know solutions?

---

### Post by zezadas on 2012-10-23
> **tadaz said:**
> When i booting kernel 3.6.x my laptop is able to boot only on external monitor.

Kernel 3.7 fixed it somewhat that it's possible to boot without external monitor, but power off do not work (stays at screen with message something about shutdown now..). Also wifi switch and sleep buttons do not wrok anymore (3.6.x they work, well at least do something).

Did you have similar issues and know solutions?

i dont have problems, also i'm still in rc1, compile it with this config [http://pastebin.com/XXz4U1uB](http://pastebin.com/XXz4U1uB)
if the problem persists maybe its you ubuntu installation

---

### Post by tadaz on 2012-10-23
Thanks for hint! I will try it as soon as i will be able allocate few hours of time.

---

### Post by tadaz on 2012-10-23
It seems what i was unable to unlock achievement related to kernel compilation this time, but i found that there is few more pals experiencing similar issues

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/946311/+index?comments=all](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/946311/+index?comments=all)

Currently suggested workaround to light-up internal display: power-on, when after its done Fn+F1 -> put it to sleep, when wake-up. Screen works.

---

