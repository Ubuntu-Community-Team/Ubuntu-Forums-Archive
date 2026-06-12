---
title: "Does anyone has the xorg,conf for an iMacDV G3 400Mhz 128MB 10 GB"
date: 2009-02-17
forum: Apple Hardware Users
---

### Post by DrKenobi on 2009-02-17
I've just installed Xubuntu 8.10 PPC on my iMacDV G3 400Mhz 128MB 10 GB.
I can only start in Low Graphical Mode. I know I need to configure xorg.conf, but I don{t know how. Does anyone has the xorg,conf for my iMac?

Thanx

---

### Post by kerry_s on 2009-02-17
boot in failsafe/single/rescue mode and run> X -configure
you will then have a /root/xorg.conf.new you can use.

**cat /root/xorg.conf.new > /etc/X11/xorg.conf**

---

