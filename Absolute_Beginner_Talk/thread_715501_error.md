---
title: "error"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by P0CKETS on 2008-03-04
In gnome, I am getting an error whenever I press the caps lock key.
Bad key or directory name: "/desktop/gnome/peripherals/keyboard/host- The Box/0/numlock_on": ` ' is an invalid character in key/directory names

This started after I tried running nautilus in fluxbox, which has yet to work. It seems to hang the system every time I try to run the program. How can I fix this?

---

### Post by JoshuaRL on 2008-03-04
Could you try:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```

That will reconfigure it, but paying attention to the keyboard and other things.

---

### Post by P0CKETS on 2008-03-04
Did not work.

---

