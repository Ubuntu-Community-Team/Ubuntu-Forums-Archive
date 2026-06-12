---
title: "right side ctrl/alt non-responsive"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by TriNitro on 2007-04-03
It's not necessarily a big problem, but none of the keys to the right of the spacebar work.  The ctrl, alt, and super keys aren't apparently mapped.  How do I go about configuring my keyboard so that I can use those keys?

---

### Post by TriNitro on 2007-04-03
btw, I just use a standard PS/2 keyboard.

I also noticed this in my xorg configuration file:
```
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    **Option         "XkbOptions" "lv3:ralt_switch"**
EndSection
```

that wouldn't have anything to do with it would it?

---

### Post by TriNitro on 2007-04-03
OK, I got it to work, not sure what did it, but I went into keyboard preferences, found my specific keyboard and I also changed the setting in layout options>Third Level Choosers from "Press right ALT key to chose 3rd level" to "Press right WIN-key to choose 3rd level" and then I had to make sure the first box was unchecked.

Apparently, the Right Alt is the default third level chooser (whatever that is...anyone?) so unless you choose something else, it will remain as the right alt.  FWIW

---

