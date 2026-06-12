---
title: "Apple aluminum keyboard: disabling numlock"
date: 2008-08-01
forum: Apple Hardware Users
---

### Post by dhasenan on 2008-08-01
Hi all,

I'm using an Apple aluminum keyboard. As you may know, by default, the keypad doesn't work. The Clear key is mapped to numlock, and pressing it converts a portion of the keys to a number pad -- around the U/I/O keys.

I used xmodmap to enable the number pad:
```

keycode 157 = KP_Equal
keycode 79 = KP_7
keycode 80 = KP_8
keycode 81 = KP_9
keycode 82 = KP_Subtract
keycode 83 = KP_4
keycode 84 = KP_5
keycode 85 = KP_6
keycode 86 = KP_Add
keycode 87 = KP_1
keycode 88 = KP_2
keycode 89 = KP_3
keycode 90 = KP_0
keycode 91 = KP_Decimal

```

Still, if I accidentally hit the Clear key, I either have to hit numlock on my other keyboard or press F6 twice.

xev doesn't show any events when the key is pressed. Can I use xmodmap to disable or alter the behavior of numlock? If not, is there any other configuration change I can make to disable numlock?

---

### Post by dhasenan on 2008-08-01
I feel stupid.

```
keysym Num_Lock = Some_Other_Symbol
```

---

