---
title: "remapping a key"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by zantzinger on 2007-08-30
My Q key is broken so I like to switch it with the ` key (top left beneath Escape). Where is xmodmap in GNOME? I installed xkeycaps via synaptic and was expecting that to be some sort of GUI for xmodmap, but maybe it isn't. Or would anyone tell me how to write teh command for xmodmap (a simple swap) so I can maybe do it through the terminal

---

### Post by felicity on 2007-08-30
I could be wrong, but I believe you can do that in /usr/share/xmodmap.std

---

### Post by felicity on 2007-08-30
OK I just tested it and it works.

the line you want is
```
keycode 49 = q
```

(assuming your keyboard isn't special.., if it is test it by typing xev in a terminal and pressing the key you want, then look at the output for that key in the terminal.. the keycode is what your looking for.. should be 49 for the key you mentioned)

---

