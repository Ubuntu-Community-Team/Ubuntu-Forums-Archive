---
title: "Resolution out of ranger after installing &quot;accelerated drivers&quot; 7.10"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by jeepfreak2002 on 2008-02-12
Just upgraded to 7.10

Everything went well untill I enabled the accelerated drive.  It installed fine, but upon reboot the new driver must have set the resolution or refresh too high.  

I can ctrl-alt-F1 to a login, but how do I adjust the resolution?

I tried the dpkg-reconfigure xserver-org - but it tells me the xserver is not running...  Any ideas?

---

### Post by jaytek13 on 2008-02-12
Well, the config file for X is /etc/X11/xorg.conf. In that file there is a monitor section where you can configure the refresh rate and a screen section where you can configure the default resolutions. I would recommend you copy and paste that file into this thread so someone can recommend what changes you might need to make. Also, a bit more description of what exactly your screen looks or is doing now would be helpful.

---

