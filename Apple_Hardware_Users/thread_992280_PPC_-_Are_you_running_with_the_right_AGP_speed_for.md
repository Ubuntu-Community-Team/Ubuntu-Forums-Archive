---
title: "PPC - Are you running with the right AGP speed for video?"
date: 2008-11-24
forum: Apple Hardware Users
---

### Post by stream303 on 2008-11-24
Most of our video cards are listed at 2x, 4x, or 8x AGP, but I'm not sure if the installer is aware of this.  You can specify this in /etc/X11/xorg.conf, but on my nvidia-driven machine, that option is ignored as witnessed by looking at the /var/log/Xorg.0.log

My question is if anyone running ATI cards has been able to specify this for their machine's spec, and had it accepted?

I'm not sure if the newer X server's detect the proper AGP speed automatically or properly.  If they don't, that might be a nice boost to video for sure....

Update!  Looks like the answer was in our faqs:

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

