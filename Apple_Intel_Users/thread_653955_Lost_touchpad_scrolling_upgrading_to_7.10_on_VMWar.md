---
title: "Lost touchpad scrolling upgrading to 7.10 on VMWare"
date: 2007-12-30
forum: Apple Intel Users
---

### Post by opus_az on 2007-12-30
Hi...I have VMWare Fusion on an Intel MacBook. When I updated my 7.04 virtual machine to 7.10 I lost the ability to scroll with the touchpad. It worked fine on the 7.04. 

I reinstalled VMWare tools but that didn't help.

Any suggestions? I'll be asking at the VMWare forums too, but I hope someone here could help.

---

### Post by opus_az on 2008-01-01
OK, I got it. Added this to /etc/X11/xorg.conf and restarted. 
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "SHMConfig"             "true"
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1"
EndSection
```
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

