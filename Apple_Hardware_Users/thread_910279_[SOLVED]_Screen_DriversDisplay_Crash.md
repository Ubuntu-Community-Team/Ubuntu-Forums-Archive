---
title: "[SOLVED] Screen Drivers/Display Crash"
date: 2008-09-04
forum: Apple Hardware Users
---

### Post by WinterWeaver on 2008-09-04
I decided to try a game from the repos. Cute little 3d game. When I quit the game, I saw my normal desktop, but artifacts appeared on the screen (funny colored lines). It flashed for a bit, and then the whole screen showed just a bunch of colored lines, and I couldn't see anything else on the desktop.

CTRL+ALT+backspace didn't work. So I restarted... It goes in now, but graphics acceloration doesn't work anymore (therefore no compiz), my default resolution is only 800x600, and I cannot change this.

I've tried to go to a virtual terminal (at the GDM screen) via, ctrl+alt+F1, and typded the whole sudo dpg-reconfigure -phigh xorg...something (cant remember now) ... but that failed and I got the message that it's not installed O.o...

Does anyone know how I can fix this?

I'm using a Macbook 3.1, with Hardy
here is the output of lspci
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
04:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

```

Thanks

WW

---

### Post by cyberdork33 on 2008-09-04
> **WinterWeaver said:**
> I've tried to go to a virtual terminal (at the GDM screen) via, ctrl+alt+F1, and typded the whole sudo dpg-reconfigure -phigh xorg...something (cant remember now) ... but that failed and I got the message that it's not installed O.o...
Double-check your command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by WinterWeaver on 2008-09-04
I did, I tried it twice.

But I got everything fixed now. I was able to locate a previous xorg.conf file, replaced it with my current one, and then everything was fixed :)

Tx for your suggestion though

WW

---

### Post by cyberdork33 on 2008-09-04
> **WinterWeaver said:**
> I did, I tried it twice.

But I got everything fixed now. I was able to locate a previous xorg.conf file, replaced it with my current one, and then everything was fixed :)

Tx for your suggestion though

WW
You had a typo is why I suggested you try again. Glad to hear you got it all working though.

---

