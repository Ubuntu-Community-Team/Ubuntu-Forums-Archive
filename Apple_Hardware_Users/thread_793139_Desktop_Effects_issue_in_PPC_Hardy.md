---
title: "Desktop Effects issue in PPC Hardy"
date: 2008-05-13
forum: Apple Hardware Users
---

### Post by dai_vernon on 2008-05-13
Hi - I have a dual boot OS X 10.4.11 / 8.04 Hardy system set up on my iMac G5 PPC (pre isight) and there are is a problem with desktop effects in Hardy.  When setting the desktop effects setting (current setting is to have no effects) in Appearance, after some processing the system says 'desktop effects could not be enabled', and reverts back to the no effects setting.

Is this a graphics card issue?  My chipset is a GeForce FX 5200 - would I need to download drivers for this set?  If so, where?

---

### Post by stream303 on 2008-05-13
Yep - no desktop effects for us.  We have to use the open nv driver.

One thing you can do to improve the display, is to see if you like dithering.  Our displays are large, but they aren't the quality of say Apple Cinema displays.

I manually add this option to my /etc/X11/xorg.conf:

```
Section "Device"
        Identifier      "Configured Video Device"
        BusID           "PCI:240:16:0"
        **Option          "FPDither" "true"**
EndSection
```

I tend to do this for any box I run across that uses an lcd and nv driver.  See if your fonts look a bit sharper.  Some don't like the effect, but I do.

---

### Post by dai_vernon on 2008-05-13
Ok, that's good news, that it's fixable.  Where do I find the open nv driver?  A search for it in Synaptic and the install software menu turns up nothing.

---

### Post by stream303 on 2008-05-13
You're using it right now. :)  It's all we have when it comes to Nvidia on PPC.  There is the Nouveux (sp?) driver, but I haven't tried it yet.

Don't confuse the dithering option - it is a generic option that isn't specific to ppc, but to any lcd using the nv driver.  I use it on some Intel notebooks as well.

---

### Post by dai_vernon on 2008-05-13
If I have it now, why isn't it working?  Do I need to enable it somewhere?  Or is it that I need to modify my Xorg.conf as you did in order to get it to go?

---

### Post by stream303 on 2008-05-13
That's the catch - there are no PPC nvidia drivers even capable of 3d effects, so we're stuck with what we got. :)

---

### Post by Spirale23 on 2008-07-01
Same problem with a powerbook with an ATI ... grrrrr

---

### Post by stream303 on 2008-07-01
Ironically, desktop affects would probably be the first thing you'd disable on a slower machine. :)

I have it on another box, and it was eye-catching, but I quickly turned it off, or at most left it at the minimal setting.  I guess to each his own...

---

