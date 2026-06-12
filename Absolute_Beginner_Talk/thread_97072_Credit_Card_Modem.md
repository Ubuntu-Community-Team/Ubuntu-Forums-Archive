---
title: "Credit Card Modem"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by RhinoHornZa on 2005-11-30
I have a Xircom PCMCIA modem that I want to install on my Laptop running Ubuntu 5.10.  How do I setup the modem and dial up connection to the Internet?

---

### Post by nab on 2005-11-30
Hi,

What' the exact type of your modem?

Insert your card and type on a terminal:

lspci

and have a look whether you can find your card.

If that's not working, type:

dmesg | tail 

This should show a device set to ttyS3 or something ttyS4 (at least my pcmcia card does on my notebook)

If you don't see your card, check with:

lsmod

whether the serial_cs module is loaded.

If dmesg shows your card, you can see with:

sudo cardctl ident

whether the screen shows the card correctly. 


Just a starting piont...

Good luck,

Niko

---

