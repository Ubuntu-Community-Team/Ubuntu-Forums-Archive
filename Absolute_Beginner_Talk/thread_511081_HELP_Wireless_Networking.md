---
title: "HELP: Wireless Networking"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by swifTT on 2007-07-27
Hello. I've just started using Ubuntu, I wanna get used to Linux as I'm completely new to it.

I can't seem to connect to my wireless router/network.

I have the INEXQ CR054g Wireless-G PCI Adapter used to connect my network.

If someone can help me solve this problem, that would be really grateful.

-S

---

### Post by rich.bradshaw on 2007-07-27
What's the chipset?

lspci

will tell you about all your PCI things, should be there somewhere.

You likely need to use ndiswrapper.

Google your chipset, ndiswrapper and Ubuntu to find a tutorial on how to do it.

---

