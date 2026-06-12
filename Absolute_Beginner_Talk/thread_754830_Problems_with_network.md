---
title: "Problems with network"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by DeaDZ_Will on 2008-04-14
Unfortunatly after my RAID Disk's decided to find themselfs, i encounter yet more problems.
I Booted up into ubuntu but unfortunatly their was no sound or network.
I turned Wireless compatipility ON
Please help

=======
info
=======
1GB Ram
I use Wireless 54 mbps
Packard bell easy note ajax C3 laptop
genraly good spec's

=======
i think it may be because it hasnt found my network hardware, any ideas on how to fix this?
THANKS SO MUCH :)

---

### Post by chazdraves on 2008-04-14
I'm not sure what card you have, but the easiest way I've found is to install ndiswrapper and Wine. Download the Windows driver for you card from the manufacturer's website and extract it using Wine. Then open ndiswrapper and click install, search for the .inf file you just installed with Wine and click OK. That works for me (Linksys WMP54G).

Good luck!
- Chaz

---

