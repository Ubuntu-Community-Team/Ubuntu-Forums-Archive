---
title: "Epson Printer Won't Print"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Wingcommander on 2007-10-25
it worked on feisty, but since upgrade all print jobs show as "stopped".

the cups log shows version problems with the ppd and cups, but I can't work out how to fix it.

can any one help please?

(Epson R300)

---

### Post by alienexplorers on 2007-10-25
Did you select the Epson Photo R300?

---

### Post by Wingcommander on 2007-10-25
I suppose I asked for that .. :)

The printer is recognised in the USB port, I can select it in the set up, If I go to [http://localhost:631/admin](http://localhost:631/admin) I can change the drivers around and it shows as online and idle.

When i try and print a test page (or anything else), the printjob manager shows it as "stopped"

If I type 
tail -f /var/log/cups/error_log

I get ...

E [24/Oct/2007:16:00:06 +0000] [Job 75] Gutenprint: If the previous installed version of Gutenprint
E [24/Oct/2007:16:00:06 +0000] [Job 75] Gutenprint: was 4.3.19 or higher, you can use the `cups-genppdupdate.5.1'
E [24/Oct/2007:16:00:06 +0000] [Job 75] Gutenprint: program to do this; if the previous installed version
E [24/Oct/2007:16:00:06 +0000] [Job 75] Gutenprint: was older, you can use the Modify Printer command via
E [24/Oct/2007:16:00:06 +0000] [Job 75] Gutenprint: the CUPS web interface: [http://localhost:631/printers](http://localhost:631/printers).
E [24/Oct/2007:16:00:06 +0000] [Job 75] Gutenprint: The version of Gutenprint software installed (5.1.3) does not match the PPD file (5.0.1).
E [24/Oct/2007:16:00:06 +0000] PID 16283 (/usr/lib/cups/filter/rastertogutenprint.5.0) stopped with status 1!
E [24/Oct/2007:16:00:07 +0000] [Job 75] Job stopped due to filter errors.

which implies a mismatch of driver/cups manager, but i cannot for the love of Christ find anyone who knows anything about this.

---

### Post by Sak on 2007-10-26
I'm actually experiencing something similar with my Epson Stylus Color 580, although a bit more strange.  Note that this was my first attempt to print anything since upgrading to Gutsy in the last couple days, and I never had any problems in Feisty previously.

For me, I tried printing this one document (web.mit.edu/globalchange/www/MITJPSPGC_Rpt68.pdf).  It worked fine for the first 5 pages, and then suddenly stopped for no apparent reason.  I rebooted into WinXP and checked the ink levels, and they were fine.  After booting back into Gutsy, and trying to print the remaining pages the new job would show up in the print monitor with the "stopped" status.  

Oddly, though, in the Printer Configuration tool, I could still print a test sheet, have the printer clean the print heads, etc.  Then, I printed a completely different PDF document, and it printed just fine, but any time I tried to continue printing or even printing any single page or the entire document that hadn't finished, it always comes up as "stopped."  Finally, I downloaded Adobe Acrobat Reader and installed it from Adobe's website, and the document prints just fine.

So, is this a problem with Evince, the default PDF viewer in Gutsy?  Is it a CUPS problem, or something in between?

---

### Post by kekx on 2007-11-03
I have an Epson R800 and I had the same problem. What I did just cycling through the setting but now it prints. What probably resolved the problem is one of two thinks:
I changed the device location. Now it clearly shows Device URI: epson:/dev/usb/lp0 (the location I had before definitely does not indicate to USB device )and I also changed the Driver - Now I have Epson Stylus Photo R800 - CUPS+Gutenprint v5.0.1 (not the simplified) driver provided with Ubuntu.
So I'm lucky now. Now just need to figure out the best settings and apps to get best photoprint our of my R800.

---

