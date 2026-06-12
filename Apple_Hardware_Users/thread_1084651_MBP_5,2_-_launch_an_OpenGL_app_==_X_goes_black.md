---
title: "MBP 5,2 - launch an OpenGL app == X goes black"
date: 2009-03-02
forum: Apple Hardware Users
---

### Post by darkcarnival on 2009-03-02
As the title says I'm the owner of a MBP and I've decided to throw Linux on it (being a long time user and such :) )

Anyway. Whenever I launch an OpenGL-based app (test cases being "SuperTux" and "Tremulous" - both available from the repository) I get a black screen with a thin white bar at the top and I'm forced to kill X to get anywhere.

This has happened with:
Nvidia 177 from the repository
Nvidia 180.11 from the repository
Nvidia 180.29 from nvidia.com hand-compiled and installed after removing the old nvidia drivers.

Anyone have any nice ideas ? I'm kinda stumped :/

PS! Compiz runs just fine - and GLXgears works.



Please please please, help ! :)

---

### Post by darkcarnival on 2009-03-02
Turns out I had been a little over-zealous in copying xserver settings from a guide on Fedora 10 for Macbooks and some nvidia-specific settings there caused the problems.

I simply stripped my x-config of any and all settings (except NoLogo) so that it now reads

```

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AllowGLXWithComposite" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NvAGP" "0"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Viewport    0 0
        Depth       24
    EndSubSection
EndSection

```

Instead of the **old settings**:
```

Section "Screen"
   Identifier     "Screen0"
   Device         "Videocard0"
   Monitor        "Monitor0"
   DefaultDepth    24

   Option        "AllowGLXWithComposite" "True"
   Option        "AddARGBGLXVisuals" "True"
   Option        "TripleBuffer" "True"
   Option        "UseDamageEvents" "True"
   Option        "UseRandR" "True"
   Option        "RenderAccel" "True"
   Option        "NoPowerConnectorCheck" "False"
   Option        "RandRRotation" "True"
   Option        "DynamicTwinView" "True"
   Option        "OnDemandVBlankInterrupts" "True"
   Option        "ConnectToAcpid" "True"
   Option        "EnableACPIHotkeys" "True"
   Option        "UseEvents" "True"
   Option        "ExactModeTimingsDVI" "True"
   Option        "NvAGP" "0"
   Option         "NoLogo" "True"
   SubSection     "Display"
        Viewport    0 0
        Depth       24
   EndSubSection
EndSection

```
Which of the settings caused this problem, I don't know...


Anyway.. Sorry for the unnecessary post (unless someone else happens to find their fix here, in which case it wasn't entirely unnecessary!)

---

