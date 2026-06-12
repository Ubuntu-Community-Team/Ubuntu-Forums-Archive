---
title: "Alright, it's time for some wireless help"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by siciliancasanova on 2007-03-17
So here's what's going on...

I just got into Ubuntu 6.10 a week ago.  Loved it, got all my hardware working but decided to just reinstall Ubuntu 7.04 (why not?)  I've seen a few minor bugs but nothing drastic and am enjoying the packaged programs (network manager for one) that are in this release.  

I'm attempting to install my Linksys WMP54GS a subsys of the Broadcom 43xx, (4318 to be specific)

I have gone in and removed ndiswrapper, blacklisted the 43xx drivers, reinstalled ndiswrapper, installed the bcmwl5 driver and here are my outputs...

lspci```
anthony@anthony-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:05.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
anthony@anthony-desktop:~$ 

```

iwconfig

```
anthony@anthony-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

anthony@anthony-desktop:~$ 

```

ndiswrapper -l

```
anthony@anthony-desktop:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present 

```

I would love to get this going, it's been a week now of rummaging through guides and such.  If someone could guide me from here, this is still new territory for me.

---

### Post by ZERO_SHIFT on 2007-03-17
try NDISWrapper

---

### Post by Fataltragedy2 on 2007-03-17
Seems like your hardware is functional but not configured due to the iwconfig response.

---

