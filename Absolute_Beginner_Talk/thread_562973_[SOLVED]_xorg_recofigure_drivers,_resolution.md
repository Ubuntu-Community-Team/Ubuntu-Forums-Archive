---
title: "[SOLVED] xorg recofigure: drivers, resolution?"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by alexmoon on 2007-09-29
I'm sorry, I know the answer to this must be somewhere but I've checked the forums and google, and the posts that get suggested from my title, and I'm still stuck. I must be missing something because I'm tired and stressed. It would be great if someone could help me out by pointing me in the right direction.

I was trying to fix a thing, and did this:
 sudo dpkg-reconfigure -phigh xserver-xorg

But I screwed it up, and now I can't find the right drivers to use or the name of the backup version of xorg.config 
I would really appreciate it if someone could tell me how to do a search for previous versions of xorg.config, or tell me which drivers to use. The output of lspci is:
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI7510 PC card Cardbus Controller (rev 01)
02:01.1 CardBus bridge: Texas Instruments PCI7510,7610 PC card Cardbus Controller (rev 01)
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller
02:01.3 System peripheral: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)



The other issue that might be causing this problem is that when the option comes up for checking various screen resolutions, I can't work out how to check (or uncheck) any of the options - no idea which button does it. Again, I suspect I am missing something very obvious, but I have no idea what.

Thanks for helping me and if there's somewhere obvious I should have looked or information I should have included please don't hesitate to tell me.

---

### Post by forestpixie on 2007-09-29
firstly open a terminal and to find all the xorg.conf backups do this

```
ls /etc/X11/xorg*
```
if you've got a recent backup, or at least one you know works

```
 sudo mv nameofthebackup xorg.conf
```

secondly I've only used the reconfigure thing once myself, but I think I used it without -phigh? - but I think you either use tab or space to move to resolutions, and you can probably use the nv driver when asked - if that causes problems go for vesa 

IF you can get in with vesa - I'm sure the restricted driver will get the right one for that nvidia 

hope that helps you along - although I'm not sure about the restricted driver thing in 6.10 which I've just noticed

---

### Post by alexmoon on 2007-09-29
Thanks! I'd made too many failed attempts to have a usable backup, but the combination of nv plus 'space' to check resolution options sorted it out.

---

### Post by forestpixie on 2007-09-29
excellent - glad I could help out

can you mark thread solved for those about to have the same problem :)

---

