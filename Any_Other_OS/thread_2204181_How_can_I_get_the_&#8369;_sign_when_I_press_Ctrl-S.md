---
title: "How can I get the &#8369; sign when I press Ctrl-Shift P?"
date: 2014-02-07
forum: Any Other OS
---

### Post by palawanbeach on 2014-02-07
Hello,
I'm traveling and I need to type the peso symbol &#8369; often. Is it possible to get the &#8369; character when I hold down Ctrl and Shift buttons and then pressing the letter P?

XEV output for capital P (Shift-P)

> KeyRelease event, serial 32, synthetic NO, window 0x2a00001,
    root 0xac, subw 0x0, time 234451112, (805,166), root:(808,214),
    state 0x11, keycode 27 (keysym 0x50, P), same_screen YES,
    XLookupString gives 1 bytes: (50) "P"
    XFilterEvent returns: False

XEV output for Ctrl-P:


> KeyPress event, serial 32, synthetic NO, window 0x3200001,
    root 0xac, subw 0x3200002, time 239787646, (54,31), root:(57,79),
    state 0x14, keycode 27 (keysym 0x70, p), same_screen YES,
    XLookupString gives 1 bytes: (10) ""
    XmbLookupString gives 1 bytes: (10) ""
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x3200001,
    root 0xac, subw 0x3200002, time 239787730, (54,31), root:(57,79),
    state 0x14, keycode 27 (keysym 0x70, p), same_screen YES,
    XLookupString gives 1 bytes: (10) ""
    XFilterEvent returns: False




XEV output for Shift-Ctrl-P

> KeyPress event, serial 32, synthetic NO, window 0x3200001,
    root 0xac, subw 0x0, time 239629660, (986,719), root:(989,767),
    state 0x15, keycode 27 (keysym 0x50, P), same_screen YES,
    XLookupString gives 1 bytes: (10) "[weird character. see screenshot below]"
    XmbLookupString gives 1 bytes: (10) "[weird character. see screenshot below]"
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x3200001,
    root 0xac, subw 0x0, time 239629730, (986,719), root:(989,767),
    state 0x15, keycode 27 (keysym 0x50, P), same_screen YES,
    XLookupString gives 1 bytes: (10) "[weird character. see screenshot below]"
    XFilterEvent returns: False




Screenshot for XEV output of Shift-Ctrl-P
[ATTACH=CONFIG]250154[/ATTACH]



xmodmap -pke | grep " 27 "
keycode  27 = p P r R

---

### Post by howefield on 2014-02-07
Peso sign in Unicode is : (U+20B1) so Ctrl+Shift+u.

An underlined u character will appear, then type in 2+0+B+1 and press enter.

---

### Post by palawanbeach on 2014-02-07
hello, howefield.
I'm aware of the unicode. but I didn't want to have to remember it. It's easier for me to just type Ctrl-Shift-P.

---

### Post by palawanbeach on 2014-02-14
bump

---

