---
title: "Lombard G4 (Daystar upgrd.) crash,crash, crash! WHY?"
date: 2007-11-27
forum: Apple PPC Users
---

### Post by cryptocoryne on 2007-11-27
I tried to install xubuntu, ubuntu, YDL, slackintosh, and Debian on my Daystar (7410) upgraded G4 400Mhz Lombard. 
No distribution would get past the splash screen other than debian. Is there some boot parameter that I need to pass to the kernel?

I don't understand what Debian's 2.6.18 kernel is doing differently. Why does it boot, but other debian-based distributions freeze? x

ubuntu stops shortly after the splash screen and drops to a busybox shell. the only useful thing I can type at this point is poweroff.

Debian is mostly solid, but there are sleep/resume problems. 

Also, pcmcia is goofed up and you have to use the boot parameter reserve=0xstartaddress, 0xlength to prevent an oops  when using pcmcia cards. 

DRI does not work out of the box, but I'm not sure DRI is worth bothering about, considering how sorry the Lombard's video card is anyway.

I'd really prefer to use xubuntu, but I guess I'll have to settle for vanilla Debian.

---

