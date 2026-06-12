---
title: "Full Screen ZOOM"
date: 2010-02-17
forum: Assistive Technology &amp; Accessibility
---

### Post by krisarmstrong on 2010-02-17
I was wondering dose Ubuntu 9.10 have a full screen zoom similar to MAC OSX or Windows 7.  In windows 7 I can press the "Windows Key and the + Key" and the entire screen zooms.  

i know that Ubuntu has a magnifier that zooms parts of the screen how about the whole screen?

Thanks,
kris

---

### Post by notlistening on 2010-02-18
You can use a combination of compiz and ezoom. Which in theory should work out of the box after an install. Try you windows key and scroll away from you on the mouse. If you have 3D acceleration then it will zoom. If that does not work go system->prefs->appearance visual effects and the set them to normal. If this does not work try hardware drivers to see if you need them for your graphics card to get 3D and if that does not work come back ans it gets a bit more complex ;)

---

### Post by 311005901 on 2010-02-19
I suggest first turning on Visual Effects.
**System>Preferences>Appearance Preferences**
Click on "Visual Effects" and select 'Normal'.

Then, [click here to install a settings manager]("apt:simple-ccsm").

Open it up under **System>Preferences>CompizConfig Settings Manager**.

From that program, you can enable and tweak all kinds of neat accessibility features.

---

### Post by krisarmstrong on 2010-02-20
> **notlistening said:**
> You can use a combination of compiz and ezoom. Which in theory should work out of the box after an install. Try you windows key and scroll away from you on the mouse. If you have 3D acceleration then it will zoom. If that does not work go system->prefs->appearance visual effects and the set them to normal. If this does not work try hardware drivers to see if you need them for your graphics card to get 3D and if that does not work come back ans it gets a bit more complex ;)

Thanks I'll give this a try and let you know soon I was wondering if this might work on the netbook version of ubuntu any ideas?

---

### Post by Sef on 2010-02-20
> Thanks I'll give this a try and let you know soon I was wondering if  this might work on the netbook version of ubuntu any ideas?

It could, if the graphics card would support compiz and there is enough memory for it.

---

### Post by aamonster on 2010-02-21
> **notlistening said:**
> You can use a combination of compiz and ezoom.
One more question: is it possible to reduce desktop resolution when zooming?

For example 1920x1200 screen. I go away from screen - now image is too small. I want to zoom it in.
I hold Win key and rotate mouse wheel for some time - screen zooms to 200%. Almost ok, but now I see only quarter of desktop.
Is it possible to set desktop size for all applications to 960x600 for 200% zoom (or 1280x800 for 150% zoom etc)?

---

### Post by Rhemat on 2010-05-14
I'm guessing that the Zoom effect can only be attained with the extra graphical features enabled?  The reason I ask, is that I use NetRadiant, and when Compiz is enabled, the view window, and the texture select window are completely unusable.  Is there any way to fix that?
Thanks in advance.

---

### Post by Rhemat on 2010-07-21
Okay, I am betting that this is an ATi graphics issue.  I'm trying this on my laptop, which has the following specs:

OS:  Linux Mint 9 KDE
Graphics Card:  nVidia 9800m GS 512MB RAM

There are other differences, but I don't think the OS would make much difference here.  I could be wrong though.

Is it just me then, or does ATi seem to suck when it comes to Linux drivers?  What is weirder, is that I think Apple has an exclusivity agreement with ATi, and there is a lot running in both OS X and Linux that are practically identical with video (both use OpenGL and X11 to my knowledge).  So why would their drivers suck for Linux when they've already done most of the work in OS X?

---

