---
title: "change login screen resolution with nvidia 6600"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by bricksen on 2007-08-12
After I setup twinview in clone modus I must have done something wrong for i suddenly had my desktop over oneandahalf screen :confused:
It was easy to change it back to normal (in my case 1024x768.) for both tv and desktop but I can't get it to work for my login screen?

this is my xorg.conf:

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1024x768 +0+0, TV: nvidia-auto-select +0+0; CRT: 1280x960 +0+0, TV: nvidia-auto-select +1280+0; CRT: 1152x864 +0+0, TV: nvidia-auto-select +1152+0; CRT: 1024x768 +0+0, TV: nvidia-auto-select +1024+0; CRT: 832x624 +0+0, TV: nvidia-auto-select +832+0; CRT: 800x600 +0+0, TV: nvidia-auto-select +800+0; CRT: 640x480 +0+0, TV: nvidia-auto-select +640+0"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "1600x1200" "1280x1024" "800x600" "640x480"
    EndSubSection
EndSection

I only want to have 1024x768 for both tv and pc what can I erase here without ******* the hole thing up?

---

### Post by bricksen on 2007-08-12
anyone?

---

