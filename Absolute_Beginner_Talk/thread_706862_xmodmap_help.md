---
title: "xmodmap help"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by trr135 on 2008-02-24
I'm working on an IBM think pad which lacks a windows key (which I usually use as a super key). So I've tried mapping another unused key on my keyboard to be super with out much success. I've done some searching, from which I've use xev to identify the keycode as 233. I created a file in my home directory named .Xmodmap which contains the string "keycode 233 = Super_R". After restarting X I used xmodmap -pk to verify the key was mapped correctly. But when I press the key it still does not function as a Super key. Any advice would be greatly appreciated

---

### Post by hugmenot on 2008-02-24
Run "xev", hover over the white window and then press your key. Does it say Super_R?

---

### Post by trr135 on 2008-02-25
Here is what I get from xev:

KeyPress event, serial 31, synthetic NO, window 0x3200001,
    root 0x63, subw 0x0, time 1397075295, (-266,341), root:(408,390),
    state 0x0, keycode 233 (keysym 0xffec, Super_R), same_screen YES,
    XKeysymToKeycode returns keycode: 116
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x3200001,
    root 0x63, subw 0x0, time 1397075295, (-266,341), root:(408,390),
    state 0x40, keycode 233 (keysym 0xffec, Super_R), same_screen YES,
    XKeysymToKeycode returns keycode: 116
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

---

### Post by hugmenot on 2008-02-25
Looks like it does map as you set it to. Did you try Super_L?

---

### Post by trr135 on 2008-02-25
Yes I have tried both but to no avail. For the mean time I've remapped one of my alt keys to verify that I'm not missing something, and it works fine.

---

### Post by stairwayoflight on 2008-06-09
How about:

```

keycode 233 = Super_R
add Super = Super_R
```

I remapped my Menu key to Control_R, but it wouldn't work till I added "add Control = Control_R".

---

