---
title: "adding 'forward delete' and 'end' keys to numpad"
date: 2007-07-28
forum: Apple PPC Users
---

### Post by badcloud on 2007-07-28
tried adding the lines 'keycode  157=End;' and 'keycode  106= Delete;' to /etc/console-tools/remap

the plan? replacing the numpad 'help' key for a 'forward delete' key and the numpad '=' for 'end'

the result? xev shows: > KeyRelease event, serial 29, synthetic NO, window 0x2400001,
    root 0x45, subw 0x0, time 240187414, (545,649), root:(557,755),
    state 0x0, keycode 106 (keysym 0xff63, Insert), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

and

> KeyRelease event, serial 26, synthetic NO, window 0x2400001,
    root 0x45, subw 0x0, time 240264374, (559,655), root:(571,761),
    state 0x0, keycode 157 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

anyone? I'm sure I'm not the only one who despises the 'help' key

---

### Post by badcloud on 2007-07-29
c'mon, there's gotta be someone who knows this one and is willing to put in a few minutes to answer me...

---

### Post by hpp3 on 2008-06-12
Open a terminal and go:
```
xmodmap -e "keysym Insert = Delete"
xmodmap -e "keycode 157 = End"
```

I realize this is a very late answer, but I was looking for the answer myself and this is what I found.
Enjoy.

---

