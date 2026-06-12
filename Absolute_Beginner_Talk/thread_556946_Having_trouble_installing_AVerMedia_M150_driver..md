---
title: "Having trouble installing AVerMedia M150 driver."
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by orion2087 on 2007-09-22
Hey guys, I've got a AVerTV 1500MCE which looks to be the same chipset as a M150 so I'm trying to follow [this](http://www.mythtv.org/wiki/index.php/AVerMedia_M150-D) guide on getting it set up for MythTV.

I followed the directions to get the firmware files set up, but I'm only seeing a /dev/video0, video 1 is no where to be found. I ran dmesg and noticed this part at the end:

```
[ 3608.635317] cx2388x dvb driver version 0.0.6 loaded
[ 3608.635321] cx8802_register_driver() ->registering driver type=dvb access=shared
[ 3608.635325] CORE cx88[0]: subsystem: 1461:c111, board: ASUS PVR-416 [card=12]
[ 3608.635510] cx8802_register_driver() ->probe failed err = -19
[ 3614.849964] cx2388x blackbird driver version 0.0.6 loaded
[ 3614.849968] cx8802_register_driver() ->registering driver type=blackbird access=shared
[ 3614.849971] CORE cx88[0]: subsystem: 1461:c111, board: ASUS PVR-416 [card=12]
[ 3614.850173] cx88[0]/2: cx23416 based mpeg encoder (blackbird reference design)
[ 3614.850650] cx88[0]/2: registered device video1 [mpeg]
```

When I run "sudo modprobe cx88-dvb" (found in a thread [here](http://ubuntuforums.org/showthread.php?t=446022): I get ```
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.20-16-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device
```

Any ideas guys? Thanks!

---

