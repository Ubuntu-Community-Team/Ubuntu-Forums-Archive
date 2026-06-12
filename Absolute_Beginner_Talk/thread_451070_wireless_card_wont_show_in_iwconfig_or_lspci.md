---
title: "wireless card wont show in iwconfig or lspci"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by twistedneck on 2007-05-21
Netgear rangemax next (bcm43xx type).

plug into multiple pci slots.. thing wont show up period.  any idea? the last 'wireless n' card i returned at least showed up.



iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.


twistedneck@jcheck-123:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)

---

### Post by scurry7 on 2007-05-22
dmesg to see if the device was detected on boot.
dmesg | grep Wireless
dmesg | grep 802.11
dmesg | grep Netgear
or just dmesg and look through it all to see if you can see anything.
If it does not detect it try a usb device...???

---

### Post by DarkN00b on 2007-05-22
```
ifconfig
``` should list all network devices connected to your system.

Also have a look at ```
lspci
```

---

