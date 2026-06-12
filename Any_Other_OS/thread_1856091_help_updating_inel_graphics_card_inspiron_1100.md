---
title: "help updating inel graphics card inspiron 1100"
date: 2011-10-07
forum: Any Other OS
---

### Post by Tankster399 on 2011-10-07
sudo lspci i got 

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

and for sudo lspci -v | less i got this
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
        Flags: bus master, fast devsel, latency 0
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
        Subsystem: Dell Device 0149
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Memory at f6f80000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>
        Kernel modules: i915

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
        Subsystem: Intel Corporation Device 24c0
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at bf80 [size=32]
        Kernel driver in use: uhci_hcd
:

my current OS is Linux mint 9 lxe since its the only OS i can even install on this laptop besides lubuntu which i hate very much. How would i go on to installing the Intel graphics drivers so i can actually play games without my laptop blacking out. 

PS I'm only a beginner

---

### Post by Tankster399 on 2011-10-07
bump sorry but i need help badly anyone mind helping??

---

### Post by Toz on 2011-10-07
Can you post back the contents of your **/var/log/Xorg.0.log** and (if you have one) the **/etc/X11/xorg.conf** files? 

If you search this forum for this video chip you'll see many reports about poor performance. The intel drivers don't seem to perform well. Let's see if you've got the proper drivers and configs in place.

---

### Post by Perfect Storm on 2011-10-08
Moved to Other OS/Distro Talk.

---

### Post by T J Wells on 2011-10-20
I have a Dell Inspiron 1100 with 512 of ram and have had trouble with Ubuntu and other distros not liking the video card in this unit.  Ubuntu only uses 640 x 480 and has a ghost image.

I switched to Linux Mint Debian and it works well at 1024 x 768 resolution.  I switched on 10/19/2011.

---

