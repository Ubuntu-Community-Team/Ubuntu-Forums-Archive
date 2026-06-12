---
title: "Keyboard Shortcuts..."
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by JcZndeR on 2006-04-22
I don't get it...  When the Keyboard Shortcuts say "0x??" ans stuff which button(s) are they corresponding to?

thx :)

---

### Post by Mustard on 2006-04-22
If it's got "0x??", then its probably referring to some special key on your keyboard, other than the usual alphanumeric keys.

If you want to find out what some of these keys return as a code, try installing xev.  Xev returns the codes for events with the mouse, keyboard etc.

```
sudo apt-get install xev
```

type *xev* in the command line and it will open a box. Press keys and you will see the keycodes returned in the terminal.  Keep your mouse pointer out of the window if you want to avoid getting a lot of feedback on mouse events.

---

### Post by JcZndeR on 2006-04-22
Thanks...
that helped
but why are some of the default shortcuts not on my keyboard?? :confused: 
i already have one of those mutimedia ones, and i still cant get some.
or atleast i havent found dem yet...

---

