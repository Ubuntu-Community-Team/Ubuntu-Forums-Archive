---
title: "Macbook Pro 10.1 (Retina) power consumption"
date: 2013-04-15
forum: Apple Hardware Users
---

### Post by sauferkel on 2013-04-15
Hey guys,

since the the retina macbook is running quite nice with the latest ubuntu builds (using kernel 3.8.0.18 atm) , i started thinking about lowering the power consumption of this thing. I know there are already two threads about the hardware, but more on other issues so i guess wo could collect power related issues here....

I use the Gnome-shell as a desktop environment and i'm just on IntelGPU. I also get down to about 13 watts with wifi off, and panel brightness on low.

What values do you get ?


Using the options powertop offers, it gets down another watt, or two. Is there a way to make these permanent? 

The option to disable the screen at all, when not using the laptop, then brings my laptop down to 6,5-7 watts, even with wlan on, and apps running (firefox,thunderbird,skype,pidgin). This is pretty awesome, i guess. Brings me to estimated "runtime" values of 12 hours. (Osx gets 18! there, but okay ;) )


Let me know ;)

sauferkel

---

### Post by ksatta1 on 2013-04-15
Good thread :) Hmm, 7W without the screen heh :D I still have to test a couple of days, but I'm quite happy with 210.x nvidia drivers, fans are not running all the time like before etc. It probably does lower the battery runtime when you're actually doing something on the screen (I mean vs. Intel only), but anyway it has dropped from 24W when idling to 13W when idling (with nvidia), amazing :) And I also have the external outputs working etc, which is great. One day I might test compiling the kernel with the apple-gmux changes to get switching working without OSX. Also you need to have different xorg.conf etc when using nvidia or intel, so it would take some time to do all the scripts etc.

---

### Post by MikeBraxner on 2013-04-16
> **sauferkel said:**
> Using the options powertop offers, it gets down another watt, or two. Is there a way to make these permanent?

[This post]("http://ubuntuforums.org/showthread.php?p=12532036#12532036") explained how to do just that, but do take note of the edit ... it might save you a nasty headache ;-)

---

### Post by sauferkel on 2013-05-07
Found some further minor tweaks if using intel graphics, add them as boot commands:
i915.i915_enable_fbc=1
i915.lvds_downclock=1
drm.vblankoffdelay=1


Brings my machine down another watt, to about 9,2 in idle, wlan off and display on low.

Source: 

[https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks](https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks)

---

