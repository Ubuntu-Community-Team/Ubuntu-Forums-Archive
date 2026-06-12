---
title: "Graphic Card and Wireless Adapter"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by jake550 on 2007-10-18
Hi, 

I recently installed Ubuntu but have a couple of problems, my wireless adapter and my graphics card do not work...i have searched threads but cant find my graphics card in any of them and im very stuck. 

Graphics card; ASUS A9550GE top corner of the box says graphics by ATI

Wireless; Belkin 54g Wireless USB 

Any help on getting either of these to work would be great, im completely new to the linux environment so nothing too technical :confused:

Thanks

---

### Post by overdrank on 2007-10-18
> **jake550 said:**
> Hi, 

I recently installed Ubuntu but have a couple of problems, my wireless adapter and my graphics card do not work...i have searched threads but cant find my graphics card in any of them and im very stuck. 

Graphics card; ASUS A9550GE top corner of the box says graphics by ATI

Wireless; Belkin 54g Wireless USB 

Any help on getting either of these to work would be great, im completely new to the linux environment so nothing too technical :confused:

Thanks

Hi and welcome, please post the output of the command ```
lspci
``` 
In the terminal located under applications, accessories, terminal and this will identify your hardware and we may be able to help.

---

### Post by Pumalite on 2007-10-18
For ATI, try ENVY. For wireless, I hope this helps:

[http://www.linux.com/feature/56946](http://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

---

### Post by jake550 on 2007-10-19
Thank you all for the responses, here is the outcome when i typed the specified command...


-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: 
Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO]
 (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems 
[SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: 
Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller
 (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA 
(rev 01)
00:08.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 04)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd.
 RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: 
ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)
-desktop:~$

---

### Post by jake550 on 2007-10-19
bump

---

