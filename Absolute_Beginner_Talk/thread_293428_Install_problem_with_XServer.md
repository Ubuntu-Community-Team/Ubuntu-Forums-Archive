---
title: "Install problem with XServer"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by UncleB on 2006-11-05
Well, it doesn't exactly hang. The bottom half of the screen seems to have a thin coloured line on it that sometimes changes when I hit keys (eg. Trying to log in).

I've tried running "dpkg-reconfigure xserver-xorg" and got nowhere. Every time I reboot I get that 'hanging'.

Anyone got any ideas? My hardware is Athlon64 (939) 3200 and the GPU is a Radeon X800 256MB. I think that's all the relevant hardware.

I've also tried Xubuntu liveCD with the same result.

Thanks for any help.

---

### Post by UncleB on 2006-11-05
Fixed by entering in Safe CLI recovery mode and editing xorg.conf to use "vesa" in place of "ati" driver.

---

