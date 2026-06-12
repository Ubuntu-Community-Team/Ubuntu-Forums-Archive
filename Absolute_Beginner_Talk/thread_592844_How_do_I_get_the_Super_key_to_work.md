---
title: "How do I get the Super key to work?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-10-26
I'm trying to get the Super keyt to work in Compiz, have tried a variety of things after searching through the forums but I always get the same error message when I try to change various keyboard settings: 

> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10300000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

---

### Post by ddrichardson on 2007-10-27
What "things" have you tried? Most likely you have some entry in /etc/X11/xorg.conf in the input section that is causing the problem. Check that you super key works as a key and not by sending some bizarre escape character by opening a terminal and typing xev then hitting the super key. You should get an output along the lines of:```
KeyRelease event, serial 31, synthetic NO, window 0x3e00001,
    root 0x1a5, subw 0x0, time 3814867237, (-188,388), root:(486,439),
    state 0x40, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

---

### Post by mordantae on 2008-03-10
> **ddrichardson said:**
> What "things" have you tried? Most likely you have some entry in /etc/X11/xorg.conf in the input section that is causing the problem. Check that you super key works as a key and not by sending some bizarre escape character by opening a terminal and typing xev then hitting the super key. You should get an output along the lines of:```
KeyRelease event, serial 31, synthetic NO, window 0x3e00001,
    root 0x1a5, subw 0x0, time 3814867237, (-188,388), root:(486,439),
    state 0x40, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

Hi i'm looking around for help on how to get the super key working in my environment and the output of xev and superkey is as follows...can anyone help me find out what's wrong? 


```
KeyRelease event, serial 31, synthetic NO, window 0x4000001,
    root 0x1a5, subw 0x4000002, time 2576340349, (28,48), root:(699,104),
    state 0x10, keycode 115 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```


is it something to do with having NoSymbol as opposed to Super_L ? how do i map the super key to the left super button.?

any help would be GREATLY appreciated since this is really putting a damper on my compiz effects experience.

thanks

---

