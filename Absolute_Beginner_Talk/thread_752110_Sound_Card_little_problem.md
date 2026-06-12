---
title: "Sound Card little problem"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by L1nux01D on 2008-04-11
Hello World!Have a small problem here.Actually I had this problem before,since I'm using Linux,but I decided to fix it.If you'll help me of course.

The problem is,some applications,such as XMMS,Firefox,Totem,use sound card fully.I mean if I launch 1 of this,I can't use another with sound.I can't play WoW with sound,and listen music at the same time.Or watch youtube and listen music.

How to fix it?

---

### Post by ibutho on 2008-04-11
Install libesd-alsa, logout of GNOME and back in again. Hopefully that should resolve your problem.

---

### Post by herbster on 2008-04-11
I wouldn't recommend EsounD. You should get an ~/.asoundrc file going that manages the mixing and outputs much better.

Which soundcard do you have? Also paste the output of:

```
lspci
```

---

### Post by L1nux01D on 2008-04-11
Here goes my **lspci**

> 00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
**_00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)_**
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:08.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)


Should I try to Install **libesd-alsa**?

---

### Post by herbster on 2008-04-11
Go ahead give it a shot. You'll want to try System > Preferences > Sound afterwards and fiddle with the outputs and testing, as well as trying to play different apps at once of course.

If it doesn't work right we can go the asoundrc route.

---

