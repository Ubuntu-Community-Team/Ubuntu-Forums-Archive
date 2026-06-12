---
title: "REALTEK AC97 Drivers"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by ryanchang on 2008-03-13
Hello,

I've looked at the other threads started about this, and I get to the compiling stage but then it lists me a bunch of errors...chkmod couldn't create the directory (something or other) and that it basically didn't work. I followed the instructions, but no avail. My sound is ****! any help is appreciated.

ryan

---

### Post by Oldsoldier2003 on 2008-03-13
> **ryanchang said:**
> Hello,

I've looked at the other threads started about this, and I get to the compiling stage but then it lists me a bunch of errors...chkmod couldn't create the directory (something or other) and that it basically didn't work. I followed the instructions, but no avail. My sound is ****! any help is appreciated.

ryan

what error are you getting when you compile?

---

### Post by ryanchang on 2008-03-15
I'm new to the terminal, so when the compiling stops, I've tried to copy some of the text but then it closes out. When it runs, I see a lot of chkmod errors, that it couldn't access the folder...I'll try again later today, I have work in about 40 minutes and I have to do other things before work.

---

### Post by FuturePilot on 2008-03-15
What sound card do you have? There may be an easier way.
Post the output of
```
lspci
```

---

### Post by gwarguy on 2008-03-15
I too am having trouble with my sound and figured i would post here instead of starting a new thread. 

the output of my lspci is

```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc R580 [Radeon X1900 XT] (Primary)
01:00.1 Display controller: ATI Technologies Inc R580 [Radeon X1900 XT] (Secondary)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

```

---

