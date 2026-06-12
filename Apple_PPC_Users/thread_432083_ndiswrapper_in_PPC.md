---
title: "ndiswrapper in PPC?"
date: 2007-05-03
forum: Apple PPC Users
---

### Post by ChrisWoj on 2007-05-03
Is it impossible to run ndiswrapper in PPC due to the fact that its purpose is running windows drivers?

And as such does this make it impossible for me to utilize the Linksys WUSB54GC (Wireless G USB) on my iMacG4?

---

### Post by linear on 2007-05-03
I believe the answer to your first question is yes, though I can't locate a source right now.

---

### Post by ChrisWoj on 2007-05-03
Well, thats absolutely splendid. :o( I've been going mad all day trying to find a way. I've got it to say I have a connection at 0% in the network manager... I can see other networks through the damn thing, but I can't actually do anything with them.

I've seen all manner of solutions involving ndiswapper, but nothing for PPC so I'm going nuts. It feels like I've plugged in nothing more than an antenna. I can't send out or request anything, but I know the signal is there! ... *grumbles* coulda figured that out with a tinfoil hat...

---

### Post by AlphaMack on 2007-05-04
If it has a Broadcom chipset, you could simply install bcm43xx-fwcutter and allow the package to fetch/extract firmware.

---

