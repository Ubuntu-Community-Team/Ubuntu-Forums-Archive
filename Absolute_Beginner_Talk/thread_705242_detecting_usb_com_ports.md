---
title: "detecting usb com ports"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by crawall on 2008-02-23
how can i check if my usb com ports are working. I have just plugged a device in but don't get any reaction. I'm working with a dell latitude D505.

any suggestions
Alex

---

### Post by zabien1970 on 2008-02-23
open a terminal and enter lsusb  (list usb devices), also lspci will list pci devices connected

---

### Post by crawall on 2008-02-23
the lsusb command gives me this:
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0403:fc82 Future Technology Devices International, Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

lspci

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
01:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
01:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)


What all that...how do i know what to do to install the sonyericsson DSS25 usb cable connection?

---

### Post by zabien1970 on 2008-02-23
It appears its there:

Bus 002 Device 003: ID 0403:fc82 Future Technology Devices International, Ltd 

 What are you trying to accomplish?

---

### Post by Ivorydawn on 2008-02-23
Hi,

You should be able to find it  /dev/ttyUSB0, I had a problem with brltty grabbing mine but removing brltty(Which you probably don't need anyway) solved the problem.  My adapter used the same chipset as yours, the FTDI chipset. 

Have a look under /dev if you cannot see it remove brltty and see if /dev/ttyUSB0 appears.

Regards

Andrew

---

