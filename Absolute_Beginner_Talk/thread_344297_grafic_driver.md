---
title: "grafic driver"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by kakarot on 2007-01-22
need to instal grafics driver, plz tell me how...

Specs:
dont know any thing more detailed than that it is an intergrated graphics card

---

### Post by taurus on 2007-01-22
Post the output of this command from a terminal but chances are it would be one of those Intel graphic controller things.

Applications -> Accessories -> Terminal
```
lspci
```

---

### Post by kakarot on 2007-01-23
0000:00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Co ntroller/Host-Hub Interface (rev 01)
0000:00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G] /GE Chipset Integrated Graphics Device (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4 -M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EH CI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interfa ce Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev  01)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus  Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH 4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:01:05.0 Modem: Motorola: Unknown device 3052 (rev 04)
0000:01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01 )

---

### Post by pay on 2007-01-23
It should already be built into the kernel with edgy but to enable 3d video you need to add an option to your xorg.conf```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
sudo nano /etc/X11/xorg.conf
```Find the part that says Section "Device" and add ```
Option "XAANoOffscreenPixmaps" "true"
```And at the end (or anywhere really) add ```
Section "Extensions"
Option "Composite" "true"
EndSection
```

---

### Post by zgornel on 2007-01-23
Do a "glxinfo". You should se : Direct Rendering: YES. Also, check the 3D driver being used (Mesa something ...). The changes that pay suggested are to be done if you intend on installing a composite window manager like beryl or compiz.

---

