---
title: "Logitech G7 and those pesky thumb buttons / Firefox"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by seanmcgpa on 2007-04-29
Installed 7.04 (and loving it - thanks guys!) but Swiftfox treats my thumb "back" button as just a regular mouse click (I can use it to click a link instead of an Alt + Left combo).

I have a Logitech G7.

Have tried editing xorg.conf a bunch of times .. first with:

```
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "true"
    Option "Buttons" "7"
    Option "ButtonMapping" "1 2 3 6 7"
    Option         "ZAxisMapping" "4 5"
```

Then with :

```
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice" 
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5 7 8"
    Option         "Emulate3Buttons" "no"
    Option         "Buttons" "8" 
    Option         "ButtonMapping" "1 2 3 4 5"

```

then finally with : 

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "Protocol"              "evdev"
        Option          "Dev Name"              "Logitech USB Receiver"
        Option          "Device"                "/dev/input/mice"
        Option          "Buttons"               "8"
        Option          "ZAxisMapping"          "4 5 7 8"
EndSection

```

Mouse works fine in all 3 instances when I restart X, but no joy with the back button.  I did indeed Google around and found some extensive discussions about Edgy and installing all sorts of programs .. but I really just want to map Button 8 (the thumb button) to Alt-Left.  Is there an easy way for a nub to do this?

By the way, when I press the back button xev reports : 

```
EnterNotify event, serial 30, synthetic NO, window 0x3600002,
    root 0x21b, subw 0x0, time 6559632, (33,41), root:(1646,159),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  27  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 30, synthetic NO, window 0x3600002,
    root 0x21b, subw 0x3600003, time 6559867, (33,41), root:(1646,159),
    state 0x0, button 8, same_screen YES

LeaveNotify event, serial 30, synthetic NO, window 0x3600002,
    root 0x21b, subw 0x0, time 6559867, (33,41), root:(1646,159),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0

```
Thanks

Sean

---

### Post by max_croft on 2007-10-19
I'm bumping this as I have the same mouse and the same issue.

---

