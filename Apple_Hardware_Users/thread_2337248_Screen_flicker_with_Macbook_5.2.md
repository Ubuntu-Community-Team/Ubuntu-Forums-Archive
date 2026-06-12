---
title: "Screen flicker with Macbook 5.2"
date: 2016-09-16
forum: Apple Hardware Users
---

### Post by morefunthanafuneral on 2016-09-16
Hello, and apologies in advance as I'm somewhat new to linux. I have hooked an adapter to the mini DVI port on a Macbook 5.2 to an external monitor running Unbutu 16, and have screen flicker on the external without it affecting the Macbook's screen... Is there a terminal update I can perform to remedy this?
Thank you in advance

---

### Post by Bucky Ball on 2016-09-16
*Thread moved to **Apple Hardware Users**.*

Welcome. Better fit here. There are differences between a Mac and PC install that other Mac users will be able to help you with.

Do you have the correct drivers installed for the video card? Run this in a terminal and post the output back here between code tags (see green link in my signature for how).

```
sudo lshw -C video 
```

If you have just installed, yes, you should update anyway. Doubt that it will make any difference to this, but one never knows ... :-k

---

### Post by morefunthanafuneral on 2016-09-17
```

[COLOR=#000000]*-display [/COLOR]
[COLOR=#000000]description: VGA compatible controller[/COLOR]
[COLOR=#000000]product: C79 [GeForce 9400M G][/COLOR]
[COLOR=#000000]vendor: NVIDIA Corporation[/COLOR]
[COLOR=#000000]physical id: 0[/COLOR]
[COLOR=#000000]bus info: pci@0000:02:00.0[/COLOR]
[COLOR=#000000]version: b1[/COLOR]
[COLOR=#000000]width: 64 bits[/COLOR]
[COLOR=#000000]clock: 33MHz[/COLOR]
[COLOR=#000000]capabilities: pm msi vga_controller bus_master cap_list rom[/COLOR]
[COLOR=#000000]configuration: driver=nouveau latency=0[/COLOR]
[COLOR=#000000]resources: irq:26 memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:1000(size=128) memory:d3000000-d301ffff
[/COLOR]
```

---

### Post by Bucky Ball on 2016-09-17
Thanks for using the code tags. You only need to use the tags, they will do the rest. No bold or color tags required. :)

If you look in Additional Drivers, do you see any drivers there for your NVidia card? You are currently using the open-source nouveau driver, which is fine for lots of things, but sometimes not for dual- or more screens (at least in my experience). 

Have a look in Additional Drivers and let us know what you see. If there is one marked 'recommended', install and reboot.

---

### Post by morefunthanafuneral on 2016-09-18
options are as follows
using nvidia binary driver-version 340.96 from nvidia-340 (proprietary, tested)
using nvidia legacy binary driver-version 304.131 from nvidia-304 (proprietary)
using nvidia legacy binary driver-version 304.131 from nvidia-304-updates (proprietary)
using X-Org X server - Nouveu display driver from xserver-xorg-video-nouveau (open source) 
the nouveau one is checked

---

### Post by Bucky Ball on 2016-09-18
I found that the 304.XXX series drivers were used for this card, but that was when that driver was the latest! 

This

nvidia binary driver-version 340.96 from nvidia-340 (proprietary, tested)

... may well work, but try enabling the 'nvidia legacy binary driver-version 304.131 from nvidia-304-updates (proprietary)' first then reboot, just to be on the safe side. Again, this might be a Mac thing (the[ page I found]("http://askubuntu.com/questions/420630/ubuntu-on-mac-diver-for-nvidia-c79-geforce-9400m") was posted by a Mac user).

---

### Post by morefunthanafuneral on 2016-09-23
i tried the using nvidia legacy binary driver-version 304.131 from nvidia-304-updates (proprietary) option, and the mac hated it, so i went with using nvidia binary driver-version 340.96 from nvidia-340 (proprietary, tested), and it seems to be coping ok,ill thrash it later, and see if it holds up... sorry it has taken so long to say thank you for your time and patience, but 30 minutes ago is the first time ive gotten to this end of the house to look at the machine since you counselled me with possible solutions... 
greatly appreciated, bucky, youre a gentleman (or woman, i dunno) and a scholar... take care:)

---

