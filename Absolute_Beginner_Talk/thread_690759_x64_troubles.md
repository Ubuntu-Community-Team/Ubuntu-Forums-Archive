---
title: "x64 troubles"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Drathas on 2008-02-07
I'm having some kind of issue with KDM/GDM (whatever Ubuntu uses as it's default WM) wherein the window manager logs me out after a certain period of time.  It seems totally at random and I'm not even sure what is causing it.  I've looked over the current bugs and I see nothing similar.  I can't produce an Xorg log because it doesn't seem to log the occurrence of this.  In fact - X seems to be completely oblivious to this happening; the log basically just states that X has started up again it doesn't mention that it stops responding/whatever.

**EDIT:**

Actually - that's SUPPOSED to say "x86" I don't know why I typed x64 :)

---

### Post by shanepardue on 2008-02-07
Are you using Compiz by chance?

---

### Post by Drathas on 2008-02-09
If compiz-fusion is installed by default then.  I am currently using it right now as well by choice - is there something I should know about?

---

### Post by argie on 2008-02-09
Drathas, in the past when video effects that my graphics accelerator couldn't handle happened, the X server would die and restart. Try disabling video effects, or choosing only the minimal ones.

---

