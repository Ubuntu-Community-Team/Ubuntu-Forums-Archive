---
title: "Problems after installing Ubuntu 7.10 to my Compaq T3628UT"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by waggygee on 2007-12-20
I have intstalled Ubutnu 7.10 on to my compaq. All runs well except my internet... The wireless does not detect any networks at all. The wired connects to my router (and shows that it is connected, I am able to got through the routers settings and everything in the same way all the other computers in this network can) but I am not able to access my internet... I should mension that their is WEP security on my network, anyone know where I should enter the pasword?

---

### Post by shadow-of-sin on 2007-12-20
To get the wired internet to work, try disabling IPv6. There is a guide here:
[http://www.simonscullion.com/2007/11/20/ipv6-issues-with-ubuntu-710/](http://www.simonscullion.com/2007/11/20/ipv6-issues-with-ubuntu-710/)

As for wireless, what wireless chipset does your computer use? Type the following in the terminal and post your otuput:
```
lspci
```

---

### Post by waggygee on 2007-12-20
> **shadow-of-sin said:**
> To get the wired internet to work, try disabling IPv6. There is a guide here:
[http://www.simonscullion.com/2007/11/20/ipv6-issues-with-ubuntu-710/](http://www.simonscullion.com/2007/11/20/ipv6-issues-with-ubuntu-710/)

As for wireless, what wireless chipset does your computer use? Type the following in the terminal and post your otuput:
```
lspci
```

Sorry for taking so long to reply. Disabling the IPv6 worked. I am posting this using Ubuntu!
the out come of that command is as follows:

waggygee@waggygee-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
07:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

---

