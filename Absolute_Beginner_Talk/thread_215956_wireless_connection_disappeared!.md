---
title: "wireless connection disappeared!?"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by da1nonlymikeo on 2006-07-14
im trying to set up my wpc54g wifi card in my laptop and not when i go to my network settings all i have is ethernet connection, and modem connection. where is my wireless connection (eth1) ??

 can anyone help me out? thanks

---

### Post by Kobalt on 2006-07-14
I also have a WPC54G card, I got it to work really easily. What version of the card is it ? It can be a ver.2 , ver.3 ...
Your wireless connection is not named as eth1, it should be named wlan0 or wlan1...
Try typing iwconfig in a console and give us the result.

---

### Post by Jagot on 2006-07-14
> **Kobalt said:**
> Your wireless connection is not named as eth1, it should be named wlan0 or wlan1...

I don't have the same card -I have a Broadcom 4318- but just thought I'd say that I enable mine with ndiswrapper and it is down as eth1, with my NIC down as eth0, so it may well be the case.

---

### Post by da1nonlymikeo on 2006-07-14
hmm well i have a ver.3 card and the iwconfig is...
 
 mike@mike-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

 dosent look to good lol

---

### Post by Kobalt on 2006-07-14
Argh :( My card is a ver.2 with an acx chipset, I don't know if the ver.3 is still using that same chip... You can know that by typing lspci in a console and read the description of your wifi card.
Have you tried to type ifup wlan0, or eth0... ?

---

### Post by da1nonlymikeo on 2006-07-14
mike@mike-laptop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)0000:00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)0000:00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)0000:00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02)0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0000:02:03.0 CardBus bridge: Texas Instruments PCI1420
0000:02:03.1 CardBus bridge: Texas Instruments PCI1420
0000:02:04.0 Communication controller: Agere Systems LT WinModem (rev 02)
0000:02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller (rev 42)
0000:02:09.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
0000:03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)



thats what i get for lspci. and by typing ifup and so on, i dont understand what you meen by typeing them. like just in a term?

---

### Post by Kobalt on 2006-07-14
Yes I mean in a terminal (console is in french, sorry :) ). It should activate the networking interface chosen (eth1 if you type this, etc.)
The chip of your card is a broadcom (BCM4318 ) apparently, and I believe this one works with ndiswrapper. Unfortunately for you I didn't have to use it to get my card working so I don't know anything about it...

---

### Post by Kobalt on 2006-07-15
Hi ! 
I don't know if you solved your problem yet, but just so you know, there is a HowTo on the forum on configuring and troubleshooting your WiFi card. I think it can be useful to you. Here you go : 
[http://www.ubuntuforums.org/showthread.php?t=197102]("http://www.ubuntuforums.org/showthread.php?t=197102")

Cheers !

---

