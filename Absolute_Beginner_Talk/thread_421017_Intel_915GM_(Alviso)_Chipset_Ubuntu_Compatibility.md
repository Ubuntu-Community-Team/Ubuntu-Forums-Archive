---
title: "Intel 915GM (Alviso) Chipset Ubuntu Compatibility"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by jopv on 2007-04-24
I'm planning to buy the IBM/Lenovo Z60T laptop with the following config:

Intel Mobile Centrino II  (Sonoma) Pentium M 760 (2,0 GHz/ 2 MB L2 Cache/ FSB533 Dothan)
Chipset: Intel 915GM (Alviso)

I would like to know if this chipset is supported by Ubuntu/Kubuntu

Thanks, JOHN

---

### Post by ramjet_1953 on 2007-04-24
There are two solutions to adding the additional resolution settings that are not actually inside the intel chipsets.

1. Use Synaptic to download [COLOR="Red"]915resolution[/COLOR]
This works, but requires some fiddling and ptching of redundant modes and perhaps even setting-up modelines

2. The latest and greatest is to download, again using Synaptic[COLOR="Red"] xserver-xorg-video-intel[/COLOR]
This is the latest intel driver and should automatically detect your screen aspect ratio and set it all up automatically.

Regards,
Roger :cool:

---

### Post by mikeyphi on 2007-04-24
I don't think there is a list of what IS supported...but probably the only way to find out is to try the Live CD before you buy...perhaps not the best answer but an option!!

---

### Post by mills on 2007-04-24
at a glance it doesn't look promising

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

[http://doc.gwos.org/index.php/HCL](http://doc.gwos.org/index.php/HCL)

---

