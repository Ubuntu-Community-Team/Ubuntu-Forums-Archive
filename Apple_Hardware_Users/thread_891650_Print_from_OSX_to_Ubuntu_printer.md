---
title: "Print from OSX to Ubuntu printer"
date: 2008-08-16
forum: Apple Hardware Users
---

### Post by involutaryhaxor on 2008-08-16
I have a new iBook G4 which I intend to keep OSX on because I like having flash and java (from what I understand you can't install those on an ubuntu ppc). I only have one printer in my house and it's connected to an ubuntu desktop. I would like to be able to print to it over the network... what exactly do I have to do? If possible, step by step directions would be great!

EDIT: BTW, it's Panther that I'm running: 10.3.9

---

### Post by tgalati4 on 2008-08-16
I know that Tiger uses CUPS so I assume that Panther does as well.

Become familiar with CUPS and printing becomes easy to set up.

In a browser, study the output of:

localhost:631

Do that on both machines.  Note the version of CUPS on each machine.

You need to share the printer from the Ubuntu machine.  You need to set up the printer on the Mac and point it to the shared machine that is hosting it.

You may need to add your Ubuntu machine's address to /etc/hosts on the Mac.

When you set up the printer on the Mac using CUPS, you will see a printer definition that looks something like:

Description: Remote Printer
Location: Terry's Office
Printer State: idle, accepting jobs.
Device URI: [http://192.168.1.110:631/printers/Laserjet1](http://192.168.1.110:631/printers/Laserjet1)

This points to an old laserjet printer that is connected via parallel cable to an Ubuntu machine that hosts the printer.

Good luck.  It's not hard, but it does require some configuration effort on your part.

---

### Post by cyberdork33 on 2008-08-16
> **involutaryhaxor said:**
> I have a new iBook G4 which I intend to keep OSX on because I like having flash and java (from what I understand you can't install those on an ubuntu ppc). I only have one printer in my house and it's connected to an ubuntu desktop. I would like to be able to print to it over the network... what exactly do I have to do? If possible, step by step directions would be great!

EDIT: BTW, it's Panther that I'm running: 10.3.9
There is java and flash or ppc, just not the typical sources:
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)


[LIST]
[*]Go to System > Administration > Printing on your Ubuntu machine.
[*]On the left side, click "Server Settings" (You should also see the printer connected to Ubuntu in this box under "Local Printers")
[*]Check the box that says, "Share published printers connected to this system" and click apply.
[*]Now on your OSX machine, you should be able to browse and see the printer being shared.
[/LIST]
> **tgalati4 said:**
> I know that Tiger uses CUPS so I assume that Panther does as well.
CUPS is actually developed by Apple :) See the note at the bottom of [www.cups.org](www.cups.org)

---

### Post by tgalati4 on 2008-08-16
Apple bought CUPS recently.  It's been around for a while.

---

### Post by cyberdork33 on 2008-08-16
> **tgalati4 said:**
> Apple bought CUPS recently.  It's been around for a while.
yes understood. Just making the note that it should work well with OS X

---

