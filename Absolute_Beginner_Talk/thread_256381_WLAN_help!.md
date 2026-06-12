---
title: "WLAN help!"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2006-09-12
I just bought a Compaq Presario 410 laptop and I can't figure out how to get the wireless card working.

Someone told me to type 'lspci' or something, and this is what comes up:

```
00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=AHCI (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
06:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
08:08.0 Ethernet controller: Intel Corporation Unknown device 1092 (rev 01)
```

Please help. I tried a couple WLAN tutorials, with like ndiswrapper, but I don't know what driver I need. I tried googling for the driver, but no luck. Anyone know what I need to get?


Thanks

---

### Post by DSn0wMan on 2006-09-12
I am not an expert, but it looks like you need some drivers for the following devices.

06:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
08:08.0 Ethernet controller: Intel Corporation Unknown device 1092 (rev 01)

I am guessing you have a broadcom wirless device.

---

### Post by kbsuperstar on 2006-09-12
What drivers do I need for a broadcom wireless device and how/where do I get 'em?

---

### Post by DSn0wMan on 2006-09-12
I would start by looking here.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I don't have a broadcom chipset, but I have seen many ppl on this forum that do. A little searching on broadcom, and WiFi should get you some good results.

---

### Post by kbsuperstar on 2006-09-13
I'll check it out and reply back. Thanks!

---

### Post by kbsuperstar on 2006-09-13
Ok, in the section 1.2.2.1. it says to download a driver and to extract the firmware parts. I downloaded bcmwl564.sys and extracted bcmwl564.sys and netbc564.inf . The tutorial then says to "install them to the correction location" and then goes on to the next section. Where exactly do I need to install these files and how do I go about doing that?


Please help, thanks

---

### Post by DSn0wMan on 2006-09-14
I am not sure, but if I were you I would start a new thread, and title it broadcom trouble or something like that. That way you will get the attention of ppl who have experience with broadcom problems.

Wish I could be of more help.

---

### Post by kbsuperstar on 2006-09-14
K, thanks

---

