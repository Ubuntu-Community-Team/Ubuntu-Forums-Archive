---
title: "Problems with Network card"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by krullebol on 2006-12-04
Hello, I am unexperienced with Linux and I want to learn to use it. I have succesfully configured my computer as a dual boot system (I still have Windows XP). Ubuntu works fine, except that I cannot access the internet. The problem seems to be my network card, in Windows it is named:

Generic Marvell Yukon Chipset based Ethernet Controller

I have been looking on the internet and a lot of people seem to have trouble with Marvell Yukon cards. But none of the solutions I found have worked for me. 

I have tried:
1) downloading a driver from the marvell site. When running "install.sh" it gave a syntax error.
2) "modprobe sk98lin" Gives no errors, but also doesn't seem t0 help

Does anybody know how to solve this problem?

---

### Post by waynepr72 on 2006-12-04
There appears to be a number of cards out there that don't have native Linux drivers, mainly I guess because the chipset manufacturers don't supply any details other than to Microsoft, I don't know. 

I suggest you try loading from Ubuntu file add manager to add new programs: ndiswrapper

You then can try and use the Windows drivers you have with the device.  Best of luck, Wireless is definitely an issue at the moment with Linux and some cards with certain chipsets so your not alone.

Good luck,

Wayne

---

### Post by krullebol on 2006-12-04
> **waynepr72 said:**
> ...
I suggest you try loading from Ubuntu file add manager to add new programs: ndiswrapper

You then can try and use the Windows drivers you have with the device.  Best of luck, Wireless is definitely an issue at the moment with Linux and some cards with certain chipsets so your not alone.

Good luck,

Wayne

How do you "use" the Windows drivers?

---

