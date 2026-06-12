---
title: "Display issues with live CD"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by kiwit on 2006-03-19
I tried the AMD64 live cd and only parts of the desktop show up...when I scroll through the drop down menus, options only appear as I move through them...when I open the browser only small portions of the window appear.  I bought this computer with the hope of running linux on it, tried installing Suse 9.3, and got a very similar problem. Is it the embedded graphics on the motherboard?  I'm using an old NEC Multisync FE700 monitor if that makes any difference

512 MB DDR RAM
ECS 761GX-M754 
Sempron 3000+

I would really like to get this resolved as Ubuntu looks great (what I can see of it at least!)

Thanks

---

### Post by fimbulvetr on 2006-03-19
Can you post your:

```

lspci -vvv

```

(Run on cmd line)

and the contenets of /etc/X11/xorg.conf

---

### Post by kiwit on 2006-03-19
The display is too garbled for me to be able to see what is in the folder (unless I can also do that from the terminal?) but this is the response I got from the command line:

_____________

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge Control:
	I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL-fast >TAbort- <TAbort- <MAbort- >SERR- <PErr-

0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661FX/M 661FX/M661Mx/741/M741/760/M760 
PCI/AGP (rev 03) (prgo-if 00 [VGA])

Subsystem: Silicon Integrated Systems [SiS] [M]661FX/M661MX/[M]741/[M]760 PCI/AGP VGA Display Adapter

Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-

Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-

Interrupt: pin A routed to IRQ O
BIST result: 00
Region 0: Memory at d8000000 (32-bit, prefetchable) [szie=128M]
Region 1: Memory at febe0000 (32-bit, non-prefetchable) [size=128K]
REgion 2: I/O ports at 2800 [size=128]
Capabilities: <avaible only to root>

_________________

---

### Post by kiwit on 2006-03-19
I just managed to open xorg.conf...is there any particular part of that file that would be useful?  (I'm carrying my old lappie to and fro to type what the file says because the display on ubuntu is too corrupted to use for the internet)

---

