---
title: "How do I disable horizontal scroll, with scroll wheel?"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by neurostu on 2008-03-03
I have a Thinkpad T61 and I have set up my "joystick" mouse to work as a scroll wheel when I press my middle button.  However, the horizontal movement is really sensitive and i hate that it scrolls horizontally when I just want to scroll vertically.

Here is what my xorg.conf looks like (custom section needed to add the scrolling functionality)
```

#Trackpoint
Section "InputDevice"
  Identifier	"Configured Mouse"
  Driver	"mouse"
  Option	"CorePointer"
  Option        "Device" "/dev/input/mice"
  Option	"Protocol"	     "ImPS/2"
  Option	"ZAxisMapping"	     "4 5"
  Option	"Emulate3Buttons"    "true"
  Option	"EmulateWheel"	     "on"
  Option	"EmulateWheelButton" "2"
  Option	"YAxisMapping" 	     "4 5"
  Option	"XAxisMapping"	     "6 7"
EndSection

```

Does anybody have any ideas as to how I can disable the horizontal scrolling but leave the verticle scrolling intact?

---

### Post by happyhamster on 2008-03-03
- You'll have to comment the: Option  "XAxisMapping"  "6 7" line by putting a # before it.

> 
#Trackpoint
Section "InputDevice"
  Identifier	"Configured Mouse"
  Driver	"mouse"
  Option	"CorePointer"
  Option        "Device" "/dev/input/mice"
  Option	"Protocol"	     "ImPS/2"
  Option	"ZAxisMapping"	     "4 5"
  Option	"Emulate3Buttons"    "true"
  Option	"EmulateWheel"	     "on"
  Option	"EmulateWheelButton" "2"
  Option	"YAxisMapping" 	     "4 5"
#  Option	"XAxisMapping"	     "6 7"
EndSection


- Another try is setting the sensitivity, by adding a line:

Option "EmulateWheelInertia" "20"

(10 = default value). This will affect the vertical movement as well though. Good luck.

---

### Post by stooshbunutu on 2008-03-03
System >> Preferences >> Mouse

There will be (on one of the tabs) checkboxes for Horizontal and vertical scrolling

---

### Post by neurostu on 2008-03-03
stooshbuntu, I have the horizontal scrolling box unchecked but that only works for the trackpad not the joystick...

happyhamster, i'll try that out. thanks!

---

### Post by neurostu on 2008-03-03
Happyhamster, that did it, thanks!

Is it possible to emulate the inertia in one axis?

---

### Post by happyhamster on 2008-03-04
> **neurostu said:**
> Is it possible to emulate the inertia in one axis?
I don't think so (at least not by editing xorg.conf). If anyone knows a way of doing that: I'd be very interested as well :)

---

### Post by dnquark on 2008-03-05
Hate to be a "me too" type poster, but I'd really like to see this ability.  By default, Firefox uses buttons 6,7 which I mapped to trackpoint X axis as back/forward, which is exactly what I want.  However, when I scroll, if my pressure on the trackpoint has even the slightest X component, it triggers the back/fwd buttons :(

Independent "wheel inertia" settings for the axes might be one way to solve this, although it would be more robust to capture the effective angle of the pointer's motion and generate the button presses according to the angle.  Sounds like it would be straightforward to implement...  for someone that's into hacking Xorg stuff...  Hope it gets done sooner or later.

---

### Post by neurostu on 2008-03-05
dnquark, you can actually disable the left and right scroll. That was the first thing I disabled when I got my joystick working.

to disable that type the following address into your URL Bar:
```

about:config

```
then set the following settings 
```

mousewheel.horizscroll.withnokey.sysnumlines   to  true
mousewheel.horizscroll.withnokey.action    to  0

``` 
and then your horiz scroll back forward will be disabled.

---

### Post by dnquark on 2008-03-05
Hm, so this does disable the horizontal scrolling with the joystick, but it also disables the back/forward behavior, so the net effect is the same as when one disables XAxis scrolling in xconf.

I still think that the X/Y scrolling wheel emulation needs to be improved on a fundamental level.  Right now, it is tied to how far cursor would move if you were just using a mouse.  For instance, if you press the trackpoint down and just a little to the right, it might generate 10 button 5 events and 1  button 7 event, corresponding to 10 clicks of "up/down" scroll wheel and 1 click of (hypothetical) "left/right" scroll wheel.  Clearly, this is not what you want in most situations: you either want to use one or the other, and cross-coupling them screws up the intended behavior.

---

### Post by neurostu on 2008-03-05
I'm not sure what you mean when you say this disables back/forward behavoir?  I have those options set on my T61 and then I mapped - to back and = to forward using a plugins called "function keys for keyconfig" and "keyconfig" and I can scroll back and forward all I like. 

I previously had back and forward mapped to the browse keys on my t61( the two keys by the arrow keys) but I now use those to switch desktops. I like using - and = better anyway b/c  i can see them without moving my  right hand, they're easier to hit then the browse buttons,  and I don't have to pull my hand off the keyboard to get to them.

But I agree that the X/Y Scrolling needs to be improved. (seperate thresholds and inertias for the two axis)

---

### Post by EReckase on 2008-06-04
> **neurostu said:**
> dnquark, you can actually disable the left and right scroll. That was the first thing I disabled when I got my joystick working.

to disable that type the following address into your URL Bar:
```

about:config

```
then set the following settings 
```

mousewheel.horizscroll.withnokey.sysnumlines   to  true
mousewheel.horizscroll.withnokey.action    to  0

``` 
and then your horiz scroll back forward will be disabled.

I've done this change to about:config, and I *still* get forward and back with the small buttons on my Logitech Marble Mouse.  Any ideas on why it still happens?

---

