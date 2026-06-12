---
title: "Adding Local Printer"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by indytim on 2007-03-17
OK, it's been awhile since I had to do this (must be too early here).

I'm trying to add a local printer under Kubuntu 6.10.  The printer is a Lexmark E322 (optra321).  The printer is using a usb connnection.  The printer has been connected in the past as a print server and as a samba share printer.  This time around, I want to make it a dedicated local printer to the Kubuntu 6.10 ops.

Going through the KDE add printer, when I come to the Local Port Selection part of the wizard, there is nothing being detected on any of the usb ports.  

I know this is probably a "101" situation, but what am I missing?

Thanks,

IndyTim

---

### Post by indytim on 2007-03-17
Resolved (sort of).

Ended up connecting the printer to the parallel port and doing the printer install via lpt1 on the port selection (did not use the usb connection from printer to pc :( ).  Works well.

Looks like there is more work to do with auto-identifying usb-connected printers for local printing only.

---

