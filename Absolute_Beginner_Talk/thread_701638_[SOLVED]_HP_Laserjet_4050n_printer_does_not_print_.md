---
title: "[SOLVED] HP Laserjet 4050n printer does not print anything"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by bobbyubun on 2008-02-19
hello group

I have set up my computer (7.04) to print to a HP Laserjet 4050n printer. I used the recommended postscript printer. When I print a test page from the Printers page, it does not print anything.
I checked connection, everything is fine and I do not have any clue what is wrong.it prints perfectly in windows.
Appreciate any help

Note: it is connected to LPT and system->administration->printers shows Laserjet-4050 ready status

---

### Post by bobbyubun on 2008-02-19
what is the best way to diagnose the printer (command line)?Is there a command or utility to log the communication between my desktop and non responding printer,then I can post more information or I might be able to figure out what is wrong with it

Thanks for help

---

### Post by bobbyubun on 2008-02-19
I typed in lpstat -p LaserJet-4050
 and get :
printer LaserJet-4050 is idle.  enabled since Tue 19 Feb 2008 01:41:43 PM EST
  open print channel failed; will retry in 30 seconds...

Any help
Thanks

---

### Post by bobbyubun on 2008-02-19
I got it to work by going to

printer properties
> Connection

then selecting "Use another printer by specifiying port" and choosing "Parallel Port #1" from the drop down list.

---

