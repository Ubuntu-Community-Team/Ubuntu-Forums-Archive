---
title: "Start up Programs"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Nekiruhs on 2007-05-21
I recently added a few programs to my Start up programs under sessions, and when I disable them they still come up. Namely its devilspie xterm and amaroK. This gets really annoying and I would appreciate it if anyone could help.

---

### Post by mitch.c on 2007-05-21
I believe the .desktop entries can be found in ~/.config/autostart. Can you delete them there?

---

### Post by Nekiruhs on 2007-05-21
Their not there. But they still start up!

---

### Post by Ateo on 2007-05-21
In addition to disabling the program from 'Startup Programs', you also need to remove it from the current session. That can be found in the next tab over 'Current Session'. Find it in there, remove it, click the Apply button. Then, to be safe, go into the 'Session Options' tab and just click on the 'Save the current session' button.

Don't forget, you need to also disable it.

---

### Post by Nekiruhs on 2007-05-21
Thanks, that did it, kept forgetting to press apply in the current sessioni think.

---

### Post by Ateo on 2007-05-21
hehe. yea. it fooled me for the longest time too.

glad it helped.

---

