---
title: "keyboard layout problem on an ibook g4 with ubuntu 10.04"
date: 2010-08-24
forum: Apple Hardware Users
---

### Post by Wesleytf on 2010-08-24
I've always been tempted by linux and am finally giving it a try on an  ibook G4.  It is the 1.3ghz 12" model, with 1.5g ram.  I've done a few of the fixes (wireless, heat), and it's doing amazingly well so far, except I seem to have lost the control key.  I have tried updating the keyboard layout and that changes nothing.  I tried changing the capslock to function as a control key, but nothing I'm doing is giving me any control key anywhere.  I'm not a box of rocks, but I've never really programmed before this (unless mathematica counts), so be easy on me.

---

### Post by Wesleytf on 2010-08-26
bump!  anyone?

---

### Post by linuxopjemac on 2010-08-26
You can read through this post:
[http://mac.linux.be/content/tuning-ubuntu-macintosh-key-mapping-and-3-mouse-button-emulation-0](http://mac.linux.be/content/tuning-ubuntu-macintosh-key-mapping-and-3-mouse-button-emulation-0)

---

### Post by Wesleytf on 2010-08-27
I've been trying quite a few things with xmodmap and I'm unsure why none of it is working...  when I use the command

  ```
 $ xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'
```

I can see that theI have correctly modified the left command (133) to Control_L, but it does not function as such--at least I can't copy/paste, get a new tab in firefox, etc.  Also, when I get no response when I press the actual control key or the function key.  However, the function key does work if I want to, say, change the brightness (fn-F1).  Anyone have any idea what the heck is going on?

---

