---
title: "this xgl thing"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by felin on 2007-04-04
This problem seems to be like a rash all over these forum, but cannot find an answer:confused:  Would be grateful for help

bought this new computer to take full advantage of the desktop effects - will I able to. should I try mandriva? my nvidia card has turbo cache- is this a problem?

trying to login to xgl after setting it up as a session - forced back to login page

glxgears
5351 frames in 5.0 seconds = 1070.070 FPS
5425 frames in 5.0 seconds = 1084.866 FPS
5824 frames in 5.0 seconds = 1164.727 FPS

lsmod |grep -i nvidia
nvidia               6829428  22
i2c_core           22848  2 i2c_acpi_ec,nvidia
agpgart          36784  2 nvidia,intel_agp

glxinfo | grep rendering
direct rendering: Yes

in xorg.conf
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "Clone"
    Option         "MetaModes" "1680x1050,NULL; 1024x768,1024x768"
    Option         "AllowGLXWithComposite" "True"
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "True"

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by nonewmsgs on 2007-04-07
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

yeah i had the same problem.  i noticed that the open source driver really doesnt handle advanced feature  well, so try the binary one.  it fixed it for me.

---

### Post by igknighted on 2007-04-07
your xorg.conf looks good.  If I were you I would forget XGL... its kinda obsolete these days.  If you want beryl or compiz, as long as you have the Nvidia drivers installed (which your xorg.conf says you do) then you can just install beryl/compiz (whichever you choose) from their repo (see [www.beryl-project.org](www.beryl-project.org) and look in the wiki) and it will work just fine.  Unless you are using Dapper, in which case if you bought a newer computer to use these effects, you really need to consider a newer OS.  Beryl was born after Dapper was released, so the support is really bad.  Try edgy (or feisty if you are feeling brave or want to wait a few weeks) and your experience will be much better.

---

### Post by felin on 2007-04-08
> **igknighted said:**
> your xorg.conf looks good.  If I were you I would forget XGL... its kinda obsolete these days.  If you want beryl or compiz, as long as you have the Nvidia drivers installed (which your xorg.conf says you do) then you can just install beryl/compiz (whichever you choose) from their repo (see [www.beryl-project.org](www.beryl-project.org) and look in the wiki) and it will work just fine.  Unless you are using Dapper, in which case if you bought a newer computer to use these effects, you really need to consider a newer OS.  Beryl was born after Dapper was released, so the support is really bad.  Try edgy (or feisty if you are feeling brave or want to wait a few weeks) and your experience will be much better.

Brilliant - thanks for the response - I will be upgrading from dapper soon. Really appreciate your time.

---

