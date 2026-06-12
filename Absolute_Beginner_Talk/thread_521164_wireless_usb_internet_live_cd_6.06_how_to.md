---
title: "wireless usb internet live cd 6.06 how to?"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Hopeless on 2007-08-09
hi,

i am trying to get wireless USB internet working showing some possible new linux users to convert to Ubuntu... im usind live cd 6.06

i can find the USB device in devices but no internet????

what do i do....?

many thanks...

---

### Post by MenZa on 2007-08-09
Well, I'm not exactly sure if you can even install the necessary kernel modules, etc. in a LiveCD session, but you'd have to be more specific; what chipset are you using for your wireless card, etc.?

---

### Post by splintercellguy on 2007-08-09
Can you post the output of lspci from Terminal?

---

### Post by Hopeless on 2007-08-10
it says on the back of the modem:

Wireless LAN USB Dongle
(MW-1000USB) 
R-LARN-02-0135
802.11b 
Brandname: Nespot
The rest is in Korean...Also says WIFI if helps i dunno...

lspci:

ubuntu@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 12)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12)0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 12)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] (rev b2)
0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
ubuntu@ubuntu:~$

in windows it says:

MMC WaveCast USB Adapter

in Linux System > Admin > Network it dosent find the wireless device... so i guess the driver needs installing? ..Yes...No...?

hope that helps..

---

### Post by hopelessone on 2007-12-27
my firend wants to go linux...

but i can;t get his internet going...any ideas??

---

