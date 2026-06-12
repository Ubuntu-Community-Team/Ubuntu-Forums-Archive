---
title: "Pending:printer-stopped"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by jorn on 2006-02-03
Hi!
It's about my HP 1200 psc printer. USB.

The printer is detected automatically at:
Bus 002 Device 002: ID 03f0:2f11 Hewlett-Packard

It was working flawlessly until now. My son borrowed it and after setting it up again, I tried printing.

The printer-icon in the upper right corner it supplied with an exclamation mark after some seconds and nothing happens.

The same thing happend with another printer, so I don't think the printer is the problem.

Is it possible to print through terminal so I can get some important output?
What can I else do to solve my frustration.

Regards - Jorn

---

### Post by jorn on 2006-02-03
Ready: open device failed; will retry in 30 seconds...

OK. Here is the output from Properties>Status:
Paused: Unable to open USB device "usb://Hewlett-Packard/psc%201200%20series?serial=HU3A9FP08D8W": No such device

I am working on it.
Jorn

---

### Post by audax321 on 2006-02-03
I'd say try this (if you haven't already):

1. Go to System > Administration > Printing
2. Delete all instances of the printer and close the window.
3. In terminal: sudo /etc/init.d/cupsys restart
4. Reinstall the printer through System > Administration > Printing

If it still doesn't work, something is definitely not right. :)

---

### Post by jorn on 2006-02-03
Thanks!   I'm getting the same exclamationmark.

The output of:  sudo /etc/init.d/cupsys restart

* Restarting Common Unix Printing System: cupsd                         [ ok ]

Jorn

---

### Post by wrtrdood on 2006-02-03
There is a problem with persistent USB device assignments.  I believe it's a known bug being worked on for the newer kernels.  I always had problems with this when I disconnected the USB printer.  The only way I found to successfully resolve it was to remove the current printer definition then add it back.  Restart cupsd in between.  The simplest way to administer CUPS is to use a browser and enter http:\\localhost:631 to talk to the CUPS system directly.

---

### Post by jorn on 2006-02-03
I solved it. Somewhere while messing around I saw an output thad said something about permissions on Usb devices.

That was some days ago. When I worked at it at that time I wasn't succesful.
But now I went to : /dev/usb/lp0
and changed permission to 777 and my printer is working.

Thank you both for paticipating. Every post is helping me climbing up the steep learning-curve.

Jorn

---

