---
title: "Macbook Air 11&quot; Alt key"
date: 2016-12-12
forum: Apple Hardware Users
---

### Post by anandamide on 2016-12-12
Hoping someone can help me with a relatively straightforward solution to a niggling problem

After installing Ubuntu 16.04 on my 2013 Macbook Air I find I'm unable to switch to virtual terminals. After a bit of digging I find this is because the left alt key is 'incorrectly' bound to Level3_Shift

```

KeyPress event, serial 37, synthetic NO, window 0x3e00001,
    root 0xd6, subw 0x0, time 1930533, (-435,387), root:(362,439),
    state 0x0, keycode 64 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

I can correct this to an Alt_L binding by using

```
xmodmap -e 'keycode 64=Alt_L'
```

However once I log into e.g. tty1 then back into X, this keybinding is lost.

Note this isn't an issue with logging in to an X session - I have a script which runs every login to switch the key binding. It's an issue with switching back into X from a VT

---

### Post by slickymaster on 2016-12-12
*Thread moved to **Apple Hardware Users**.*

---

