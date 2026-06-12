---
title: "FPDither option for Rev-A G5 iMac"
date: 2006-11-20
forum: Apple PPC Users
---

### Post by stream303 on 2006-11-20
I just added the "FPDither" "true" option to my xorg.conf file on my Rev-A 20" G5 iMac and the teeny-teeny fonts look very nice.

lspci | grep VGA showed that I have a GeForce FX Go5200 rev-a1 video card and man nv says that it should work.

Here's a snippet from my /etc/X11/xorg.conf

```
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nv"
        Option          "FPDither" "true"
        BusID           "PCI:240:16:0"
EndSection
```

So now with lcd subpixel smoothing turned on in the fonts-preferences and this FPDither option in xorg.conf, things seem a little better!  I really like it.

Although my eyes are a bit tired from staring at the screen for a few hours just before trying this option...  I'll have to re-evaluate after some rest. :)

---

### Post by stream303 on 2006-11-21
Now that I haven't stared at my monitor all night I can definitely say this is an improvement.  Heck, the fonts used for writing this are nice and clean.

Apparently this FPDither option is for *anyone* running the open-source **nv** driver, a 24 bit-depth, and an lcd with a supported card.

It now looks like the good Apple display it was supposed to be!

**UPDATE:** This option will make the 6-bit displays (basically the lower-cost laptop displays on our iMac's) look good, whereas it will look bad on higher-quality 8-bit displays like the Cinema - at 8-bit already, there's no need for FPDither on high-quality screens.  Reminder - have to be using the **nv** driver at 24 bit depth already.

---

