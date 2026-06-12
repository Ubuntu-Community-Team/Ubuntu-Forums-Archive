---
title: "[SOLVED] Gateway MX7515 needs driver support"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by cmdrkeenkid on 2007-09-25
I just installed the Feisty Fawn build of Ubuntu on my Gateway MX7515 and I'm having a couple problems...

1.) The wireless won't work and I can't find much on getting it to work either.
2.) I got it to play mp3s, but I'm not hearing any sound from my speakers. I'm thinking that maybe the drivers aren't supported by it or something.

If anyone could lend me some advice that would be spectacular and greatly appreciated.

Thanks!

---

### Post by Maestro23 on 2007-09-25
What type of wireless card is inside?

---

### Post by overdrank on 2007-09-25
> **cmdrkeenkid said:**
> I just installed the Feisty Fawn build of Ubuntu on my Gateway MX7515 and I'm having a couple problems...

1.) The wireless won't work and I can't find much on getting it to work either.
2.) I got it to play mp3s, but I'm not hearing any sound from my speakers. I'm thinking that maybe the drivers aren't supported by it or something.

If anyone could lend me some advice that would be spectacular and greatly appreciated.

Thanks!

Hi if you could post the output of the command in the terminal 
```
lspci
```
The terminal is located  under applications, accessories, terminal. This will allow us to identify your wireless card and maybe help.

---

### Post by cmdrkeenkid on 2007-09-25
This is the information that I came up with...

> 
00:00.0 Host bridge: ATI Technologies Inc ATI Radeon Xpress 200 (RS480/RS482/RX480/RX482) Chipset - Host bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
03:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
03:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
03:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)


---

### Post by overdrank on 2007-09-26
> **cmdrkeenkid said:**
> This is the information that I came up with...


03:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
Hi this thread may help with your wireless
[http://ubuntuforums.org/showthread.php?t=197102&highlight=Broadcom+Corporation+BCM4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=Broadcom+Corporation+BCM4318)
As for you sound 
ATI Technologies Inc IXP SB400 AC'97 Audio Controller 
This link may help
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
Hope this helps and good luck!

---

### Post by cmdrkeenkid on 2007-09-26
Thank you all so much! I have both working sound and wireless now. :)

---

### Post by overdrank on 2007-09-26
> **cmdrkeenkid said:**
> Thank you all so much! I have both working sound and wireless now. :)

Great and good luck could you mark the thread as solved please
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)


:guitar:

---

