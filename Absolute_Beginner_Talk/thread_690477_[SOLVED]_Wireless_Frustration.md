---
title: "[SOLVED] Wireless Frustration"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Jay Crown on 2008-02-07
I am new to Linux in general and I am having some problems. I have no idea how to get my Belkin Wireless rt2570 device to work.  I downloaded the driver and when I try to install it I get this:

```
make[1]: *** No rule to make target 'Tried/rt2570-1.1.0-b2/Module'.   Stop.
```

I tried a to download the driver from a different place and when attempting to install that I got pretty much the same error.

I tried to install RutilTv0.16 too but I'm a bit frustrated trying to find and gather a bunch of dependencies for it's dependencies and their dependencies and so on. Is there an easier way? I do not have any internet access on that desktop so I've been downloading all these dependencies (glib, xlib, zlib, cairo, pango, x11, atk, gtk, and on and on) onto a USB drive and moving them over to try to install them. Is there a better way?

Also, some of the dependencies do not seem to have a Makefile. How do I install those? And most of all how do I get this USB wireless device working?

Also 'iwconfig' brings up this if it helps:

```

lo             no wireless extensions.

eth0        no wireless extensions.

rausb0    RT2500USB WLAN   ESSID:"Kingdom"
               Mode:Managed   Frequency=2.412 GHz   Bit Rate-11 Mb/s
               RTS thr:off   Fragment  thr:off
               Link  Quality=0/100   Signal  level:-120 dBm  Noise level:-200 dBm
               Rx invalid nwld:0   Rx invalid crypt:0  Rx invalid  frag:0
               Tx excessive retries:0   Invalid misc:0 beacon:0

sit0         no wireless extensions.
```

I've successfully (I think) installed ndiswrapper1.51 but I do not know how to use it. I read something about using it to install a legacy driver but like I said I'm new and I am lost. Help? Thanks in advance

-Jay

Any help or pointing in the right direction would be very much appreciated. Thanks

---

### Post by xc3RnbFO8P on 2008-02-07
Try this HOWTO:

> [http://ubuntuforums.org/showthread.php?t=106846](http://ubuntuforums.org/showthread.php?t=106846)

---

