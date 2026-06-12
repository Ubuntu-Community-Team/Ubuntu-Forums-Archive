---
title: "gutsy recommended video card"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by sitka on 2007-10-23
Recommended Video card for Gusty?   :confused:

---

### Post by Pierre Lourens on 2007-10-23
Intel's integrated graphics are great and work out of the box, along with most of Nvidea cards.  There is some ATI support, but ATI as a whole has been less helpful with providing drivers to the Linux community. 

I'd go with Nvidea or Intel.  My Intel GMA950 runs Compiz Fusion excellently, and I haven't had any problems whatsoever.

---

### Post by sitka on 2007-10-23
Have a Radeon X300 now...   It has frozen up on me once already when running compiz fusion...   Hasn't frozen since I turned everything off.  There is a noticeable performance hit when using eye candy features too :(

---

### Post by louieb on 2007-10-23
a couple of nvidia cards in the 50 dollar range (if you shop around) FX5200 and 7300GT.  I  have PCs  with these cards running Gutsy both just worked without a problem. BTW  I've  seen  2 or 3 forum threads  where  there are problems with the FX5200.  The common thing about them there PC has on-board video and the are using the PCI version of the card.
If you PC  has an AGP or PCI-E slot I'd get a card for that.

---

### Post by Pierre Lourens on 2007-10-23
> **sitka said:**
> Have a Radeon X300 now...   It has frozen up on me once already when running compiz fusion...   Hasn't frozen since I turned everything off.  There is a noticeable performance hit when using eye candy features too :(

Sorry to hear that.  Is your computer easily upgradeable?  If so, Newegg should have some pretty good prices on hardware.

---

### Post by rebelxhardcore on 2007-10-24
Does anyone know if the ATI Radeon x800xl will work with full support, I have a dell Optiplex GX620 mini-tower with Intel GMA950 Graphics, but I am using an ATI Radeon X800XL in the machine- will there be full support for this card?

Note: the intel GMA950 graphics is turned off due to having the ATI/MSI Radeon X800XL card in the PCI-e slot.

John

---

### Post by Qwerty_ on 2007-10-24
I would go with nvidia. My 6600GT runs fine in ubuntu not a single issue in installing drivers or anything.

---

### Post by rebelxhardcore on 2007-10-25
Well I tried running Ubuntu 7.10 with this graphics card, there is some slow-downs with some of the OpenGL screen savers, but the odd thing some games run fine, but when I hit a certain area of the map in the game it slows down quick. I pulled out the ATi and for some strange reason the operating system runs like a dream with the Intel GMA950. - That's uninstalling the ATi and reconfiguring it with the intel GMA950 graphics.

But I see some sweet deals on Newegg for a graphics card and I'll buy it.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130048](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130048)

Hopefully it will work. 7800GTX 256MB 256-bit GDDR3 PCI Express x16.

---

### Post by eldepeche on 2007-10-25
Check [here](http://www.free3d.org/) for benchmarks using free software drivers. This is the route I would recommend, since:

1. Free software drivers can be included in the default distribution, so the cards listed on this page will work out of the box, with no (or very little) extra configuration. 

2. While Ubuntu does a good job of integrating the proprietary (black-box) drivers, the simple fact is that ATI/AMD and nVidia won't divulge all the information necessary for someone who diverges from their particular kernel configuration, so it's impossible to guarantee these drivers will work with your hardware/software configuration, or that they won't fail in unexpected ways.

3. You probably switched to GNU/Linux because you have at least some support for software freedom. This is free software. Driver blobs from the manufacturers are not.

Caveat: ATI/AMD have pledged to release full specifications and help in the creation of free software drivers for their chipsets. These do not yet exist, but likely will in the near future (1 year? 18 months?).

---

