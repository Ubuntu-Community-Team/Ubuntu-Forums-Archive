---
title: "This is all a little bit overwhelming"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2007-11-03
It looks like right out of the box I did some things pretty wrong. I must have misunderstood how the whole partition thing works because my I seem to have lost my windows install completely. Whatever, no big deal, but I would like some advice on getting the wireless card in my year and a half old compaq presario V2000 with AMD Turion to work. I have tried searching the forums but I appear to be more of an absolute beginner then most of the other absolute beginners. I didn't think it was going to be that big a deal if something didn't work because my intent was to be able to boot to windows in a pinch but well....

---

### Post by alwiap on 2007-11-03
what is your wireless card model?

---

### Post by boriquajake on 2007-11-03
Wow, thank you for responding. If I were in Windows I would probably go to the device manager or something and be able to look up my wireless card model. How do I do that in Linux? Should I go online and look up my lappy model?

---

### Post by alwiap on 2007-11-03
being a linux newbie myself, there's probably a better way to doing it, but if you type:
```
lspci
```
in the terminal and paste the output here i think we can see what type it is.

p.s. the terminal if you didn't know is located in Applications > Accessories > Terminal

---

### Post by Maestro23 on 2007-11-03
> **boriquajake said:**
> Wow, thank you for responding. If I were in Windows I would probably go to the device manager or something and be able to look up my wireless card model. How do I do that in Linux? Should I go online and look up my lappy model?

System>>Prefs>>Hardware Info

or in Command LIne (Terminal)

> lspci

---

### Post by boriquajake on 2007-11-03
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


Sorry for dissapearing. I didn't expect to be answered so soon. ;-)

---

### Post by alwiap on 2007-11-03
try this link:
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by Maestro23 on 2007-11-03
Here's yours:

> 05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Now to get this bad boy up and running.  (Follow the link posted above).

---

### Post by boriquajake on 2007-11-03
Thanks, fellas. I appreciate the help.

---

