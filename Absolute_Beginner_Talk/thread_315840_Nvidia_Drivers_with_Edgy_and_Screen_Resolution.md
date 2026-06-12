---
title: "Nvidia Drivers with Edgy and Screen Resolution"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by kandarz on 2006-12-09
I just upgraded to Edgy from Dapper (clean install) and am trying to get my nvidia drivers to work.  I had them working in Dapper with Beryl fine after just an hour of tweaking but it seams that Edgy is causing me more problems.

I have a EVGA Nvidia Geforce 7600 GT KO graphics card and the nvidia drivers do seam to load but I'm unable to get a resolution above 800x600 @ 50 Hz, actually that's the only option at all.

My /etc/X11/xorg.conf file I believe is setup correctly. I've attached it to this message.

Now I'm running a Optiquest Q95 (Viewsonic tube) 19in CRT off a dual head DVI card with an adapter.  The Q95 supports up to 1600x1200 @ 80 Hz and I'd like to run at 1280x1024 @ 80 Hz.

The Nvidia Settings works but it says that the GLX X server extention isn't supported but the xorg.conf file says to load it.

I installed this all from the Ubuntu repo's using nvidia-glx and it is configured from nvidia-xconfig.  I've reconfigured xserver-xorg numerious times but no luck.

So in the end I'd like to be able to use 1280x1024 @ 80 Hz along with Beryl. Thanks in advance to anyone with information.

---

### Post by dbbolton on 2006-12-10
if you want to double-check your xorg.conf, run :

sudo dpkg-reconfigure xserver-xorg

---

