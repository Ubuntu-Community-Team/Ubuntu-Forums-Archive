---
title: "Whats my graphix card?"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-05-17
lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
05:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
05:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

---

### Post by compmodder26 on 2007-05-17
You have an Intel 945GM

---

### Post by carlosqueso on 2007-05-17
It's this one: ```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
```

That's an Intel graphics card.

---

### Post by mojo123 on 2007-05-17
can you give me that latest drivers for it (btw is it good :D?)

---

### Post by compmodder26 on 2007-05-17
You don't need to get any new from the internet.  They should be installed automatically by Ubuntu.  If you check your xorg.conf file, it should say "i810" for the driver in the "Device" section.  Is something not working properly for you?

---

### Post by mojo123 on 2007-05-17
no i just thought there might have been drivers for improvement, no problems.

---

### Post by icechen1 on 2007-05-17
> **mojo123 said:**
> can you give me that latest drivers for it (btw is it good :D?)

It is installed by default in Ubuntu,i have this card and Beryl desktop effects works fine so it is good.
If you have resolution problems,you will need 915resolution

---

