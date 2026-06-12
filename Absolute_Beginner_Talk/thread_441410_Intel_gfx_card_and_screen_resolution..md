---
title: "Intel gfx card and screen resolution."
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by drwindow on 2007-05-12
How do I set my intel chipset into 1280X800 resolution?

So far this is the only thing preventing me from installing feisty fawn....

---

### Post by mejy on 2007-05-12
Assuming you've got X running, run 'sudo dpkg-reconfigure xserver-xorg -p high' in the terminal and select the resolutions you want.

---

### Post by drwindow on 2007-05-12
What do you mean by X?

---

### Post by mejy on 2007-05-12
If you have anything graphical (ie.  not white text on black) running, you've got X.  You can run that command by going to Applications -> Accessories -> Terminal.

---

### Post by RSingh on 2007-05-12
Screen Resolution option is available in System > Preferences > Screen Resolution.

---

### Post by drwindow on 2007-05-12
I know, but the resolution I want isn't listed in the 3 scroll down options.

And yes, apparently I do have X.

---

### Post by mejy on 2007-05-13
Please try running the command that I mentioned in my first post - that should fix your problem.

---

