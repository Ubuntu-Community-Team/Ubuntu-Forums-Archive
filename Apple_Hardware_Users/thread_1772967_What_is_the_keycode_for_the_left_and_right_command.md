---
title: "What is the keycode for the left and right command keys IN NATTY?"
date: 2011-06-01
forum: Apple Hardware Users
---

### Post by unagimiyagi on 2011-06-01
Anyone know?  Obviously I'm trying the low-level way of remapping command to control for my macbook pro.
Currently, the command keys are mapped to the windows key (super key, I think).  Is that screwing up xev's output?

Running xev from a terminal window, I'm getting:

```
KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

PropertyNotify event, serial 36, synthetic NO, window 0x4200001,
    atom 0x161 (_NET_WM_ICON_GEOMETRY), time 2164950, state PropertyNewValue
```
I may have missed a line or two, but where is the magic keycode words?

By contrast, clicking the right alt key, for example, gives me this:

```
KeyRelease event, serial 36, synthetic NO, window 0x4200001,
    root 0x15a, subw 0x0, time 2253381, (-594,671), root:(1120,724),
    state 0x8, keycode 108 (keysym 0xffea, Alt_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

So the right alt has a keycode of 108, and if I wanted to map it to the right control, I would add to my xmodmap keycode 108 = Control_R



Thanks!

---

