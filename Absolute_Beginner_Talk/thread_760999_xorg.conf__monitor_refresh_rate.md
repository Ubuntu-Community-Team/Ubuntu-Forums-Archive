---
title: "xorg.conf  monitor refresh rate"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by oldsoulsong on 2008-04-20
Hi all 
I was wondering if someone could make me an xorg.conf file up. I've tried from several guides but every time I try them I end up in low graphics mode. What I'm trying to do is increase the refresh rate to 75hz. Currently its on 52hz which is causing tears in videos.

I have Nvidia 6600 LE graphics card, and im using the standard nvidia restricted driver thing, and my resolution is is 1440x900

Thanks in advance

---

### Post by LowSky on 2008-04-20
run this command from safe mode start up it will let you set up you xorg file with the most cusomization that you need.
```
 sudo dpkg-reconfigure -phigh xserver-xorg
```
 Having one of us create your file is a bad idea, and why would you want to trust one of us to set it up. We could mess it up so bad you computer doesnt boot correctly, and you don't want that.

---

### Post by oldsoulsong on 2008-04-21
thnaks for that 

i tried it but it just comes up with this 

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080421141133

---

