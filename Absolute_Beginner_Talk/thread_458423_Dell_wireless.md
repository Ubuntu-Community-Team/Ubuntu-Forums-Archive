---
title: "Dell wireless"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by wil313 on 2007-05-29
Ok, I am trying to get an internet card working, I did the lspci (sp?) and it says that it is showing up... But I don't think its working... This is what I got:

wil@wil-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by DJ Wings on 2007-05-29
It's a Broadcom... Broadcoms have had a history of not working with Linux, but there *is* a workaround. I don't have it, but someone else will probably post it soon.

---

### Post by wil313 on 2007-05-29
Its not too technical is it?

---

### Post by Ek0nomik on 2007-05-29
Just search the Ubuntu forums for support on your wireless card.  There are a lot of HOWTO's.

This one may help you:

[http://ubuntuforums.org/showthread.php?t=340689&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=340689&highlight=BCM4306)

---

### Post by DJ Wings on 2007-05-29
[Here's another one I found](http://ubuntuforums.org/showthread.php?t=201902&highlight=bcm4306)

---

### Post by Ek0nomik on 2007-05-29
If you need help just make a post in the thread you are following and someone will probably help.

Those wireless threads are very heavily watched and responded to.

---

