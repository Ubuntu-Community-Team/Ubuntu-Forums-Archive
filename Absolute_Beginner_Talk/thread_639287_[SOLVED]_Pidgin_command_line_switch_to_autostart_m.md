---
title: "[SOLVED] Pidgin command line switch to autostart minimized? Sessions &amp;gt; Start Up Progr"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by snuffy on 2007-12-13
I have put Pidgin in my Sessions > Start Up Programs to autostart when i boot my PC.

I would like it to start pidgin minimized to the tray, i.e. withouth the buddy list on the desktop. can i do this by adding a switch to the command in Start Up Programs?

NB. I have tried the 'extended preferences' plugin that should do this, but it had no effect when starting from the Start Up Programs command line.

Many thanks for your help.

Tim.

---

### Post by pHreaksYcle on 2007-12-15
As far as I know, Pidgin will start minimized to tray if it was minimized to tray when it was last exited. So, tray it before you shutdown. Hope this helps and gl.

---

### Post by snuffy on 2007-12-15
you would think so yes... but no. it doesn't.



> **pHreaksYcle said:**
> As far as I know, Pidgin will start minimized to tray if it was minimized to tray when it was last exited. So, tray it before you shutdown. Hope this helps and gl.

---

### Post by SanskritFritz on 2008-01-16
At least once, you have to exit Pidgin properly before shutdown. The reason is, that the shutdown does not ask Pidgin to exit gracefully, but forces it to exit, thus Pidgin is unable to write its settings.

---

### Post by snuffy on 2008-02-13
thanks, that did it.

---

### Post by SanskritFritz on 2008-02-13
> **snuffy said:**
> thanks, that did it.Great :-)

---

