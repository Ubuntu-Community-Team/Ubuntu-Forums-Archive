---
title: "No Internet on Ubuntu 12.04"
date: 2012-05-07
forum: Apple Hardware Users
---

### Post by Delta 397 on 2012-05-07
I installed Ubuntu 12.04 on my Macbook Pro 8,1 and I have no Ethernet connection to the internet or wireless for that matter. Here is info on my Mac.

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Universal Host Controller #5 (rev 05)
00:1a.7 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Universal Host Controller #1 (rev 05)
00:1d.7 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe (rev 10)
02:00.1 SD Host controller: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader (rev 10)
03:00.0 Network controller: Broadcom Corporation BCM4331 802.11a/b/g/n (rev 02)
04:00.0 FireWire (IEEE 1394): LSI Corporation FW643 PCI Express 1394b Controller (PHY/Link) (rev 08)

```


here is the output of "lspci -nnk".

```
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
	Subsystem: Apple Inc. Device [106b:00db]
	Kernel driver in use: agpgart-intel
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:01.1 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0105] (rev 09)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
	Subsystem: Apple Inc. Device [106b:00db]
	Kernel driver in use: i915
	Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
	Subsystem: Intel Corporation Device [8086:7270]
	Kernel driver in use: mei
	Kernel modules: mei
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Universal Host Controller #5 [8086:1c2c] (rev 05)
	Subsystem: Intel Corporation Device [8086:7270]
	Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
	Subsystem: Intel Corporation Device [8086:7270]
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
	Subsystem: Intel Corporation Device [8086:7270]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Universal Host Controller #1 [8086:1c27] (rev 05)
	Subsystem: Intel Corporation Device [8086:7270]
	Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
	Subsystem: Intel Corporation Device [8086:7270]
	Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 05)
	Subsystem: Intel Corporation Device [8086:7270]
	Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 05)
	Subsystem: Intel Corporation Device [8086:7270]
	Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
	Subsystem: Intel Corporation Device [8086:7270]
	Kernel modules: i2c-i801
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
	Subsystem: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4]
	Kernel driver in use: tg3
	Kernel modules: tg3
02:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
	Subsystem: Broadcom Corporation Device [14e4:0000]
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci
03:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
	Subsystem: Apple Inc. AirPort Extreme [106b:00d6]
	Kernel driver in use: bcma-pci-bridge
	Kernel modules: bcma
04:00.0 FireWire (IEEE 1394) [0c00]: LSI Corporation FW643 PCI Express 1394b Controller (PHY/Link) [11c1:5901] (rev 08)
	Subsystem: LSI Corporation Device [11c1:5900]
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci
mitch@mitch-Ubuntu:~$
```

---

### Post by carl4926 on 2012-05-07
You started a new thread on this?!

Can you tell everyone if this is a new install, by that I mean clean, not an upgrade?
Did the wired ethernet work on the live CD (I would expect it to)

---

### Post by Delta 397 on 2012-05-07
I was given the advice to move it to the Apple section.  Also yes it is a new install and yes the ethernet worked fine on the live cd.

---

### Post by carl4926 on 2012-05-08
> **Delta 397 said:**
> I was given the advice to move it to the Apple section.  Also yes it is a new install and yes the ethernet worked fine on the live cd.

If it worked on the live CD, then it should work once installed. Unless the problem is as a result of an update. If you are connected to the internet during install, some updates will be installed, which could mean dead internet once the install completes and it reboots. Or it may be after that, once you have the new install running and do updates proper that you get the problem.
At the grub boot menu, if you boot the previous kernel, that's the one it was released with, does the ethernet work with that?

---

### Post by smurphy on 2012-05-08
If you know your network, delete all network configurations in the Network Manager, and create a new one, where you configure the IP's statically. worked for me. I suspect a bug in the network-manager (Running on a Mac Mini here).

---

### Post by mode7 on 2012-05-10
I don't know about ethernet. I have not used it once on my MBP81.
The wireless will not work because the b43 firmware is missing.

I personally used the wireless dongle from my desktop to install these. Without that or ethernet, you may need to manually install the firmware yourself.

If you can get access to the internet somehow, the b43-firmware-installer package will do it for you.
I also recommend you add the mpodroid/mactel ppa, so you can get the macfanctld daemon, and any possible wireless updates.
Anyways, if you install the firmware-b43-installer package, it will do the firmware stuff for you. It needs internet access to download from Broadcom, so you can't manually install this package offline.

For offline install, try this:
[http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html](http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html)
I haven't tested this on Precise, but it worked for me on Oneiric, and you should be good to go if you download everything to a pendrive. 
(***SKIP EVERYTHING related to compat-wireless on this page***. The latest kernel already has support for b43, you ONLY need the firmware files!!!)

---

