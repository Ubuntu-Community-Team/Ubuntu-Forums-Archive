---
title: "Desktop wont fill entire screen"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Keva161 on 2008-02-04
Hi

Sorry if this is a dumb question but I got a new laptop at the weekend. A Toshiba Satellite U300-13U, came with Vista on it. Decided to try out Ubuntu and downloaded the image and installed it this evening.

Bit of a problem, the desktop only seems to take up 3 1/3's of the screen.

[http://img245.imageshack.us/my.php?image=desktopny1.png]("http://img245.imageshack.us/my.php?image=desktopny1.png")

Tried to re-size the screen res but just got a black screen :/

---

### Post by randy78 on 2008-02-04
> **Keva161 said:**
> Hi

Sorry if this is a dumb question but I got a new laptop at the weekend. A Toshiba Satellite U300-13U, came with Vista on it. Decided to try out Ubuntu and downloaded the image and installed it this evening.

Bit of a problem, the desktop only seems to take up 3 1/3's of the screen.

[http://img245.imageshack.us/my.php?image=desktopny1.png]("http://img245.imageshack.us/my.php?image=desktopny1.png")

Tried to re-size the screen res but just got a black screen :/

Just hold down CTRL+ALT and press BACKSPACE to restart the X server when your desktop comes up...

That should do the trick ;)

---

### Post by LowSky on 2008-02-04
what kind of video card does that thing have? You most likely need to enable the drivers for it first

---

### Post by jan quark on 2008-02-04
first have a look at the restricted drivers in the restricted drivers manager

system > administration > restricted

are there any inactive drivers ?

then pls post the result of 

```
lspci
```

---

### Post by Keva161 on 2008-02-04
> **jan quark said:**
> first have a look at the restricted drivers in the restricted drivers manager

system > administration > restricted

are there any inactive drivers ?

then pls post the result of 

```
lspci
```

Not that I can see. Im not sure on the graphics card but some Intel one I think.

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
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
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0a:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0a:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0a:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

---

### Post by Keva161 on 2008-02-04
My graphics are Intel GMA X3100. I think I read that Ubuntu has them already. How do I install them?

---

### Post by Keva161 on 2008-02-05
Bump

---

### Post by Keva161 on 2008-02-05
BUMP
Anyone? Im new to using this.

---

### Post by timbounceback on 2008-02-05
have you tried ctrl+alt+backspace?

---

### Post by Keva161 on 2008-02-06
> **timbounceback said:**
> have you tried ctrl+alt+backspace?

Yes, no difference.

---

### Post by Keva161 on 2008-02-16
Anyone?

---

