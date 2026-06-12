---
title: "[SOLVED] Printer Cups no work - how to remove, install?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-10-27
I can only get the Printer cups in Gutsy to print to a PDF file.  It will not print to my HP 2420 printer no matter if I use the USB cable or the parallel cable.

This is a fresh install of Gutsy.

I would like to try removing cups and then reinstall.  How do I remove cups?

Thanks

Carl

---

### Post by llamakc on 2007-10-27
Before you remove CUPS, try this:

```

 sudo aptitude remove gnome-cups-manager

```

and make sure that the package "system-config-printer" is installed. If it is, go in and reinstall your printer.

---

### Post by cwmoser on 2007-10-27
Still does not work.  The printer worked perfectly with Feisty.  This Gutsy is a fresh install too.

Any other ideas?

Thanks

Carl



> **llamakc said:**
> Before you remove CUPS, try this:

```

 sudo aptitude remove gnome-cups-manager

```

and make sure that the package "system-config-printer" is installed. If it is, go in and reinstall your printer.

---

### Post by llamakc on 2007-10-27
I don't know if reinstalling CUPS will help but you can open Synaptic, search for all CUPS packages and choose reinstall (from the right-click menu?). Is HPLIP installed?

---

### Post by cwmoser on 2007-10-27
Yes, HPLIP is installed.


Carl

---

### Post by cwmoser on 2007-10-27
Is there another mechanism to printing than cups?  
Whatever Feisty used worked perfectly.

Carl

---

### Post by llamakc on 2007-10-27
Feisty used CUPS. I believe there are some printing bugs over at launchpad.net. Have you looked there for a comparable bug for your printer model yet? Sometimes fixes get posted in the comments of bugs (before the fix is applied to new packages).

I'd connect the printer via parallel, reboot, and rerun the printer-configure applet in Gnome.

Oh, before that try configuring the printer via CUPS web interface at [http://localhost:631](http://localhost:631) on your machine.

---

### Post by cwmoser on 2007-10-27
llamakc,

You figured it out -- using the web interface:
"Oh, before that try configuring the printer via CUPS web interface at [http://localhost:631](http://localhost:631) on your machine."


I browsed to [http://localhost:631](http://localhost:631), removed the printer and then reinstalled it -- and presto, it started printing.


Thanks much.

Carl

---

