---
title: "[SOLVED] New motherboard (compatability with old components and ubuntu?)"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by travismoore on 2008-01-28
**Motherboard and processor**
[http://www.misco.co.uk/applications/SearchTools/item-details.asp?EdpNo=290189&Tab=2&NoMapp=0](http://www.misco.co.uk/applications/SearchTools/item-details.asp?EdpNo=290189&Tab=2&NoMapp=0)

**Heatsink fan**
[http://www.misco.co.uk/applications/SearchTools/item-details.asp?EdpNo=280829&CatId=28](http://www.misco.co.uk/applications/SearchTools/item-details.asp?EdpNo=280829&CatId=28)


Thats what im going to buy (probably this evening) if everything is compatible.

Just need to know if my current componenets are compatible.

**Current components:**
RAM1: 512MB DDR PC2700
RAM2:256MB DDR (dosn't say what PC i presume same as 512)
RAM3:125MB DDR PC2700 (not in my pc but i have it)
Graphics:Nvidia GeForce 2 MX/MX 400 (64MB)

I don't mind so much using the onboard graphics as they are 128MB which is better than my current card but they are shared(i think -_-) and im not sure about compatibility with ubuntu.

Also do i need thermal gel to put the heatsink and fan on the processor?

Thanks,

Travis

---

### Post by Therion on 2008-01-28
HSF and new mobo are compatible.

Memory appears compatible since it's all 184 pin DDR but mixing brands, module sizes, timings etc. could be problematic.  Most likely everything will sort itself out, but if you get BIOS beeps on startup, memory issues would be my first consideration.

No AGP slot on the new mobo, but you say you're willing to use the onboard graphics.  Personally I detest onboard graphics "solutions" since they tag the CPU and system memory for rendering.  I'd suggest popping in an inexpensive PCI-e video card, but that's up to you.  The SiS chipset may not (or may not) be able to use accelerated graphics working, but Ubuntu should work with framebuffer mode. When you are installing Ubuntu, if it can't figure out what chipset to use, it will bring up a list for you to choose from. If you get that list, just select the vesa driver and all should be well (thought it might be a little slow).  Again, I'd suggest even a lower-end nVidia PCI-e graphics card over integrated graphics any day of the week.

You will definitely need some thermal paste for the HSF/CPU "connection".  Usually you get a little tube of thermal paste with a new HSF.  If you don't, pick up a tube at your local parts store.

---

### Post by travismoore on 2008-01-28
> **Therion said:**
> HSF and new mobo are compatible.

Memory appears compatible since it's all 184 pin DDR but mixing brands, module sizes, timings etc. could be problematic.  Most likely everything will sort itself out, but if you get BIOS beeps on startup, memory issues would be my first consideration.

No AGP slot on the new mobo, but you say you're willing to use the onboard graphics.  Personally I detest onboard graphics "solutions" since they tag the CPU and system memory for rendering.  I'd suggest popping an inexpensive PCI-e video card, but that's up to you.

Yea my whole pc needs a giant upgrade really so i will get new graphics card at some point anyway. Can't say im fond of onboard graphics either but as i have no money at the moment its the only solution.

---

