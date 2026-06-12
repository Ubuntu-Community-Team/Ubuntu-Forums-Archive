---
title: "ATI Rage Pro 128 - Poor video performance"
date: 2005-11-14
forum: Apple PPC Users
---

### Post by amklinux on 2005-11-14
Hi.

I'm new to Ubuntu PPC, and this problem is really annoying me. I have an ATI Rage Pro 128 video card in a G4 Mac, and the video performance is terrible. I tried the ati and r128 driver, and nothing seems to work (tested xine and vlc). Before installing Ubuntu, I had Yellow Dog 3.1, and the video was *very* good.

My xorg.conf configuration is:

Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "fbdevhw"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "v4l"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Rage 128 PF/PRO (AGP TMDS)"
        Driver          "r128"
        BusID           "PCI:0:16:0"
        Option          "UseFBDev"              "true"
# I tried these changes, but it didn't make any difference:
 #      Option          "RenderAccel"           "true"
 #      Option          "AllowGLXWithComposite" "true"
EndSection

Please, help me!

amklinux

---

### Post by SexyBern on 2005-11-17
I've had all kinds of similar problems.

I did the following and it seems to work with acceptable performance now:

1. Commented out the 'Load "glx"' line
2. Changed the 'Driver "ati"' line to 'Driver "r128"'

This was on an iMac DVSE with the Rage 128 video.

The version of Ubuntu is Dapper as of today (17-Nov).

Cheers,

Bern

---

