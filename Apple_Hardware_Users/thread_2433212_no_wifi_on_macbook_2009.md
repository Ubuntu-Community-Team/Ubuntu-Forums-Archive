---
title: "no wifi on macbook 2009"
date: 2019-12-15
forum: Apple Hardware Users
---

### Post by c1henry on 2019-12-15
installed xenial on hard drive partition.  cant get it to recognize the internal wifi.

the output from lspci is: 

00:00.0 Host bridge: NVIDIA Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: NVIDIA Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: NVIDIA Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: NVIDIA Corporation MCP79 Co-processor (rev b1)
00:04.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: NVIDIA Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: NVIDIA Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: NVIDIA Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: NVIDIA Corporation MCP79 AHCI Controller (rev b1)
00:10.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: NVIDIA Corporation C79 [GeForce 9400M G] (rev b1)
04:00.0 FireWire (IEEE 1394): LSI Corporation FW533 [TrueFire] PCIe 1394a Controller (rev 07)

---

### Post by jeremy31 on 2019-12-15
Moved to Apple Hardware

---

### Post by gsahli on 2019-12-16
Your issue is most likely the broadcom chipset BCM43xxx. It requires a firmware install on every startup -- there is a ubuntu/debian package for that, that does the startup install.
Read here:
[https://www.linuxquestions.org/questions/linux-networking-3/ubuntu-16-04-mac-mini-2009-broadcom-driver-selected-and-wlan-enabled-but-home-network-does-not-show-4175600634/](https://www.linuxquestions.org/questions/linux-networking-3/ubuntu-16-04-mac-mini-2009-broadcom-driver-selected-and-wlan-enabled-but-home-network-does-not-show-4175600634/)
Or, search for BCM-43 installer

---

