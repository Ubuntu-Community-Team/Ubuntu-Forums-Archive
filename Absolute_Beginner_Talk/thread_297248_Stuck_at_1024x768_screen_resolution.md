---
title: "Stuck at 1024x768 screen resolution"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by MakLeod on 2006-11-10
This problem has been bothering me for a while, and I can't seem to figure out why it's happening.  I'd preferably like to be in 1152x864 resolution, and I have that option enabled in my xorg.conf file.  However, for some reason whenever I use the Gnome screen resolution manager it won't give me anything other than 1024x768.  Here's the xorg:

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Monitor        "VL173"
    DefaultDepth    24
    Option         "Coolbits" "1"
    SubSection     "Display"
        Depth       1
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


As you can see I have four resolutions selected, but only 1024 is being allowed.  Any ideas?

---

### Post by John.Michael.Kane on 2006-11-10
Have a read [http://ubuntuforums.org/showthread.php?t=289269&highlight=modeline](http://ubuntuforums.org/showthread.php?t=289269&highlight=modeline)

Make the adjustments to fit your monitor specs.
You may have to find these specs in your monitor manual.
HorizSync 
VertRefresh

---

### Post by Toby2 on 2006-11-10
I had this problem, except I was stuck at a 1400x1050 resolution. To fix it, in the 'Monitor' section of my xorg.conf, I added this:
```
HorizSync 70
VertRefresh 70
```
I'm not sure what the numbers should actually be, but 70 fixed it for me. If you set the incorrect values, the screen display might go a bit distorted, so I'm not sure; for me it was trial and error.

EDIT: Do what SD-Plissken said; find them in your manual. :P

---

### Post by Velotix on 2006-11-10
If none of the above work, try using a different driver - nVidia have a driver that's available from their website; [here](http://www.nvidia.com/object/linux_display_ia32_1.0-9629.html). Use it at your own risk.

---

### Post by MakLeod on 2006-11-11
Hmm has anyone had any experience with installing the driver directly from the nvidia website?  I'd like to try it, but I don't want to break my system.  Plus it's updated as of November 7th.

---

### Post by SZorg on 2006-11-11
If I recall, I installed from the nvidia website. I got a bunch of things going on, changed various settings in Gnome, made my desktop environment 3D etc. It messed with a few things, I really liked the 3D cube environment but I couldn't handle the rest of it, and ended up ditching it.

---

### Post by bodhi.zazen on 2006-11-11
> **MakLeod said:**
> Hmm has anyone had any experience with installing the driver directly from the nvidia website?  I'd like to try it, but I don't want to break my system.  Plus it's updated as of November 7th.

Yes, it works just fine. You need to follow the instructions in the guide....

[How to nvidia](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

I prefer method 2

---

