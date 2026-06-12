---
title: "Feisty Terminal won't open!"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Irwin J. Finster on 2007-04-24
Hi,

I just installed Feisty, and when I go to the menue entrey for terminal, I get the message on the bottom panel of the screen 'Terminal is Starting' (translated from german) but nothing happens.

Any ideas of what I could try?

Thanks,

Irwin

---

### Post by Spr0k3t on 2007-04-24
For now, disable desktop effects and beryl if you have that installed.  The problem is related to compositing of the terminal on some graphics cards.  There's a single line you can add to the xorg.conf but I don't know it off the top of my head (not at home).  I had the same issue and this post here fixed it el pronto:

[http://ubuntuforums.org/showpost.php?p=2421298&postcount=2](http://ubuntuforums.org/showpost.php?p=2421298&postcount=2)

In the interim, if you need a terminal you can always do alt-f2 xterm.

---

### Post by Vorian on 2007-04-24
*moved to the beginners forum*

---

