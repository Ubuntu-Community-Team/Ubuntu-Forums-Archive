---
title: "Question on configuring MBP 5-2 for use with Jaunty"
date: 2009-07-30
forum: Apple Hardware Users
---

### Post by swarup on 2009-07-30
I am using the [wiki]("https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty") for configuring my MBP with Jaunty. After it says how to set the repositories and instructing to install a few things, it then shows the following, with no instructions as to what to do with it. Is there something I need to *do* in accordance with the following?

> PCI Devices

```
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 9400M (rev b1)
04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
05:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 06)
```

---

### Post by justinlawrence on 2009-09-17
I'm having the same problem.

---

### Post by buntuLo on 2009-09-17
it's only the list of recognised PCI devices, nothing to do with it.
except enjoying the considerable lenght of the list :~)

---

### Post by amd-64 on 2009-09-17
These are the specs of your hardware. You can generate this by the command lspci
which lists pci devices. You will want to try this command because if a device is not recognized by your OS, it will be shown as unknown and the OS will not know what module to use to control it. 

I like using lshw-gtk to view the devices. It is graphical and more organized. If it is not on your system, you may want to  install it.

---

