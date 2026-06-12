---
title: "thunderbolt-net on gen 1 Thunderbolt macs?"
date: 2018-09-29
forum: Apple Hardware Users
---

### Post by kevin160 on 2018-09-29
I have a 2012 mini and a 2011 macbookpro, both of which have gen 1 Thunderbolt.  Under macOS, I can plug them in together over a simple $10 Thunderbolt cable and use the Thunderbolt bridge option to create a network link and have them talk at just under 4 Gbps.  Pretty nifty!

Support for this under Linux was added to the 4.15 kernel, 18.04 Ubuntu seems to have the modules included, and I added the udev rule to allow permissions, but I'm not seeing any new interfaces or dmesg messages even if I manually modprobe thunderbolt-net.  

Has anybody used this under Ubuntu?

---

