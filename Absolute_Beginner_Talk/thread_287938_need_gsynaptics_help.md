---
title: "need gsynaptics help"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-10-29
i'm getting this error message when trying to turn off tapping - [i]GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics[/i]

i opened xorg.conf and found

[i]Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection
[/i]

would i enter that element myself? and, if so, where would i put it?

---

### Post by meng on 2006-10-29
Add the line
Option "SHMConfig" "true"

in that section.

---

### Post by fuscia on 2006-10-29
> **meng said:**
> Add the line
Option "SHMConfig" "true"

in that section.

that did it. thanks.

---

