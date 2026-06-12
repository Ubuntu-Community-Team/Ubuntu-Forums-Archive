---
title: "Lost in Terminal"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by pcflunkies on 2007-01-25
I can run some things from the prompt, although I can't figure out how to change / find the directory I am in. I am not sure what to try here is what my prompt looks like. As an example I tried to get to the desktop and tried cd desktop, but no such directory found.

stupidav@Ubuntu-1:~$

---

### Post by pay on 2007-01-25
Linux is case sensitive so to change to the desktop you would need to ```
cd Desktop # or
cd /home/<user>/Desktop
```

---

### Post by meng on 2007-01-25
the bit after the : tells you which directory you are in, namely ~ (/home/stupidav)
otherwise, you can enter the command: pwd, it will tell you which directory you are in (print working directory)
change directory is cd, e.g.
cd Desktop
(will take you to ~/Desktop, aka /home/stupidav/Desktop)

---

### Post by pcflunkies on 2007-01-25
Thank you guys, I am not sure what I must of done, I thought I watched my Caps, but I must not of or something, 

Thanks again, especially for the quick response!

:guitar:

---

