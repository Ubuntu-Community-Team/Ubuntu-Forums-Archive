---
title: "Dell Inspiron 6000 Wireless Issues"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by lague1317 on 2007-08-15
Hey all,

I'm new to all this and just installed Ubuntu on my Dell Inspiron 6000 Laptop with an Intel Pentium M processor and Intel PRO/Wireless 2915ABG Network Connection.
I can't seem to get my wireless working.. I read through a bunch of the previous posts on how to do it but I still can't seem to get it working.. And also my wireless LED doesn't work properly-- If there's a way to get that working, not only so it turns the wireless on/off but also so it actually shows with the LED.

Any help would be awesome.
Thanks a lot.

---

### Post by overdrank on 2007-08-16
> **lague1317 said:**
> Hey all,

I'm new to all this and just installed Ubuntu on my Dell Inspiron 6000 Laptop with an Intel Pentium M processor and Intel PRO/Wireless 2915ABG Network Connection.
I can't seem to get my wireless working.. I read through a bunch of the previous posts on how to do it but I still can't seem to get it working.. And also my wireless LED doesn't work properly-- If there's a way to get that working, not only so it turns the wireless on/off but also so it actually shows with the LED.

Any help would be awesome.
Thanks a lot.

HI and welcome it seems that this card has worked for many and then give some trouble. As for the led lights working I don't think that is important as the connection. If you could post the out put of the  command in the terminal 
```
lspci
```
Then terminal is located under applications, accessories. Then we can get some more info on the wireless card and maybe help.

---

### Post by lague1317 on 2007-08-16
This is everything that came out when I typed that in the terminal..

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
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)

---

### Post by overdrank on 2007-08-16
Ok I am by no means a networking guru but I found this link that may help and I see you have made another post in wireless and networking that may bring some more help.
[http://ubuntuforums.org/showthread.php?t=197451&highlight=PRO%2FWireless+2915ABG](http://ubuntuforums.org/showthread.php?t=197451&highlight=PRO%2FWireless+2915ABG)

---

