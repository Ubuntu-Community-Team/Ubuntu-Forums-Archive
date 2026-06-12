---
title: "Winmodem"
date: 2005-07-09
forum: Absolute Beginner Talk
---

### Post by joegum on 2005-07-09
I use a ProStar Model 2794 laptop.  The info I have about the wi nmodem is as follows:

pci=0x1039, 0x7013, 0x16
manu= Silicon Integrated Systems [SiS] Intel 537 [56k Winmodem] SiS630

So far, the only Linux I've found that can use this winmodem is Xandros.  I'd like to try Ubuntu after all the good thing s I've read about it, but I must use dialup.  


Is there an easy way to find out if Ubuntu will work with this?

Thanks,   -Joe

---

### Post by polo_step on 2005-07-09
[QUOTE=joegum]
Is there an easy way to find out if Ubuntu will work with this?
[/QUOTE]
I think a first, easy try, would be to see how the Live CD reacts to it. That's just a guess on my part.

I'm not 100% positive, but I believe this is the same chipset and query readout that showed in this OEM Linspire box's modem, which worked OK with that Debian distro.  I went to DSL before installing Ubuntu, so I don't now how that would have worked or not.

---

### Post by az on 2005-07-09
You probably need the sl-modem drivers.

[https://wiki.ubuntu.com/forum/hardware](https://wiki.ubuntu.com/forum/hardware)

Look in the modem subpage and run scanmodem.

---

### Post by joegum on 2005-07-16
Thank you for the great advice.   !   -Joe

---

