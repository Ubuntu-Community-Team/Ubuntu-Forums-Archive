---
title: "Ubuntu not recognizing video card"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by Torqumada286 on 2008-01-04
I just got a new Radeon 3870 for my system.  Ubuntu is not recognizing it and loading the correct drivers.  Its using the generic VESA driver at the moment.  When I try to force it to use either the open or proprietary drivers it defaults back to the generic driver.  I am stuck at 800x600.  Any ideas how to fix the problem?

Torqumada

---

### Post by wolfen69 on 2008-01-04
try:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Torqumada286 on 2008-01-04
Sorry, but that didn't help.  In fact, the graphics are worse.  There has been a failure with GNOME now too.

Torqumada

---

### Post by Torqumada286 on 2008-01-04
When I do the the lspci command in returns the following:

> 00:00.0 Host bridge: ATI Technologies Inc RD580 [CrossFire Xpress 3200] Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
**01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9501**
01:00.1 Audio device: ATI Technologies Inc Unknown device aa18
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
03:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

It keeps saying unknown device.  It recognizes it as an ATI device, but not the type.

Torqumada

---

### Post by Torqumada286 on 2008-01-04
Anyone?

Torqumada

---

### Post by Torqumada286 on 2008-01-04
I guess I have stumped the experts.  Is there a prize for that?  :)

Torqumada

---

### Post by Torqumada286 on 2008-01-04
One more time.  Someone must have an answer.

Torqumada

---

### Post by shae on 2008-01-05
I am not sure that there are linux drivers for that video card yet.  If there are your best bet is to install the latest drivers from AMD's website.

---

### Post by barbedsaber on 2008-01-05
I am not reallt sure about this, but In the linux reality podcast, (which is really good), they suggest that if linux dosnt recognise your soud card, you should use a live cd from a distro with really good sound support. my point is, maybe trying a live cd from distro with good video card support, and pre loaded drivers, you copy the driver that it uses into the kernal that ubuntu uses,

I DO NOT KNOW IF IT WILL WORK
it probobly dosn't even make sense, so get someone who knows what they are talking about to sheck this post before you download open suse 10 or fedora or somthing.

---

### Post by oliviacond on 2008-01-05
the driver in the ubuntu repo is rather old, so the possible solution is to install the latest driver.

Guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
(Method 2)

---

### Post by Torqumada286 on 2008-01-05
[Actually, this thread mentions that the newer Radeons aren't supported fully.]("http://ubuntuforums.org/showthread.php?t=645974")  You can get some general functionality out of an open source driver, but not 3d functionality.  So I guess I am waiting until they do so.  :(

Torqumada

---

