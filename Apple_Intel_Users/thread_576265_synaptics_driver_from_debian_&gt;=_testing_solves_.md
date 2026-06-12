---
title: "synaptics driver from debian &gt;= testing solves minor trackpad woes"
date: 2007-10-15
forum: Apple Intel Users
---

### Post by vh1 on 2007-10-15
it adds an option called LockedDragTimeout that does what it suggests, if you have locked drags turned on, you can set the number of milliseconds so it releases itself (like how OSX handles things and how you wish synaptics in windows would)

but another thing I just noticed is that also like in OSX, you don't have to press two fingers simultaneously to trigger the scroll. now you can have one finger moving the mouse, then stroke a second finger down and it scrolls, instead of jumping over momentarily to the left or right

it works with the xserver found in gutsy, so if you've upgraded or for some reason running the new xorg in fiesty, it should install for you

you can [fetch it from one of the mirrors](http://packages.debian.org/lenny/xserver-xorg-input-synaptics/i386/download) to try it out

---

