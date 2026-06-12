---
title: "Install motherboard driver help :S"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-08-23
Im going to be building my friend a new computer and I plan on using Ubuntu as his OS. Jw how can I get the motherboard drivers (onboard, etc) installed. Do i need special drivers or is there a way to get windows drivers to work?

---

### Post by szf on 2006-08-23
This is a definitive "it depends" kind of OP...
what is the mainboard, other components?

---

### Post by WalmartSniperLX on 2006-08-23
> **szf said:**
> This is a definitive "it depends" kind of OP...
what is the mainboard, other components?

[http://www.msicomputer.com/product/p_spec.asp?model=K9VGM-V&class=mb](http://www.msicomputer.com/product/p_spec.asp?model=K9VGM-V&class=mb)

i decided to post the page lol

---

### Post by szf on 2006-08-24
I see that you're looking at a VIA AM2 chipset. This is new enough that there's no much feedback so far on the combo and Linux...

I couldn't find this board listed at resources such as [phoronix.com]("http://www.phoronix.com/lch/"). 

Personally, I've been conservative on the three Linux boxen that I've built*. A common thread here is that they were all based on the VIA chipset, as is the  MSI K9VGM-V, so that may be a good thing (tm).

If there's isn't anything already in your possession (i.e. you already have a gig+ of quality DDR2 RAM and want to go AMD64) that's binding you to this choice, maybe you should consider selecting a combo that is known to *just work with Linux*...

* box 1: AMD Duron 750MHz (?)/ Asus Socket-A (model forgotten) mainboard/ 256 MB PC133 RAM
* box 2: AMD Thunderbird 1100 MHz/ Abit KT7A mainboard/ 1 GB PC133 RAM
* box 3 (current): Pentium 4 2400 MHz/ Asus P4V8 mainboard/ 2 GB DDR RAM

---

### Post by spacezmonkey on 2006-10-22
I am using this motherboard. MSI K9VGM-V. and using the onboard graphic card. Is it possible to intall that driver onto ubuntu?? currently the MSI website only enable us to download windows driver for VGA driver.

---

### Post by az on 2006-10-22
> **spacezmonkey said:**
> I am using this motherboard. MSI K9VGM-V. and using the onboard graphic card. Is it possible to intall that driver onto ubuntu?? currently the MSI website only enable us to download windows driver for VGA driver.

All the drivers that work with linux are part of the kernel or xorg  already.  I would say that 99.9 percent of basic hardware (motherboard, hard disk, ethernet, video, etc...) works fine.

There is no such thing as downloading a driver for linux, with the exception of a few things which have drivers written by the manurfacturer who do not release them as free-libre open source software.  In some cases, the closed-source and proprietairy drivers are still distributable and ship with Ubuntu anyway.

Regardless of your video card manufacturer, it will work.  If it is an ATI or Nvidia card, it will still work, but if you need hardware acceleration, you will have to go with the proprietary (manufacturer) driver.

---

### Post by spacezmonkey on 2006-10-23
does it means that i need to have a separate vidoe card to have 3d acceleration? for example playing tuxracer?

thank you

---

