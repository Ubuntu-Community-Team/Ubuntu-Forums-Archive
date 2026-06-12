---
title: "Apple wired keyboard Print Scr key"
date: 2009-01-22
forum: Apple Hardware Users
---

### Post by genti on 2009-01-22
I am using Ubuntu 8.10 and I am trying an Apple wired keyboard.
I love the feel of the keys but the layout is the problem.

I am having a problem with the Print Scr key.
This is **NOT** the numeric pad lock or the Fn lock issues covered in two bug reports with Launchpad.

I followed the guide here [https://help.ubuntu.com/community/AppleKeyboard](https://help.ubuntu.com/community/AppleKeyboard) and I was able to do almost all what I wanted.

I mapped the F14 key to Print Screen but the problem is that when I press it the print screen does not happen.

I tried xev and this is what I get when I press the F14:
KeyRelease event, serial 34, synthetic NO, window 0x3400001,
    root 0x13b, subw 0x0, time 1661372, (-1801,207), root:(348,1599),
    state 0x12, keycode 192 (keysym 0xff61, Print), same_screen YES,
    XKeysymToKeycode returns keycode: 107
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

On the other hand this is what happens if I press the Print Screen on another keyboard (that works as it should):
MappingNotify event, serial 34, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

MappingNotify event, serial 34, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 247

FocusOut event, serial 34, synthetic NO, window 0x3400001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 36, synthetic NO, window 0x3400001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 36, synthetic NO, window 0x3400001,
    mode NotifyNormal, detail NotifyNonlinear

PropertyNotify event, serial 36, synthetic NO, window 0x3400001,
    atom 0x159 (_NET_WM_ICON_GEOMETRY), time 1670887, state PropertyNewValue

FocusIn event, serial 36, synthetic NO, window 0x3400001,
    mode NotifyNormal, detail NotifyAncestor

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

PropertyNotify event, serial 36, synthetic NO, window 0x3400001,
    atom 0x159 (_NET_WM_ICON_GEOMETRY), time 1675627, state PropertyNewValue

FocusOut event, serial 36, synthetic NO, window 0x3400001,
    mode NotifyNormal, detail NotifyNonlinear

I tried System>Preferences>Keyboard shortcuts and Print is mapped as the shortcut and the system recognised F14 as Print Screen, it just does not ...print.

Any Ideas?

---

### Post by ZOMGxuan on 2009-06-29
I'm bumping this because I realised I had the same problem.
This older thread seems to describe the same problem:
[http://ubuntuforums.org/showthread.php?t=876725]("http://ubuntuforums.org/showthread.php?t=876725")

Restated, the problem is that even though the system detects F14 being pressed down as Print Screen being pressed down (i.e. both Keyboard Shortcuts preferences and Compiz Config Settings Manager recognize F14 as Print), pressing down F14 has no actual effect. The dialog for gnome-screenshot does not pop-up, even if F14 is held down for a long time.
Taking a screenshot works if the keyboard shortcut for gnome-screenshot is changed to a normal key like Space or A, but does not work if it is changed to F13 (mapped to Insert in xmodmap) or F15 (mapped to Scroll Lock in xmodmap), so it seems that this set of function keys are afflicted by a similar problem.

Referring to the community documentation for Apple Keyboards at [https://help.ubuntu.com/community/AppleKeyboard](https://help.ubuntu.com/community/AppleKeyboard) turns up this:
> Ubuntu 9.04 (Jaunty Jackalope)

Since Xmodmap have been replace by X Keyboard Extension, it's impossible to use Xmodmap to proceed with the mapping. Configuration can be done using the Keyboard preference tool. 

So does this mean xmodmap no longer works in Jaunty? Strange, because following the guide for Intrepid Ibex allows me to map F18 to summon the calculator, but I am running Jaunty. Also, the documentation does not state *how* such configuration can be done with the Keyboard preference tool.

---

### Post by ZOMGxuan on 2009-06-29
As a workaround to this, I suggest setting the Take Screenshot shortcut to something like F12 or <Alt> F12. I originally tried to map F16-F19 to PrintScr, but none of these work. F16-F19 work when mapped to keys like XF86Calculator, in that they were able to summon the calculator when pressed. F13-F15 work neither with this nor with PrintScr. So we have two very strange problems here. Does PrintScr have some sort of special behaviour in X.org?

---

