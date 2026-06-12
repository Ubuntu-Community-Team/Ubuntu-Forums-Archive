---
title: "[SOLVED] What is XV, XAA, and EXA?"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by slughappy1 on 2008-02-19
I have a black listed video card for Compiz [http://wiki.compiz-fusion.org/Hardware/Blacklist]("http://wiki.compiz-fusion.org/Hardware/Blacklist")
I am curious what "XV does not play with XAA under compiz, only with EXA" means. What is XV, XAA, and EXA? I think I've read that Hardy has EXA, is that true?

---

### Post by northern lights on 2008-02-19
XV simply stands for "X video extension", which in turn is an extension of X11 (your display protocol) to rescale video output (e.g. watch a divX movie in fullscreen).

XAA and EXA are graphics acceleration architectures providing 2D hardware acceleration for X, where XAA the initial architecture now to be replaced by EXA.

As far as I know gutsy can run on EXA also, should be able to set that in your xorg.conf - I'll let you know should I find out where and how.

---

### Post by slughappy1 on 2008-02-21
Thank you

---

