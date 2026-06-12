---
title: "Boot over IP?"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by Sonic Reducer on 2007-01-05
say i forgot a paper at home, could i possibly log onto a computer at school and boot my computer from home and retreive the file off my box?

i don't know the limitations of remote desktops, or even the proper terminology, but if there is any way to boot my ubuntu computer at home from a windows computer at school and print the paper or whatever i'd forgotten i'd love to know about it

---

### Post by Jussi Kukkonen on 2007-01-05
In  theory yes, if your hardware suppots it. it's called Wake-on-LAN: [http://en.wikipedia.org/wiki/Wake-on-LAN](http://en.wikipedia.org/wiki/Wake-on-LAN)... I'd suggest finding an old low-power machine that you can set up as file server / SSH machine (and leave on), though.

---

### Post by geek_Man on 2007-01-05
No, you wouldn't be able to physically turn your computer on remotely. Sorry.

EDIT: Or maybe I'm wrong, I thought you couldn't. My bad.

---

### Post by PilotJLR on 2007-01-05
You would need a management machine on the same subnet to use WoL (assuming the target NIC supports WoL).

Another option is to buy a managed PDU, which would enable you to telnet or even dial-in to the PDU and turn on an outlet.

And you could also just keep the computer on.  :-)

---

### Post by moshuptrail on 2007-01-05
I think WOL (wake on Lan) only works for standby mode - the computer is up, powered on, but pretty much asleep.  I would suggest just leaving it on.  If you are concerned about the wasted cycles, look up BOINC.

---

### Post by PilotJLR on 2007-01-05
No, WoL works for a cold boot. 

ATX soft power keeps the NIC powered... if your computer is off, but the PSU is switched on, then you will notice a link light on the NIC, unless it does not support any of these features. This is because soft power keeps the NIC up and running, listening for a WoL frame.

---

