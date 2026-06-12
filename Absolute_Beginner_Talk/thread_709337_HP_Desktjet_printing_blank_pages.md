---
title: "HP Desktjet printing blank pages"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by MissingHorcrux on 2008-02-27
My printer is not printing pages correctly - they're all coming out blank. It's connected via USB port and worked fine on Windows XP. I heard there might be printer bugs in Gutsy, so I installed the printingbuginfo script, and here's what it gave me:

ProblemType: printingbuginfo v2.0: printingbug+localusb ([https://wiki.ubuntu.com/PrintingBugInfoScript](https://wiki.ubuntu.com/PrintingBugInfoScript))
CupsConfiguredDevices: device for PSC_1500_series: hp:/usb/PSC_1500_series?serial=MY55KB90NQ0498
CupsConfiguredPPDs: PSC_1500_series: HP PSC 1500 Foomatic/hpijs (recommended)
Date: Wed Feb 27 08:55:36 2008
DesktopEnvironment: GNOME
DistroRelease: Ubuntu 7.10
EtcPapersize: letter
InstalledPrintingPackages:
 ii  cupsys                   1.3.2-1ubuntu7.5         Common UNIX Printing System(tm) - server
 ii  cupsys-driver-gutenprint 5.0.1-0ubuntu8           printer drivers for CUPS
 ii  foo2zjs                  20070625-0ubuntu1.1      Support for printing to ZjStream-based printers
 ii  foomatic-db              20070919-0ubuntu3        OpenPrinting printer support - database
 ii  foomatic-db-engine       3.0.2-20070719-0ubuntu4  OpenPrinting printer support - programs
 ii  foomatic-db-hpijs        20070813-0ubuntu1        OpenPrinting printer support - database for HPIJS driver
 ii  foomatic-filters         3.0.2-20070719-0ubuntu1  OpenPrinting printer support - filters
 ii  ghostscript              8.61.dfsg.1~svn8187-0ubu The GPL Ghostscript PostScript/PDF interpreter
 ii  hpijs                    2.7.7+2.7.7.dfsg.1-0ubun HP Linux Printing and Imaging - gs IJS driver (hpijs)
 ii  hplip                    2.7.7.dfsg.1-0ubuntu5    HP Linux Printing and Imaging System (HPLIP)
 ii  libgnomeprint2.2-0       2.18.2-0ubuntu1          The GNOME 2.2 print architecture - runtime files
 ii  min12xxw                 0.0.9-1build1            Printer driver for KonicaMinolta PagePro 1[234]xxW
 ii  openprinting-ppds        20070919-0ubuntu3        OpenPrinting printer support - PostScript PPD files
 ii  pnm2ppa                  1.12-16                  PPM to PPA converter
 ii  pxljr                    1.1-0ubuntu1             Driver for HP's Color LaserJet 35xx/36xx color laser printers
 ii  splix                    1.0.1.1-0ubuntu2         Driver for Samsung's SPL2 (bw) and SPLc (color) laser printers
 ii  system-config-printer    0.7.75+svn1653-0ubuntu2  Printer configuration GUI
Locale: LANG=en_US.UTF-8, LC_CTYPE=en_US.UTF-8, LC_PAPER=en_US.UTF-8
Uname: Linux kelly-laptop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
UsbPrinterDevices: 
UsbPrinterIEEE1284Id: 
UsbPrinterKernelModules:
 usblp                  15104  0 
 usbcore               138632  8 usblp,wacom,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
lsusb:
 Bus 005 Device 003: ID 1058:0901 Western Digital Technologies, Inc. 
 Bus 005 Device 001: ID 0000:0000  
 Bus 003 Device 003: ID 03f0:4c11 Hewlett-Packard 
 Bus 003 Device 001: ID 0000:0000  
 Bus 004 Device 001: ID 0000:0000  
 Bus 001 Device 004: ID 056a:0015 Wacom Co., Ltd 
 Bus 001 Device 001: ID 0000:0000  
 Bus 002 Device 001: ID 0000:0000  

I'm rather new to Linux, so please keep that in mind if you have any advice to give me.
Thanks in advance, guys!

---

### Post by dstew on 2008-02-27
What printer do you have?

---

### Post by MissingHorcrux on 2008-02-27
> **dstew said:**
> What printer do you have?

HP PSC 1510, printer/scanner

---

### Post by dstew on 2008-02-27
That output all seems correct to me. Have you tried printing from different applications? How about printing a test page? It is probably some configuration problem, rather than a driver problem. That printer should work with the drivers you have installed.

---

### Post by MissingHorcrux on 2008-02-27
> **dstew said:**
> That output all seems correct to me. Have you tried printing from different applications? How about printing a test page? It is probably some configuration problem, rather than a driver problem. That printer should work with the drivers you have installed.

It works when printing from AbiWord, but OpenOffice Presentation still prints blank pages. I've got through all the Options and Preferences and everything, and I can't figure out why it would be doing this. :/ 
Printing docs is the most important - that's great I figured that out. But I'd like to be lazier in my classes and print out the presentations ahead of time... lol.

---

### Post by PeterJS on 2008-02-27
It might have to do with the default resolution and cartridge configuration. I've got a PSC1310, and it was printing out blank pages, until I changed the default print out mode. You can change the print out mode under System > Administration > Printing > Printer options. For mine the right setting was 600dpi, color, black + color, hopefully that will give you a starting point.

I started looking at that based on this post:
[http://ubuntuforums.org/showpost.php?p=3188623&postcount=4](http://ubuntuforums.org/showpost.php?p=3188623&postcount=4)

---

