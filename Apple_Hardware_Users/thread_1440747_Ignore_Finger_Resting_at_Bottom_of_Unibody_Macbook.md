---
title: "Ignore Finger Resting at Bottom of Unibody Macbook Pro Touchpad?"
date: 2010-03-27
forum: Apple Hardware Users
---

### Post by Pretz on 2010-03-27
I spent the last hour and a half googling for pointers, reading manpages, and trying synaptics settings to get my touchpad to work like it does in OSX on my unibody macbook pro.  I can't find anything that works.

What I want: Since my MBP 5,4 doesn't have a dedicated mouse button, I normally rest my thumb on the bottom section of the touchpad.  That way I can tap with my thumb while using my index finger to move the pointer.  OS X smartly ignores the fact that my thumb is resting on the touchpad, and lets me move the pointer as if my thumb weren't there. I can then use my middle finger for two finger scrolling, and everything magically works

On my nice shiny new install of Ubuntu 9.10, if I have my thumb *anywhere* on the touchpad, it registers as a two-finger scroll, thus making it impossible to move the pointer while resting my thumb on the touchpad.  Even if I disable two-finger scrolling, the cursor will not move with two fingers on the touchpad.  A passable solution would be disable two-finger scrolling detection in the lower part of my touchpad, or even disable the lower part of the touchpad completely.  A better solution would be to allow me to scroll into the lower portion, but not initiate a two finger scroll from the lower portion.

Synaptics settings that have not worked for me:
**AreaBottomEdge**: This disables moving the pointer from the bottom section of my touchpad, but does not disable two-finger scrolling from the bottom section.  This is essentially the exact *opposite* of what I want.
**BottomEdge**: This doesn't seem to have any relation to two-finger scrolling.  I haven't been able to get anything useful to come out of setting this.
These references haven't helped (although they are interesting):
[http://wiki.debian.org/MacBook#Touchpadforthenew2008unibodyMacbookandMacbookPro](http://wiki.debian.org/MacBook#Touchpadforthenew2008unibodyMacbookandMacbookPro)
[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic#Trackpad](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic#Trackpad)
[http://jjinux.blogspot.com/2009/09/linux-least-bad-synaptics-configuration.html](http://jjinux.blogspot.com/2009/09/linux-least-bad-synaptics-configuration.html)
[http://lucumr.pocoo.org/2007/11/13/two-finger-scrolling-on-ubuntu](http://lucumr.pocoo.org/2007/11/13/two-finger-scrolling-on-ubuntu)
[http://miteshjlinuxtips.wordpress.com/2009/05/22/macbook-pro-touchpad-synaptics-configuration-in-xorg-conf/](http://miteshjlinuxtips.wordpress.com/2009/05/22/macbook-pro-touchpad-synaptics-configuration-in-xorg-conf/)

I haven't been able to find any threads discussing this particular issue.  If you have a solution, share it!

Thanks!

---

### Post by kosumi68 on 2010-03-28
[http://ubuntuforums.org/showpost.php?p=8778094&postcount=268](http://ubuntuforums.org/showpost.php?p=8778094&postcount=268)
[http://ubuntuforums.org/showthread.php?t=947947](http://ubuntuforums.org/showthread.php?t=947947)
[http://ubuntuforums.org/showthread.php?t=950515](http://ubuntuforums.org/showthread.php?t=950515)
[http://ubuntuforums.org/showthread.php?t=1334696](http://ubuntuforums.org/showthread.php?t=1334696)

---

### Post by Pretz on 2010-03-28
Thanks for the pointer to that last thread!  I guess the answer is "it's possible but super super alpha"

I got it working using [http://bitmath.org/code/multitouch/](http://bitmath.org/code/multitouch/) and arturoc's ad-hoc additions to gestures.c from [http://ubuntuforums.org/showpost.php?p=8978021&postcount=34](http://ubuntuforums.org/showpost.php?p=8978021&postcount=34)

Thanks for all the hard work on multitouch drivers!

---

### Post by tomodachi on 2011-10-27
what about a similar feature for oneiric (11.10)
does one have to  re-apply it there? 

or it it natively supported nowdays?

---

