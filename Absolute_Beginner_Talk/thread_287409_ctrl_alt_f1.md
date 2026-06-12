---
title: "ctrl alt f1"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by josh76 on 2006-10-28
When I press Ctrl alt f1 my screen goes black and stays that way can anyone help?

---

### Post by Dinerty on 2006-10-28
ctrl + alt + f1 takes you rto the cli (command line interface), this basically enables you to right raw commands in Ubuntu with no gui (graphical user interface).

Does it not as for your username/password?

---

### Post by lizzard on 2006-10-28
Try Alt-F7 to get back to your custom environment.

---

### Post by josh76 on 2006-10-28
I tried ctrl alt f7 the black screen remains.

---

### Post by josh76 on 2006-10-28
it doesn't ask for user name or password

---

### Post by az on 2006-10-28
In some cases, the framebuffer parameters for the monitor are whacked when you go to a virtual console and you get that.  It used to be common about five years ago (before xfree version 4) If you boot into recovery mode, everything works fine, correct? (you successfuly get to the console?)

This is a bug.  Can you please file a bug report (or add to an existing one)?  The package to file it with is xserver-xorg.

---

