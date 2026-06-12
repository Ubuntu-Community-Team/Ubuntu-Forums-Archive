---
title: "Right shift as Delete key - keydown issue"
date: 2011-02-01
forum: Apple Hardware Users
---

### Post by new-num-order on 2011-02-01
I have macbook pro 2,1 and Karmic. I remapped right shift to delete by adding this command to startup apps:
```
xmodmap /etc/X11/Xmodmap
```

And I wrote this in the above Xmodmap file:
```
keycode 62 = Delete
```

It works alright, but it deletes just one character on each keypress. I want it to delete characters continuously when I'm holding the key down for a longer period of time. In other words, I want it to behave the same way backspace does but deleting in other direction instead.

Is there another keyname for Delete that does?

Thanks in advance!

---

