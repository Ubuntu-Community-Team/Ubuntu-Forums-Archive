---
title: "Trying to fix window borders."
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by Halidan on 2007-11-07
I understand this should probably be in Desktop Effects & Customization section, but I'm a beginner, so I thought it'd be ok to post here as well.  

I installed 7.10 across the net, over the top of 7.04, which might have screwed things up a bit, because now I have no windows borders (with title bar etc.)  I've searched a lot for this and I found a number of workarounds, none of which have worked so far.

The ones I've tried so far (that I can remember) are:
In terminal:

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

Adding to xorg.conf under Section "Device":
```
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
Option "AddARGBGLXVisuals" "True"
Option "RenderAccel" "True"
Option "AllowGLXWithComposite" "True"
Option "backingstore" "True"
Option "TripleBuffer" "True"

```

Adding to xorg.conf at the bottom:
```
Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

I've also got the restricted drivers enabled, I've downloaded emerald window manager and tried that, with no luck.

If it's helpful, my PC has an nVidia 7900GTX graphics card.

Well, thanks for any help! (and apologies if this is in the wrong section)

---

### Post by DutyDuty on 2007-11-08
I know you've probably heard this before, but ```
emerald --replace
``` or ```
compiz --replace
```

---

