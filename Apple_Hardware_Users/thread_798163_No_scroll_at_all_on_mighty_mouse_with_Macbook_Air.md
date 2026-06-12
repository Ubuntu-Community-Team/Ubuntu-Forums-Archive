---
title: "No scroll at all on mighty mouse with Macbook Air"
date: 2008-05-17
forum: Apple Hardware Users
---

### Post by Brightbelt on 2008-05-17
Hi, I'm using Ubuntu 8.04 and my bluetooth mighty mouse is detected ok and it works ok in many regards - I can even get a right-click just my pressing down on the right-front side of the mouse. 

What I can't do at all is scroll. The scroll just seems to not function. I'm not too concerned about left-right scrolling (I've searched already and I already know there's a thread on that).

I really do miss the vertical scrolling and it's relegated me to using a Logitech mouse so I can scroll. But that takes away my one (1) single Usb port. (I know the compromises made for "thinness" here - no big deal).

Can anyone show me or point me towards a fix for vertical scrolling? I appreciate any leads....

Many Thanks, Frank B.

---

### Post by The_Doctor on 2008-11-16
Bump.

Macbook Pro Penryn (4th generation), brand new (today) bluetooth mighty mouse. Everything but scroll and squeeze show up in evtest.

Relevant xorg.conf snippet:


Section "InputDevice"
    Identifier     "mmouse"
    Driver         "evdev"
    Option     "WHEELRelativeAxisButtons" "4 5"
    Option     "HWHEELRelativeAxisButtons" "7 6"
EndSection

---

