---
title: "[SOLVED] Visual effects wont work, at all"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by JimBuntu on 2007-11-02
I have Ubuntu Studio Gutsy and I can not get the visual effects to work at all. I have tried to download the Compiz packages (everyone i could find) and nothing works. Anyone know why?

---

### Post by overdrank on 2007-11-02
> **JimBuntu said:**
> I have Ubuntu Studio Gutsy and I can not get the visual effects to work at all. I have tried to download the Compiz packages (everyone i could find) and nothing works. Anyone know why?

Hi and have you enabled the restricted drivers or installed the drivers for your graphics card? Also what model of graphics card is in the system?

---

### Post by JimBuntu on 2007-11-02
I don't have an actual graphics card, its "integrated" with "up to" 64 MB of shared video memory. Could this simple thing be the problem?

---

### Post by JimBuntu on 2007-11-02
When i go to System>Preferences>Appearances and try to put it on normal, it says "Desktop effects could not be enabled".

---

### Post by overdrank on 2007-11-02
> **JimBuntu said:**
> I don't have an actual graphics card, its "integrated" with "up to" 64 MB of shared video memory. Could this simple thing be the problem?

Yes and do you know the chipset? The command ```
lspci
``` in the terminal will give that info on the graphics.

---

### Post by JimBuntu on 2007-11-02
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:0b.0 Communication controller: Agere Systems LT WinModem (rev 02)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:0d.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)

---

### Post by overdrank on 2007-11-02
Ok you may search synaptic manager for intel and then install the drivers and the 915 resolution. Then you can make sure that your xorg shows you are using the i810 driver with this command ```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by JimBuntu on 2007-11-03
this looks like spanish to me but ill try.

---

### Post by overdrank on 2007-11-03
> **JimBuntu said:**
> this looks like spanish to me but ill try.

That is strange, it looks Greek to me! ;)

---

