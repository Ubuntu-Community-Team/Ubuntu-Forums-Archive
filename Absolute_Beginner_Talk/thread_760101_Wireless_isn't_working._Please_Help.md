---
title: "Wireless isn't working. Please Help"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by Pasty-Flawss on 2008-04-19
Hey,

My wireless isn't working on ubuntu but it works on windows.

I am using a laptop Acer Aspire 5310.

My wireless card driver thingy is 802.11b/g WLAN i think..

Also my sound isn't working..

I think it's just a matter of downloading the right drivers but i don't know what im doing..

All help appreciated.

Thanks in advance :).

---

### Post by rbc on 2008-04-19
You are correct, it may be a driver issue. In terminal, type "lspci" to find out what wireless card you have, then post back

---

### Post by Pasty-Flawss on 2008-04-19
this is what the output was:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
06:00.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
06:00.1 Generic system peripheral [0805]: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
06:00.2 FLASH memory: ENE Technology Inc Unknown device 0720
06:00.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller

---

### Post by rbc on 2008-04-19
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

Here's your card. I was going to refer you here:[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported), but your card is not listed. Can you also type "lspci -nn" to see what chipset the card has

---

### Post by Pasty-Flawss on 2008-04-19
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
04:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
05:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
06:00.0 FLASH memory [0501]: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller [1524:0730]
06:00.1 Generic system peripheral [0805]: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller [1524:0750]
06:00.2 FLASH memory [0501]: ENE Technology Inc Unknown device [1524:0720]
06:00.3 FLASH memory [0501]: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller [1524:0751]

---

### Post by rbc on 2008-04-19
I found this post, leo_rockaway has the same card as you and got it working with fwcutter instead of ndiswrapper. Check his link at the end of what he posted

---

### Post by rbc on 2008-04-19
Sorry, forgot to include the link: [http://ubuntuforums.org/showthread.php?t=759962&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=759962&highlight=broadcom)

---

