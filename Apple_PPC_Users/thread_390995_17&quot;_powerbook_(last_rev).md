---
title: "17&quot; powerbook (last rev)"
date: 2007-03-22
forum: Apple PPC Users
---

### Post by CrazyP on 2007-03-22
Thanks for all the help so far in these forums.  I have a couple issues I still can't seem to fix.  First, I want to disable the tap buttons on the track pad, I manage to random select and paste items and it is annoying.  But, I want to keep the scrolling feature, if at all possible.  Here is my xorg config:

<code>
Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/input/appletouch"
Option "Protocol" "auto-dev"
Option "LeftEdge" "50"
Option "RightEdge" "900" # max 950
Option "TopEdge" "30"
Option "BottomEdge" "304" # max 334
Option "FingerLow" "15"
Option "VertScrollDelta" "30"
Option "HorizScrollDelta" "30"
Option "EdgeMotionMinZ" "30"
Option "EdgeMotionMaxZ" "160"
Option "EdgeMotionMinSpeed" "1"
Option "EdgeMotionMaxSpeed" "400"
Option "EdgeMotionUseAlways" "false"
Option "MinSpeed" "0.6"
Option "MaxSpeed" "1.0"
Option "AccelFactor" "0.09"
Option "LockedDrags" "false"
Option "CoastingSpeed" "1"
EndSection
</code>

Also, my screen random flickers and I am not sure why.  I have the Mobility Radeon 9600 as my vid card.   It isn't to bad, i would like to fix it, so any help would be great.

Thanks.

---

