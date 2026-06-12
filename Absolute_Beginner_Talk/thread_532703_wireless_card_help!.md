---
title: "wireless card help!"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2007-08-23
Im trying to get my wireless card to work but it says that its all working fine but it wont pickup my wireless internet connection and i have no other way of testing it :mad: so i did some terminal thing "lspci" and here is what i got back any help would be great:KS

```
carl@Kubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:01.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller
02:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
02:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller
02:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc:
02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
carl@Kubuntu:~$ 
```

---

### Post by Dave Crowhurst on 2007-08-23
[COLOR="SandyBrown"]How-To IPW2200: Getting Intel Pro Wireless 2200 BG to work on debian/ubuntu [/COLOR][http://www.debuntu.org/2006/03/27/9-how-to-ipw2200-getting-intel-pro-wireless-2200-bg-to-work-on-debian-ubuntu]("http://www.debuntu.org/2006/03/27/9-how-to-ipw2200-getting-intel-pro-wireless-2200-bg-to-work-on-debian-ubuntu")

Is that your network card?

---

### Post by kamitsukai on 2007-08-23
erm.....yes why?

---

### Post by kamitsukai on 2007-08-23
omg im a complete newb and all that comand line looks scary :(

---

