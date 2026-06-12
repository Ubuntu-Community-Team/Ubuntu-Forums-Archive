---
title: "Airport Extreme Configuration"
date: 2007-02-12
forum: Apple PPC Users
---

### Post by thomasmallen on 2007-02-12
Well, so far so good with my Linux quest. I completely purged out OSX on my first install and am not regretting it, except for one thing. The situation on getting my wireless card is not promising...

I no longer have Mac OS files, so any solutions relying on native firmware appear to be undoable (they seem to always refer to System>Library>... aka OSX directories).

I'm running a 2.0GHz Macbook which I'm 99% certain came with an Airport Extreme card installed (I think this was the first or second generation of PCs from Apple that came standard with Extreme). I know that this is a PPC forum, but what better place to mind Mac people running Linux who might know about this sort of thing?

Oh, and I'm on 6.10, installed yesterday (so the latest stable Kernel).

---

### Post by das_syndrom on 2007-02-13
Hi!

Have you read any guides before?
[linux-on-laptops]("http://www.linux-on-laptops.com/apple.html")
[tuxmobil]("http://tuxmobil.org/apple.html")
[a_good_one]("http://desrt.mcmaster.ca/macbook.xhtml")
[Ubuntu-Macbook-Howto]("https://help.ubuntu.com/community/MacBook")

In short:
If you have a Macbook CoreDuo, you need the madwifi-drivers
If you have a Macbook Core2Duo, you have to use ndiswrapper. Its awful, but it works!

Andi

---

### Post by thomasmallen on 2007-02-13
Thanks for the help. Turns out, my computer doesn't have a BroadCom card. I had read so many horror stories of wireless on Macs with Ubnutu that I assumed it was Broadcom. In any case, I have the KDE Network Manager and everything works.

---

