---
title: "hp pavillion dv6000 wireless problems (Intel)"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by Ronaldbain99 on 2007-11-22
Alright.  I don't know what the problem is here because my version has the intel wireless card (most others use broadcom from what I hear) and it has decided not to work...at all...

I've been having so many problems with this laptop since I bought it even when I had Vista installed.  I don't know if it is a hardware problem or not, but I'm just getting tired of having to use an ethernet cable to connect every time.  Help?

---

### Post by Arthur Archnix on 2007-11-22
A few questions for you:

Hardware related:
1. Did wireless work in Vista, and do you still have Vista installed?
2. Your laptop probably has a manual switch to physically turn it off and on. On HP laptops it can be difficult to tell, but on many it will glow blue when it is on. 
3. Can you post the output of lspci and wrap it in code tags, the # in the formatting tab.
```
lspci
```

Ubuntu stuff, Assuming its not a hardware problem:
1. Have you double checked your router settings, making sure, for example, that you are able to access the wireless with a good password, known mac address, etc.
2. Do you see the network manager applet in the top right corner of the screen? Clicking on that should give you a list of wireless networks available. If it doesn't Right-click on it and make sure that networking and wireless are both checked.

---

### Post by Ronaldbain99 on 2007-11-22
```
ron@ron-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
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
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
05:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

```

The wireless card worked on Vista just fine.  I've formatted everything to accept the signal from a wireless router.  I'm at my Sister's house right now and I get a signal from hers and am unable to use it.  There is no encryption key.

---

### Post by spiderbatdad on 2007-11-22
with no encryption key it should not be too hard, but for some reason it may take two or three attempts at configuring. Right click on the network monitor and make sure wireless is enabled. Then, left click and select manual configuration. Select the wireless mode and go to properties. De-select roaming mode and enter the network name by choosing it from the drop-down arrow. Then under network configuration use the drop-down arrow to select DHCP. Hope it helps. You may have to go through enabling wireless a couple of times and even making sure any other wireless networks listed are not eneabled as roaming.

---

