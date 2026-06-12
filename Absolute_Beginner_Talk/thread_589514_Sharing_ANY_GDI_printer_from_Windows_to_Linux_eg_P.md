---
title: "Sharing ANY GDI printer from Windows to Linux: eg Panasonic KB-MB271"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Mundu on 2007-10-24
This is useful for people with Windows GDI based printers such as my new and very affordable **Panasonic KX-MB271** Laser multi function printer that are **only supported in Windows **(XP etc). 

It appears that they cannot even be shared from Windows to Linux over Samba (Windows printer sharing).

However, I run into and implemented a nice solution using Ghostscript and Redmon so that **ANY printer **attached to Windows **can appear as a Postscript printer to Linux / Ubuntu**.

The ghostscript and RedMon software is installed and configured on your Windows box, **adding a virtual printer to Windows **that accepts Postscript and redirects it to the Windows attached GDI printer. Ubuntu Linux can then print to pretty much ANY unsupported printer.

I used the lastest versions of Ghostscript (8.60) and RedMon (1.7). GhostScript Viewer 4.8 is useful to confirm that Ghostscript can print to your Windows attached printer. I chose to emulate an HP Laserjet 5 PS, even though I dont have one.

The instructions I used are located at:

**[http://www.stat.tamu.edu/~henrik/GSPSprinter/GSPSprinter.html]("http://www.stat.tamu.edu/~henrik/GSPSprinter/GSPSprinter.html")**

It does take a little effort, but it does work.

Hope that information is useful to those who have "nice" printers that are unsupported by Ubuntu Linux.

---

