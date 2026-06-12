---
title: "monitor blinks / flashes"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by aBitLater on 2008-02-11
occasionally, my laptop monitor blinks, and if I reboot, it's ok for awhile.

How can I find out what is causing this?

My first thought was that it is compiz???  I'm not sure how to disable that, or even if compiz is the real culprit. Do I just uncheck the "enable integration into the desktop environment" to disable compiz features?

I did check to see if Sync to VBlank is checked because I seemed to recall a few posts (on other topics) saying that it might cause problems. It is not checked.  I also noticed that outputs has only, 
"640x480+0+0"

but my monitor is at 1400x900 resolution.  I'm not sure if that matters.

Thanks for suggestions and help.

---

### Post by oldb0y on 2008-02-11
Have you tried to set the resolution that's correct for your monitor?

---

### Post by aBitLater on 2008-02-11
1440x900 is correct for my monitor, and that's what it is now.  (I mistakenly said 1400 in last post).

My laptop is an HP Pavilion dv8000.

Here are the pertinent sections of my xorg.conf - I can list it all if that helps anyone to help me:

```
Section "Device"
        Identifier      "nVidia Corporation G72M [GeForce Go 7400]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       28-72
        Vertrefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G72M [GeForce Go 7400]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1440x900"
        EndSubSection
EndSection

Section "Module"
        Load            "glx"
EndSection


```

---

