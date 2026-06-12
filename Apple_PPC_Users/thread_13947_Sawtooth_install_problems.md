---
title: "Sawtooth install problems"
date: 2005-02-03
forum: Apple PPC Users
---

### Post by dlenmn on 2005-02-03
I tried to look around for information before bothering yall, but i was unsuccessful. Most of this is history, but I figured that it might be useful anyway.

I have an upgraded sawtooth powermac g4 that's just been sitting around since I got a powerbook a few months ago. I've fooled around with debian on oldworld and nubus powermacs before (meaning, after much work, I managed to install it but was exhausted and stopped after that), and after I ran the ubuntu live cd on my powerbook I decided that it was cool and that I should try installing it on one of the hard dives in my desktop.

I first tried running the live cd. Every time it would start fine up but then stall after outputting something like "ohci_hcd: November 2004 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)". I decided to press on none the less.

So I tried installing from the install cd. The basic install would get through language, keyboard, etc. fine. It would then "detect hardware to find cdrom drives" and would eventually spit out: "Error while running 'modprobe -v aec62xx'". However, I could click continue, and it would get up to 95% done before freezing at "starting pc card services" (why would it bother with that?).

So, at this point, I tried an expert install. It started better, as I could skip the pc card stuff. But once I got to configuring a network device it would try to load a module, something with the words sungem and uninorth in the name/description, and freeze up. I got past that by choosing to enter parameters just for that module and then entering nothing (I don't know why that worked, but it was able to set up a network connection fine after that). I also ran into a problem with aec62xx but was again just able to hit continue. After that, everything installed fine.

However, after restarting it would load to the point "starting hotplug subsystem" and then freeze. That is where I am currently stuck. Any advice would be appreciated.

Also, there is probably plenty of information online for this, but how do I get yaboot to boot to OS X? Do i have to enter some long ugly device name? Holding down option while booting works for now, so that's not such a big deal.

Thanks.
-Leon

---

### Post by dlenmn on 2005-02-04
I  tried a hoary install cd and again it didn't get past "ohci_hcd: 2004 nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)" when booting up. Any advice for that? Thanks.
-Leon

---

