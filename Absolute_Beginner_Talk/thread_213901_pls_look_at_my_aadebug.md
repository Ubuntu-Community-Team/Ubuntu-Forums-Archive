---
title: "pls look at my aadebug"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by Susan.Desanco on 2006-07-11
I'm not getting sound on an install of xubuntu dapper onto an older PC.

Here is the main output of aadebug:
----------------------------------------------------------------

It detects the kernel, then...
Proc Sound
Warning: module config file does not exist
This indicates that alsa is not installed correctly.

Dev Snd
/dev/snd does not exist

It does however correctly list the PCI sound card at the bottom of the report in the Hardware section:
  0000:00:0b.0 Multimedia audio controller: Rockwell International Riptide PCI Audio Controller
--------------------------------------------------------------

This is on xubuntu.  Is alsa on xubuntu by default?
When I type alsamixer in Terminal it tells me "function and ctl_open failed for default: no device"
(which I suppose makes sense)

Anything else I can do to continue to diagnose?

The box is 440BX chipset, Celeron 433MHz, 96MB PC-66 ram

Thank you!

---

