---
title: "Unable to get nvidia-settings to recognize projector resolution higher than 640x480"
date: 2011-01-10
forum: Apple Hardware Users
---

### Post by kvaadithya on 2011-01-10
Hi guys,

This is my first post on the forum ... so please bear with me if I violate the usual conventions.

Here's the story. I've managed to successfully install ubuntu 10.10 64-bit version on my Macbook Pro 6,2. And after that, one of the first things I did was to install the restricted n-vidia drivers. As of now, System -> Administration -> Additional Drivers says that the version of N-vidia is current.

The problem is: when I connect the laptop to an external projector via a mini display port/vga adaptor, the maximum resolution which nvidia-settings gives me is 640x480 for the projector (on the laptop, however, the default resolution of 1440x900 is preserved).

I know that the projector is natively capable of supporting much higher resolutions (e.g., when I boot from Mac OS X, I'm able to get 1440x900 on the projector), but for some reason, it looks like these higher resolutions are not recognised by the nvidia-settings application.

As [https://help.ubuntu.com/community/MacBookPro6-2/Maverick#External%20Monitor](https://help.ubuntu.com/community/MacBookPro6-2/Maverick#External%20Monitor) says, I tried modifying the /etc/X11/xorg.conf file by adding the line: Option       "NoEDID" "True" under the "Device" section, but no luck. I'm still stuck with 640x480.

Also tried the variant: Option "UseEdid" "False". Again no luck.

Thanks for taking the time to help me!

---

### Post by buntuLo on 2011-01-11
are you connecting the beamer to the miniDP-VGA adapter directly with the original cable of the beamer?
if not, is it possible for you to try this configuration?

i had the same problem connecting to every kind of beamer, when an extension cable and/or a commuting box were used for the connection: the edid infos would not be received by the laptop.

in such cases, it should be possible to manually set the desired resolution and refresh rates in the xorg.conf file (together with disabling the edid request as you tried to do), but i didn't have the chance to try this out.

good luck, Lo.

---

### Post by kvaadithya on 2011-01-13
Hi Lo,

Thanks for your prompt reply. And sorry for my late reply: I was travelling and had to get back to office to check the projector's connections.

Yes, the mini display to VGA adaptor sits between the laptop and the cable that connects to the projector.

> in such cases, it should be possible to manually set the desired  resolution and refresh rates in the xorg.conf file (together with  disabling the edid request as you tried to do), but i didn't have the  chance to try this out.

I did try quite a few variants of the xorg.conf file. I tried giving it my own metamodes line, and tried tweaking the "mode validation" option (described in [ftp://download.nvidia.com/XFree86/Linux-x86_64/1.0-8762/README/appendix-d.html](ftp://download.nvidia.com/XFree86/Linux-x86_64/1.0-8762/README/appendix-d.html)) so that it doesn't use the EDID. No luck yet though.

---

### Post by schneibe on 2011-08-04
Hey guys, I'm having the same problem here. Did any of you find a solution to this issue?

Thanks,

Bertrand

---

### Post by blane2 on 2011-08-04
in the bottom of the xorg.conf under section "screen"

add modes "1440x900"

```

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-2: nvidia-auto-select +1920+0"
    SubSection     "Display"
        Modes      "1200x800"
        Depth       24
    EndSubSection
EndSection

```

this is example code i was using a 1200x800 res.


the no edid thing, doesn't work

---

