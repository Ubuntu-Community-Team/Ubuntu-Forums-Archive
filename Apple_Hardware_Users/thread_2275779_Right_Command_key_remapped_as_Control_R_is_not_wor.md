---
title: "Right Command key remapped as Control_R is not working"
date: 2015-04-28
forum: Apple Hardware Users
---

### Post by Zorgoth on 2015-04-28
Several months ago when I acquired this Macbook Pro, I followed some guide that I've never been able to find to map my command keys to behave like control keys and the control key to behave like a super key. I do not know what file I changed to do this and have never been able to find it. I am using Ubuntu 14.04.

My problem is that while the Control->Super and Command_L->Control_L work fine, my right command key does nothing. I want it to work as a control key as well.

Xev says that the right command key is Control_R, but the event notification has a line that isn't present in the Control_L notification, as you can see:

```

KeyRelease event, serial 37, synthetic NO, window 0x6600001,
    root 0xb0, subw 0x0, time 2716783, (-51,487), root:(1658,539),
    state 0x4, keycode 133 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x6600001,
    root 0xb0, subw 0x0, time 2720678, (126,326), root:(1835,378),
    state 0x0, keycode 134 (keysym 0xffe4, Control_R), same_screen YES,
    XKeysymToKeycode returns keycode: 105
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

---

