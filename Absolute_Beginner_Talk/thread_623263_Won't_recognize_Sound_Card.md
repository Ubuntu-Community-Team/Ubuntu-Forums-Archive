---
title: "Won't recognize Sound Card"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by hotrod1 on 2007-11-25
Well I installed Ubuntu yesterday and right now I cannot use my sound card because it will only recognize my onboard sound and my USB headset but I tried following some guides on the forums to help install the Creative Sound Blaster Gamer card that I have but it still will not recognize it and I am new to Linux but experienced at Windows so sorry if I cannot describe everything right now but I apreciate all the help I can get, thanks.

---

### Post by Rowdy73 on 2007-11-25
No drivers available for it, i have the Creative Labs Sound Blaster X-Fi sound card and learned from the alsamixer site that it's not supported for Ubuntu/Linux use. :(

---

### Post by hotrod1 on 2007-11-25
Oh but is there at least a workaround so that I can use my sound card some other way?

---

### Post by Rowdy73 on 2007-11-25
> **hotrod1 said:**
> Oh but is there at least a workaround so that I can use my sound card some other way?

Let me know if there is, (if you find out before i do).

---

### Post by hotrod1 on 2007-11-28
No sorry I couldn't find anything but hopefully someone else can find something.

---

### Post by hotrod1 on 2007-12-02
Anybody? bump bump

---

### Post by Daveth on 2007-12-02
your gamer is supported, at least in part, under ALSA, so that's a start

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

what does this in a terminal give ?

```
lspci
```

this should demonstrate whether the system recognises it or not.

---

### Post by hotrod1 on 2007-12-04
Yes it does recognize it and this is what I get, sorry for the delayed response. 

```
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:05.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GT] (rev a1)
04:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
05:06.0 Multimedia audio controller: Creative Labs SB X-Fi
05:07.0 Ethernet controller: Macronix, Inc. [MXIC] MX987x5 (rev 25)
05:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

```

---

### Post by hotrod1 on 2007-12-07
Bump bump

---

