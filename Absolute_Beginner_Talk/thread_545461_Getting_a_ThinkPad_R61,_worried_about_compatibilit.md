---
title: "Getting a ThinkPad R61, worried about compatibility..."
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by jflipper on 2007-09-07
Hi, brand new to Linux, but I can't justify using Vista.  I was wondering if I could have some help figuring out what work I would need to do to make Ubuntu work on the following computer (in addition to the basic install).

**Computer:** ThinkPad R61 7732 CTO

Processor:               Intel Core 2 Duo T7300 - 2.0 GHz 800MHz 4MBL2
Display:                   14.1" WXGA TFT Display (w/o camera)
Graphics:                 Intel GMA X3100 GM965 w/ 1394
Memory:                  2 GB PC2-5300 DDR2 SDRAM 667MHz SODIMM
Hard Drive Cache:   Intel Turbo Memory 1GB
Optical Device:        DVD Recordable 8x Max Dual Layer, Ultrabay Enhanced
Wireless Card:        Intel Wireless WiFi Link 4965AGN

I think that's about it for the important stuff (and maybe more than I needed to bother listing).  Let me know if anything seems fishy, or if anyone knows fixes that I'll likely need to go through to make all this work.  Thanks for helping out the newb!

---

### Post by dca on 2007-09-07
It should work, the only thing I can think of is after install the display might show 640x480 so you'd need to install the i915resolution package for the Intel graphics.  I may be wrong...  but, that's all I can think of...

---

### Post by overdrank on 2007-09-07
> **jflipper said:**
> Hi, brand new to Linux, but I can't justify using Vista.  I was wondering if I could have some help figuring out what work I would need to do to make Ubuntu work on the following computer (in addition to the basic install).

**Computer:** ThinkPad R61 7732 CTO

Processor:               Intel Core 2 Duo T7300 - 2.0 GHz 800MHz 4MBL2
Display:                   14.1" WXGA TFT Display (w/o camera)
Graphics:                 Intel GMA X3100 GM965 w/ 1394
Memory:                  2 GB PC2-5300 DDR2 SDRAM 667MHz SODIMM
Hard Drive Cache:   Intel Turbo Memory 1GB
Optical Device:        DVD Recordable 8x Max Dual Layer, Ultrabay Enhanced
Wireless Card:        Intel Wireless WiFi Link 4965AGN

I think that's about it for the important stuff (and maybe more than I needed to bother listing).  Let me know if anything seems fishy, or if anyone knows fixes that I'll likely need to go through to make all this work.  Thanks for helping out the newb!

Hi and welcome a quick search of the forums, results
[http://ubuntuforums.org/search.php?searchid=26762451](http://ubuntuforums.org/search.php?searchid=26762451)
I am sure you can find anything in thees searches that will raise concern. Good luck! :guitar:

---

### Post by asmoore82 on 2007-09-07
Thinkpad T42 here w/Fiesty ...
it all looks good except for that Video Card,
I think it would be well worth it to spring for ATI Radeon Mobility.

---

### Post by LowSky on 2007-09-07
i got a t60 runnig it fine (ati drivers suck)

tried a t22 and a t30 and they work too with XFCE

---

### Post by asmoore82 on 2007-09-07
> **LowSky said:**
> i got a t60 runnig it fine (**ati drivers suck**)

tried a t22 and a t30 and they work too with XFCE

Agreed for the most part, but the hardware is great.
As soon as the driver catches up and supports Xorg/AIGLX this
Thinkpad will become a lean, mean compiz-fusion machine!!
(already have it working through Xgl, but it's just not the same)

with my T42 and the ATI drivers that Ubuntu automagically installed,
my S-Video output works with no add'l config... just have to connect it and
restart X and I get an automagic clone Display setup=D>. :D

---

### Post by Judicata on 2007-09-07
Thinkpads generally play well with Linux (last I checked Shuttleworth and many of the Ubuntu developers use them). Check out [http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki) , specifically [http://www.thinkwiki.org/wiki/Category:R61](http://www.thinkwiki.org/wiki/Category:R61) .

---

