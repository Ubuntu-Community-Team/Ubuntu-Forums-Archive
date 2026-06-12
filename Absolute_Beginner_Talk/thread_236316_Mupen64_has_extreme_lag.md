---
title: "Mupen64 has extreme lag"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by emprog on 2006-08-14
After some searching on this forum for a good N64 emulator I came across Mupen64 and so I installed it. If I load any roms I get extreme lag, not even playable quality. The computer I am currently using is not the greatest but I thought it would be good enough for a N64 emulator. I am hoping it is just a configuration issue. Here are my results from glxgears..

461 frames in 5.3 seconds = 86.544 FPS
456 frames in 5.5 seconds = 82.561 FPS
456 frames in 5.8 seconds = 79.036 FPS

Here are my results from lspci...

erick@wolf:~$ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 80)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 14)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
0000:00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0c.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

Also, I have about 477MB of low mem available and a p4 processor.

Thanks.

EDIT:::

Something else I tried..

erick@wolf:~$ glxinfo | grep render
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

Is there a way around this?

---

### Post by reacocard on 2006-08-14
might i ask what graphics chip and cpu you have?

mupen64 requires a fair bit of power to run well. on my laptop with a pentium M processor and intel 915 integrated graphics, mupen64 runs with the processor scaled all the way down (600MHz ~= 1.5 ghz p4) but is somewhat choppy. with processor scaled all the way up (1.7GHz ~= 2.6 ghz p4) it runs perfectly smoothly. for glxgears, scaled down gives about 690 fps, scaled up, over 1000. but my glxinfo says i have direct rendering, which probably helps.

---

### Post by emprog on 2006-08-14
**might i ask what graphics chip and cpu you have?



How can I get this information from terminal?

---

### Post by reacocard on 2006-08-14
for cpu:
```
hwinfo | grep "cpu MHz"
```
will get cpu speed in MHz.

no idea for the graphics though.

---

### Post by %hMa@?b&lt;C on 2006-08-14
what plugins are you using.? Zelda OoT runs full speed for me... My favorite game EVER!!!! I have beaten it at least 15 times.
with RICE'S PLUGIN it runs well for me

---

### Post by emprog on 2006-08-14
This is what I get from hwinfo

erick@wolf:~$ hwinfo | grep "cpu MHz"
bash: hwinfo: command not found

About the plugin, I am really not sure. I thought my problem had something to do with 3d accel not being activated but since I am using a laptop with an integrated video card I am not sure if there are drivers for me available?

---

### Post by reacocard on 2006-08-15
my laptop has integrated, and direct rendering, so obviouly it's possible. what model laptop do you have?
As for hwinfo, try "sudo apt-get install hwinfo", then redoing that command.

---

