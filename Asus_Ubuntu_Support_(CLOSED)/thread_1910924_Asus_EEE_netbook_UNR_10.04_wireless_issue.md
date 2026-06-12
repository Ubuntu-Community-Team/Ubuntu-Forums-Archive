---
title: "Asus EEE netbook UNR 10.04 wireless issue"
date: 2012-01-18
forum: Asus Ubuntu Support (CLOSED)
---

### Post by jace10 on 2012-01-18
Hello all,

I was running easypeasy on my netbook just for the hell of it but i decided to make the switch over to ubuntu netbook remix because of several issues.  Anyway upon installing I hooked an ethernet cable up to install the proprietary driver for the wireless card, which went flawlessly, but for some reason my home wireless network wouldn't show up. I fooled around with it, doing the "sudo aptitude install linux-backports-modules-wireless-lucid-generic" and going into the bios to make sure wifi was enabled, but it has only gotten worse. Now when i right click on the connection thing in the upper right, I can't even check "Enable wireless", all it says is "Enable Networking" and "Enable Notifications", then connection information and the like.  Additionally, when I go to the hardware driver thing under system->administration it says the driver is "activated but not currently in use", and I dont see any buttons besides remove.  Please help me out, does 10.04 just not work with asus eee seashell series?  This netbook is kind of useless if I can't use the wifi haha. 

p.s. I had no problems with the wireless in easypeasy after installing the proprietary driver btw

cheers.

---

### Post by carl4926 on 2012-01-18
What device do you have

```
lspci -nnk
```

---

### Post by jace10 on 2012-01-18
Atheros Communications, here's the whole output:

"00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010] (rev 02)
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011] (rev 02)
    Kernel driver in use: i915
    Kernel modules: i915
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
    Kernel driver in use: uhci_hcd
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
    Kernel driver in use: ahci
    Kernel modules: ahci
01:00.0 Ethernet controller [0200]: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter [1969:1062] (rev c0)
    Kernel driver in use: atl1c
    Kernel modules: atl1c
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
    Kernel modules: wl
"

---

### Post by carl4926 on 2012-01-18
If you look here
[http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices](http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices)

Your device, which didn't report fully in the code
> 02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
    Kernel modules: wl

This part: 14e4:4727
Is listed near the bottom of that chart. And is poorly supported.
You may need to check that 'wl' is properly installed and matches your kernel
Or compile manually

---

### Post by jace10 on 2012-01-18
Ah I see. Thanks for the help!

---

