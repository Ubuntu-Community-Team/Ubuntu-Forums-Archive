---
title: "Help and Guidence please"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by yiggaman on 2007-04-29
im trying to install drivers for wireless network card, im hopping i have the right drivers? but this camez ups?

what do i need to do from here???


yiggaman@y1:~$ sudo ndiswrapper -i /home/yiggaman/WPC54G v4 driver rev 1.22.1.2004/WLIPNDS.INF
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile Install driver described by 'inffile'
-d devid driver Use installed 'driver' for 'devid'
-e driver Remove 'driver'
-l List installed drivers
-m Write configuration for modprobe
-da Write module alias configuration for all devices
-di Write module install configuration for all devices
-v Report version information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX

---

### Post by Ecthelion on 2007-04-30
You get this message because the line you entered is not how it should.
I don't know how it should, but if you want to know, read the manual...

```
man ndiswrapper
```

---

### Post by Outrunner on 2007-04-30
Try 

```
sudo ndiswrapper -i /home/yiggaman/WPC54G\ v4\ driver\ rev\ 1.22.1.2004/WLIPNDS.INF
```

---

