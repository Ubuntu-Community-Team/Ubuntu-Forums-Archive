---
title: "I have no sound"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by smmalis on 2007-09-14
I just reinstalled ubuntu (i screwed up some stuff) and I have no sound.  I never had sound before, and need to fix this problem.  Everything looks right, volumes are up and everything.  I have an Asus M2V motherboard and am using the onboard sound chip.

---

### Post by lisati on 2007-09-14
Sometimes installing the updates can help.....

---

### Post by smmalis on 2007-09-14
I've installed every update.  I know that much.

---

### Post by StevenEpic on 2007-09-15
try this :D

[http://ubuntuforums.org/showpost.php?p=1191847&postcount=1](http://ubuntuforums.org/showpost.php?p=1191847&postcount=1)

---

### Post by Crafty Kisses on 2007-09-15
> **smmalis said:**
> I just reinstalled ubuntu (i screwed up some stuff) and I have no sound.  I never had sound before, and need to fix this problem.  Everything looks right, volumes are up and everything.  I have an Asus M2V motherboard and am using the onboard sound chip.

Make sure all the codecs and stuff are installed, you also might want to post the following output:
```
lspci
```

---

### Post by smmalis on 2007-09-15
lspci gives this:
```
00:00.0 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. VT3351 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6238
00:00.7 Host bridge: VIA Technologies, Inc. VT3351 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. [K8T890 North / VT8237 South] PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.1 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.2 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.3 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0193 (rev a2)
04:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
06:00.0 IDE interface: Marvell Technology Group Ltd. Unknown device 6121 (rev b1)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

```

I'll try that link and see if it works.

---

### Post by smmalis on 2007-09-15
After following the instructions in that guide, no luck.  aplay -l gives: 
```
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: ALC861VD Digital [ALC861VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
And alsamixer has nothing muted.

---

