---
title: "Emacs stuck in recording mode"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by mahalie on 2007-08-17
Total noob move here, I started editing something in Emacs, tried to quit and did something wrong.
Now I'm in --recording mode and can't exit.
Ctrl + X, Ctrl + C does nothing and I tried Ctrl + (, that means shift + 9 right? to stop recording and it didn't work.  

ACK!!! Can someone hand me a clue. I'm reading emacs command guides but they aren't helping.

:mad:

-I just got Ctrl + Z to stop it, so now how do I end/kill that buffer w/o saving??

Sorry, I don't even know if buffer is the right term.

---

### Post by mali2297 on 2007-08-17
Type
```

pkill emacs

```
in the terminal to kill emacs (without saving).

If you instead want sort things out first, type *fg* to come back to emacs.

---

