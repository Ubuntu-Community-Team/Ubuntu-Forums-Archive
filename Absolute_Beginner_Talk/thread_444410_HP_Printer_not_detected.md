---
title: "HP Printer not detected"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by stalbot on 2007-05-15
Hi,

I have an HP Deskjet 5550 printer. I've installed and ran HPLIP but my printer is not detected. My printer in connected using a Dynex LPT to USB cable. I've tested the port with other devices and it works. I've tested the printer in other ports and it does not work.

I've search the forum and found the hp-check command. Here is the error message I received:

DeskJet-5550
------------
Device URI: parallel:/dev/lp0
Installed in HPLIP? No
PPD: /etc/cups/ppd/DeskJet-5550.ppd
PPD Description: HP DeskJet 5550 Foomatic/hpijs (recommended)
Printer status: printer DeskJet-5550 is idle.  enabled since Tue 15 May 2007 10:54:34 AM EDT

error: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP. (You can still print to this printer using another backend and HPIJS.)

Any ideas anyone?

---

### Post by Kobalt on 2007-05-15
Have you installed your printer in System > Admin. > Printing before running HPLIP ?

---

### Post by stalbot on 2007-05-15
I found that my problem is not with my printer.

I'm using a Dynex parallel to usb cable. ([http://www.dynexproducts.com/pc-196-2-dynex-6-usb-parallel-printer-cable.aspx](http://www.dynexproducts.com/pc-196-2-dynex-6-usb-parallel-printer-cable.aspx))

My printer is not recognized because of this cable. I tried using my old parallel cable and it worked fine.

I searched for linux drivers to install my cable but I can't find nothing.

Any ideas

---

