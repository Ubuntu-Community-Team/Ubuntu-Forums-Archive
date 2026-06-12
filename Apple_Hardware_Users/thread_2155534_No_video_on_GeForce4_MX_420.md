---
title: "No video on GeForce4 MX 420"
date: 2013-06-18
forum: Apple Hardware Users
---

### Post by dbbolton on 2013-06-18
I have an 867mHz G4 with an nVidia GeForce4 MX 420, and I can't get X to work with any recent Linux distro. The last thing that worked was Debian squeeze. I installed Debian wheezy, and I can get to a TTY, but only by sshing into the machine, blacklisting nouveau, and restarting. 


As for X, I have tried both the vesa and fbdev drivers (fbdev is what X -configure chose) with no luck. I tried booting a 12.10 PPC live CD and the video of course doesn't work.


Essentially, I am just looking for some advice as to what combination of kernel+driver will allow me to run X on this machine, or if anyone has even been successful getting X to work with this chipset.


More specific card info:
```
0000:00:10.0 VGA compatible controller [0300]: NVIDIA Corporation NV17 [GeForce4 MX 420] [10de:0172] (rev a3) (prog-if 00 [VGA controller])
    Subsystem: NVIDIA Corporation Device [10de:0008]
    Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 48
    Memory at 91000000 (32-bit, non-prefetchable) [size=16M]
    Memory at 98000000 (32-bit, prefetchable) [size=128M]
    Memory at f1000000 (32-bit, prefetchable) [size=512K]
    Expansion ROM at 90000000 [disabled] [size=128K]
    Capabilities: [60] Power Management version 2
    Capabilities: [44] AGP version 2.0
```

---

### Post by dbbolton on 2013-06-26
My solution was to install Debian Squeeze since the nv driver works.

---

### Post by abtabt on 2013-06-27
you can try this without wipe hd (USB boot)

[http://ubuntuforums.org/showthread.php?t=2131644](http://ubuntuforums.org/showthread.php?t=2131644)

post #7

---

