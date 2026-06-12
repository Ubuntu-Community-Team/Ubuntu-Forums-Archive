---
title: "Wacom tablet recommendation for Ubuntu 8.10"
date: 2009-02-19
forum: Art &amp; Design
---

### Post by rempresent on 2009-02-19
At work, I use a Wacom Intuos.3 for image manipulation in Photoshop.  At home, I have a PC running Ubuntu 8.10 and would like to start doing some work with a tablet.  I know that there are a lot of software tweaks and bumps that need smoothing out in order to get it to work "just right".  I am fine with it and prepared for a little frustration.

However, if you have had some experience in this area, all input would be greatly appreciated.  Feel free to recommend other input devices or software successes that you have had.  I was planning on just running GIMP, but am up for other suggestions.

Thanks in advance.

---

### Post by rempresent on 2009-02-19
Also, first post so go easy on me.

---

### Post by mcduck on 2009-02-20
Intuos 3 works fine, that's what I'm using myself. But I've understood that pretty much al Wacom tablets should work so it's more a question of what you want to use. ;)

By default, only the pen tool works (no extra buttons or eraser), but the tablet can be just plugged in on the fly and everything works.

If you follow this quide [https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom") you can get all the extra buttons & eraser tool working correctly, but then you need to have the tablet connected from the boot and can't just plug it in when needed. Anyway, the extra tools are definitely worth it, and it's quite easy to setup.

If you install the wacom-tools package you'll get a program called "wacomcpl" which can be sued to configure all the buttons, sensitivity etc.. The annoying thing is that the settings won't stay after boot since it saves them into a fle that Ubuntu doesn't use. So to get your settngs to stay you need to copy commands wacomcpl added into ~/.xinitrc and add them into some configuration file that is actually used. ~/.profile seems to work fine.

At least Gimp and Inkscape work great with tablets, I don't know about other programs since these two do pretty much everything I need (apart from Imagemagick for batch processing of images ;)).

---

### Post by rempresent on 2009-02-21
Thanks for the advice mcduck.

I have heard good things about Inkscape, is it a Illustrator clone or used only for vector images?  I do most things in GIMP anyway, but it would be nice to have a better/more convenient set of tools to work with.

---

### Post by cb951303 on 2009-02-21
from linuxwacom website
> 

Supported Serial Devices
UD series & PenPartner
Graphire & Intuos series
Cintiq series
TabletPC (with/without touch)

Supported USB Devices
Graphire series
Cintiq (V4 series)
CintiqPartner
Intuos 1, 2, & 3
Cintiq (V5 series)
Volito series
PenPartner series
PL & DTF
Bamboo, Bamboo1, & BambooFun
TabletPC (with/without touch)


Wacom tablets usually works great with linux. Sometimes they may require a few config file modifications but the end result is almost always positive.

EDIT: Inkscape is only for vector images but check out the roadmap from wiki. There are really interesting plans. Such as CAD support :D

---

### Post by mcduck on 2009-02-21
Inkscape is a vector graphics program, but you can import bitmap images into Inkscape as objects, and also trace them into vectors. It's also able to export as PNG files.

---

