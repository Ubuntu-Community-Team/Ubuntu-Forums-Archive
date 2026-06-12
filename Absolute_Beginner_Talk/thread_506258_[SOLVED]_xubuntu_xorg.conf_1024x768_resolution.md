---
title: "[SOLVED] xubuntu xorg.conf 1024x768 resolution"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by udiopz on 2007-07-21
I've installed Xubuntu 7.04 in an old desktop pc.

I want the 1024x768 resolution. Both my monitor and video card support it. However, it's not an option in Applications -> Settings -> Display Preferences.

Please.. can somebody help me? ()

This is a parte of my /etc/X11/xorg.conf :
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc 3D Rage II+ 215GTB [Mach64 GTB]"
        Monitor         "LM520/LM520A"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

---

### Post by confused57 on 2007-07-21
What video card or chipset do you have, and which video driver are you using?

---

### Post by NESFreak on 2007-07-21
> **confused57 said:**
> What video card or chipset do you have, and which video driver are you using?

> "ATI Technologies Inc 3D Rage II+ 215GTB [Mach64 GTB]"?

looks OK to me. Maybe it's something with the driver or the refresh settings of the monitor?

---

### Post by confused57 on 2007-07-21
> **NESFreak said:**
> ?

looks OK to me. Maybe it's something with the driver or the refresh settings of the monitor?
I didn't want to assume anything with the OP's signature:
> ASUS Notebook A6M-Q065H | CPU 32 bit: SEMPRON 3400+ | RAM: 1 GB DDR2 667 | HD: 100 GB | Video card:** NVIDIA GeForce Go 610**0

And the section of his xorg.conf didn't list the video driver that is being used.

---

### Post by udiopz on 2007-07-22
I have this problem in an old desktop pc with **"ATI Technologies Inc 3D Rage II+ 215GTB [Mach64 GTB]"**.
the nvidia video card quoted in my signature is installed in another computer (my notebook), not involved in this question.

---

### Post by Saner on 2007-07-22
How much memory does the card have ?

---

### Post by udiopz on 2007-07-22
only 2 mb.. it's an old card (sold in 1997)..

---

### Post by Saner on 2007-07-22
Try lowering the colour depth.

Restart X

Then try again.

Its been a long time, but I dont think you have the memory to have 1024x768 at a high colour depth (may get 16) but I may be wrong, as I say its been a while

---

### Post by udiopz on 2007-07-22
it works! thank you very much 4 the help!

---

