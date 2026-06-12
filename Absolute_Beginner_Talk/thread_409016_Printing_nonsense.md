---
title: "Printing nonsense"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Smitje on 2007-04-14
Hi fellow ubuntians

After Using Ubuntu (Edgy 64) for a couple of months now, with relatively little problems,  I'm dead stuck trying to get my printer to work.

I tried to follow some of the installation manuals out there, and sone programs, (after just adding a printer in the administration pannel ofcource) but nothing works. at first there was no reaction from the printer but after downloading pcl3 and the hpijs the printer now starts printing nonsense, whenever I send anything to it.

This Is a bit surprising, couse it is an old granddaddy of all printers the hp deskjet 510, it's been around for a while, and stil works fine in Wind#ws.

can annyone please help.

cheers 
Smitje

---

### Post by Legionox on 2007-04-14
Have you tried the djet500 driver? And try [this link]("http://openprinting.org/show_printer.cgi?recnum=HP-DeskJet_510")

---

### Post by 23meg on 2007-04-14
According to [this page]("http://hplip.sourceforge.net/supported_devices/inkjet.html"), your printer is of the DJ540 class; try selecting that printer and see if it works.

---

### Post by freebird54 on 2007-04-14
In my experience if a PCL printer prints nonsense, it has missed the initialization at the start of the print job.  This has happened from thesmallest to the largest of the HP style printers.  The fix I found on my system (using a PCL compatible from Panasonic) ws not the driver, but the printer port itself.

When you boot the machine, there will be a message similar to **"Press DEL to enter setup"** (or F1 or F10 or F12).  In the BIOS setup screens that show up next there will be an entry for the parallel port type.  Usually this will be set to ECP/EPP and will also have choice for those separately, or Normal or Centronics.  Setting this to normal, save and exit - and all should be well.

Assuming this was the problem of course :D

FIrst on MY list of fixes, anyway...

---

### Post by Smitje on 2007-04-14
Manny thanks to you all

I changed the lpt to normal in my bios and now it finally works.

it had to be sonething simple in the end, but I would not have found it without you guys.
thank you!

Cheers Smitje

---

