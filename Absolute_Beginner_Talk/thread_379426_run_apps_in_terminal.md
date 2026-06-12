---
title: "run apps in terminal"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2007-03-08
ok so here is a dummy question :) is there any way to run a program through terminal which after is executed stays independently? i mean if you run in terminal sudo nautilus starts nautilus but terminal is actually logging what happens with nautilus if i can say so... further if i close terminal application ends too; any ideas?

---

### Post by Ferri on 2007-03-08
It's not terminal, but may be if you use alt-F2 and enter the command there you'll have the effect you're asking for.

---

### Post by K.Mandla on 2007-03-08
Usually if you append the command line with an ampersand, it'll background the application and you can close the terminal safely. Like this:

```
sudo nautilus &
```

:D

---

### Post by dstew on 2007-03-08
This comes up with a number of applications that use the terminal as their primary user interface. For example, if you use the program X-board to play chess on the internet, the terminal window stays open to communicate with the chess server. If you need another terminal window, just open another one (start another instance) by double clicking the menu icon. Both terminal windows open and act independently.

---

### Post by mcduck on 2007-03-08
You can use 'nohup' to allow apps to stay open when you start the from a terminal. If you also want it to run in background add  '&' to end.of the command.

For example 'nohup xmms &' would start xmms, leave the terminal usable for other purposes and in case the terminal is closed xmms would keep running.

---

