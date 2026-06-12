---
title: "How do I change the Monitor Resolution?"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by PhilKE3FL on 2007-05-15
I'm using a monitor that can display much nicer than Linux is doing. I tested it using XP Pro on this PC when I first got it & it displayed much better than this.

How does one go about changing the monitor settings, resolution, in Linux?

Thanks,

---

### Post by Billy McCann on 2007-05-15
Changing it in System > Preferences > SCreen Resolution does help?

Is your desired resolution not there to select?

Go ahead and paste the output of this command here.
```
cat /etc/X11/xorg.conf
```

What video card are you using?

---

### Post by Nythain on 2007-05-15
make sure you have the proprietary drivers installed for your video card then take a look in you /etc/X11/xorg.conf file for a section like this:
```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    #Enable 32-bit ARGB GLX Visuals
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```
and add the resolutions you want available (that you know you can handle)

---

### Post by PhilKE3FL on 2007-05-17
Thanks, the present resolution is 1280x1024 & it looks just fine. 

I think the problem was that I have a KVM switch & I was first in the Windows PC then switched to the Linux & the resolution & positioning were all messed up.

When I only boot the Linux box the monitor looks fine, I'll have to test it to see what it gets reduced to when I switch between the Windows XP box & the Linux box using the KVM switch.

Have you ever seen that problem?

Phil K

---

### Post by Terl on 2007-05-17
I have.  I had a kvm with a linux box and a winxp box and when I would switch between them the image would need to be tweaked (moved with monitor's buttons) into position.  I also got annoyed because it was analog and I liked the dvi.  I just dealt with it.  I am not sure of a good fix for it.  I have a flat panel so when I hit the switch I would just auto-adjust using the monitor's built in adjusters.  It worked.  :)  

The kvm is still hooked up, I just use it on and off for when I work at home or if I am working on a pc for my kids.

---

