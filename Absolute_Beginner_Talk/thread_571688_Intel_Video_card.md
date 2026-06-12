---
title: "Intel Video card"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Tombo5150 on 2007-10-09
I have an Intel Video card in my new dell inspiriron laptop. I would like to figure out how to use an S-Video cable to get the screen on a television. How do I configure the card so i can do this? I've seen lots of stuff for ATI cards, but mine is Intel.

---

### Post by skymera on 2007-10-09
uhh  i had an intel card.
in linux it was useless!

is it not piossible to plug into the TV and sww if it works?

sorry you may have tried it

---

### Post by Tombo5150 on 2007-10-09
What? I heard that Intel is very open source friendly

---

### Post by skymera on 2007-10-09
well not mine, i had the drivers, but it was terrible.

---

### Post by overdrank on 2007-10-09
> **Tombo5150 said:**
> I have an Intel Video card in my new dell inspiriron laptop. I would like to figure out how to use an S-Video cable to get the screen on a television. How do I configure the card so i can do this? I've seen lots of stuff for ATI cards, but mine is Intel.

Hi this link maybe of some help
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_Large_Widescreen_Support](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_Large_Widescreen_Support)
Good luck!

---

### Post by milosz.galazka on 2007-10-09
Informations about configuring xorg for vga or s-video output is [here]("http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_900")

Just backup your xorg.conf  :)

---

### Post by Tombo5150 on 2007-10-09
How do you backup the xorg.conf? I opened the file and put in some stuff that it said to on the webpages but the commands did not work in terminal after I tried.

---

### Post by Tombo5150 on 2007-10-09
When I enter the commands it says PCI id of the i1810 is not recognized.

---

### Post by milosz.galazka on 2007-10-10
To backup xorg.conf just do something similar:
```
cd /etc/X11/
cp xorg.conf xorg.conf.bak
```

Please post some informations about your intel card and probably *dmesg* output and your xorg.conf file.

My card (just to be short):
```
 dmesg | grep agpgart
[   15.416000] Linux agpgart interface v0.102 (c) Dave Jones
[   15.460000] agpgart: Detected an Intel 915GM Chipset.
[   15.460000] agpgart: Detected 7932K stolen memory.
[   15.476000] agpgart: AGP aperture is 256M @ 0xa0000000

```
I don't have svideo output.. but somebody will find the answer, as I hope...

---

