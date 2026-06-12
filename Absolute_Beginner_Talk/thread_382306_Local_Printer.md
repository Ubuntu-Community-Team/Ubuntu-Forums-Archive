---
title: "Local Printer"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by luke411 on 2007-03-11
This is strange, but I'm running 6.1 and after I completed the last round of updates, to include the patch for the savings time change, I can no longer get a local printer to be detected, via usb.

I originally could plug into my Brother 1440 Laser Printer that is on another machine and print no problems. But I can no longer do that. When I tried to remove the printer and re-add it, I could not get it to be detected. So, tonight I tried adding a local Epson 820 I had lying around and same thing, it tells me no printer is detected.

I can add network printers but that won't work for me. Any  ideas on what might be broken? Oh, I should add that when I try to add a local printer by specifying a port, and not detecting one, I cannot change the port number. It's inop and there's no way for me to select one.

Could it be the printer wizard that is broken and maybe I need to re-install it? Also. I think I used to get prompted for my su password when I added a printer but it no longer does that either. Now it just lets me into printer settings but only allows me to add network printers. If it's the printer wizard, does anyone know the name of it so I can try to reinstall it?

---

### Post by compiledkernel on 2007-03-12
Memory serving correctly, the ML series samsungs have their own proprietary driver. 

Here is the LP.org page -- [http://openprinting.org/show_printer.cgi?recnum=Samsung-ML-1740](http://openprinting.org/show_printer.cgi?recnum=Samsung-ML-1740)

I assume you have the printer setup already. Did you compile the above mentioned driver?

---

### Post by ramjet_1953 on 2007-03-12
Did you try navigating to: System>Administration>Printing and then double click on New Printer.

It should do a scan for any new printer and find it, if it is plugged in and switched on.

If it detects your printer, just follow the prompts.

If it doesn't detect the printer, you may want to visit this site : 

[http://www.linuxprinting.org/printer_list.cgi](http://www.linuxprinting.org/printer_list.cgi)

Regards,
Roger :cool:

---

### Post by luke411 on 2007-03-12
As I said, the gnome-cups-manager does not detect the printer. It's not a driver issue, as I can add the printer as a network printer but cannot add it as a local printer. The Open Printer Data-base only tells me what I already know, that the printer works great right out of the box, which it did for me as well, until recently.

I did install the Foomatic Gui tool which DOES detect the printer and allows me to add it but still will not allow me to print. It spools the test page but will not print it. 

I guess I'll just keep playing with it and if I can figure it out, I'll post it here.

---

### Post by luke411 on 2007-03-12
The problem is some updated library files. If anyone has the same problem, the thread and the fix can be found here.

[http://ubuntuforums.org/showthread.php?t=380336](http://ubuntuforums.org/showthread.php?t=380336)

---

