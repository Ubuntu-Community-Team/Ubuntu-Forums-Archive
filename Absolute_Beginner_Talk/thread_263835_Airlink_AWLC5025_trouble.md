---
title: "Airlink AWLC5025 trouble"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by blx_286 on 2006-09-23
I have been searching the forum and google, but haven't found much yet. Has anyone got this card working?

I had a NetGear WG111 that was working kinda flakey with ndiswrapper and it took a dive yesterday. I decided to check out wifi-radar and it was all downhill from there. :confused: 

Anyway, since I originally had trouble getting the WG111 up in the first place, I went and bought this Airlink card today. Problem is I can't get it going either. I am a noob, but here's what I found with lspci -

```
0000:07:00.0 Network Controller: RaLink: Unknown device 0401
Subsystem: Unknown device 17f9:0011
Flags: bus master, slow devsel, latency 64, IRQ 11
Memory at f6000000(32-bit, non-prefetchable) [size=32k]
Capabilities: <available only to root>
```

I think I also have an IRQ conflict with IRQ 11 because after I plug in that wireless card, the laptop starts acting strange. Apps won't launch like Synaptic, Network or Device Manager and the laptop won't shutdown. If you hold down the power button long enough, it will shutdown but that's probably not good.

Can someone point me in the right direction?

Thanks.

---

### Post by blx_286 on 2006-09-24
Found the fix to my prob by following the directions in this thread [http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980)

My chipset is by RaLink and the drivers are RT61.

---

