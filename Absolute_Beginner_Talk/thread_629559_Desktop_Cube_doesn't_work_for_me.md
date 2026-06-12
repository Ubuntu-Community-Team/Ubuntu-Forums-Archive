---
title: "Desktop Cube doesn't work for me"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2007-12-02
I have been following some of the threads on this subject. (This one for example: [http://ubuntuforums.org/showthread.php?t=580723&page=5](http://ubuntuforums.org/showthread.php?t=580723&page=5))  I have gone to system, preferences, advanced desktop effects settings and enabled what it said to enable, but I am unable to get the cool cube thingey to appear. What am I missing?

---

### Post by overdrank on 2007-12-02
> **boriquajake said:**
> I have been following some of the threads on this subject. (This one for example: [http://ubuntuforums.org/showthread.php?t=580723&page=5](http://ubuntuforums.org/showthread.php?t=580723&page=5))  I have gone to system, preferences, advanced desktop effects settings and enabled what it said to enable, but I am unable to get the cool cube thingey to appear. What am I missing?

HI have you enabled the effects under system, preference, appearance, visual effects?

---

### Post by boriquajake on 2007-12-02
Holy crap, that is weird. I have been through this before but now when I go to enable desktop effects it says "desktop effects could not be enabled". Do you have any ideas?

---

### Post by schorsch on 2007-12-02
What graphic card do you use?

---

### Post by boriquajake on 2007-12-02
I am not sure. How can I tell? Is there some cool terminal command that will tell me?

---

### Post by overdrank on 2007-12-02
> **boriquajake said:**
> I am not sure. How can I tell? Is there some cool terminal command that will tell me?

HI and that command would be ```
lspci
```

---

### Post by jken146 on 2007-12-02
```
lspci
```

edit: Damn, too slow!

---

### Post by boriquajake on 2007-12-02
>  lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
05:09.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller


OK, what line tells me what I want?

---

### Post by boriquajake on 2007-12-02
Based on what others have said on this forum I know that my laptop is somewhat problematic. I was able to get advanced desktop effects enabled before but suddenly it no longer works.

---

### Post by fatality_uk on 2007-12-02
Make sure you have the right ATI drivers installed
Go here for some info about doing that.
[http://debianhelp.co.uk/ati.htm](http://debianhelp.co.uk/ati.htm)

Bear in mind this chipset probably isnt going to give you the full effects of Compix-Fusion

---

### Post by jken146 on 2007-12-02
> OK, what line tells me what I want?

```
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
```

---

### Post by boriquajake on 2007-12-02
> **fatality_uk said:**
> Make sure you have the right ATI drivers installed
Go here for some info about doing that.
[http://debianhelp.co.uk/ati.htm](http://debianhelp.co.uk/ati.htm)

Bear in mind this chipset probably isnt going to give you the full effects of Compix-Fusion


I gather that you are right. The thing is, I had the advanced desktop effects activated for a time. I could not set them to maximum but I could get the "normal" level to work. Now I can't, obviously I changed something but I don't know what.

---

