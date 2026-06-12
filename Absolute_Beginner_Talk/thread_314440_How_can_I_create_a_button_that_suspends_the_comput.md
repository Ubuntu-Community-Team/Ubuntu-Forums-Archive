---
title: "How can I create a button that suspends the computer?"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by jsully1 on 2006-12-07
I'm looking to make a button on my top panel that directly suspends the computer.  Any ideas?

A helpful member pointed out that gnome-session-save --kill opens the quit menu, which is helpful, but I was wondering if I could go that extra bit further!

---

### Post by CatKiller on 2006-12-07
```
gdm-signal -s
``` should do it. I probably shouldn't have tried it on a computer that doesn't support it, though :roll:

The useful options are:

-z, --hibernate
-h, --halt
-s, --suspend
-r, --reboot

---

