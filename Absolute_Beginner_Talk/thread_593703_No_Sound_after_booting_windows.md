---
title: "No Sound after booting windows"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by andlessa on 2007-10-27
Hi,
I've just installed Ubuntu 7.04 in my laptop (HP Pavilion dv2000) and everything is working fine except for the sound. I have a dual boot with windows vista and if after turning on my laptop I boot straight to Ubuntu the sound works perfect. But if I first boot to Vista and then restart to Ubuntu my sound doesn't work at all. All the drivers seem to be installed and my volume is up, but I don't get any sound!
Here is the output for aplay:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And for lspci:

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

I've been looking everywhere for a solution, but I couldn't find it. It's the first time I'm using Ubuntu, so it may be some very stupid error.
Thanks.

---

### Post by Sp4cedOut on 2007-10-27
try unplugging the AC cable, shutting down, turning it back on, and plugging it in after you're in Ubuntu again.

---

### Post by hypnosis on 2008-01-19
I've exactly the same problem. Indeed if I shut down the PC then it will be working again... but I would like to be able to change between ubuntu and windows whenever I want without having to shut the computer down.

Anyone has an idea ?

---

### Post by hypnosis on 2008-01-24
No one can help ?

---

### Post by KingWilliam on 2008-02-04
I have the same problem here. If i want to game i run windows. Then i reboot into ubuntu and have no sound. When I reboot sound is just fine. Only after windows sound is gone. 

Anyone? It's a pain in the butt to reboot every time...

---

