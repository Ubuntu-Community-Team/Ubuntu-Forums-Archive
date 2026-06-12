---
title: "[SOLVED] No sound"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Jake90 on 2008-01-16
Hi, I just upgraded from Feisty to Gutsy and now I have no sound at all. The sound worked fine in Gutsy. I'm a newbie so step by step would be nice. 
```
lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0531 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
```
Thanks

---

### Post by balaknair on 2008-01-16
Hello Jake
You need to provide a little more info
Could you open a terminal(Applications menu> Accessories> Terminal) and paste the following command
```
aplay -l
```
and post the output here.

---

### Post by Jake90 on 2008-01-16
> **balaknair said:**
> Hello Jake
You need to provide a little more info
Could you open a terminal(Applications menu> Accessories> Terminal) and paste the following command
```
aplay -l
```
and post the output here.

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by balaknair on 2008-01-16
OK, the steps outlined in this thread worked for someone else with the Conexant card
[http://ubuntuforums.org/showthread.php?t=455147](http://ubuntuforums.org/showthread.php?t=455147)

You should try that
All the best

PS: if it works for you, please post a reply here and mark the thread as solved.
bye

---

### Post by Jake90 on 2008-01-16
Thanks it worked!!

---

### Post by balaknair on 2008-01-16
Glad to be able to help
have fun

---

