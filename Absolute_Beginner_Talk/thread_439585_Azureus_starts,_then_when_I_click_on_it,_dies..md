---
title: "Azureus starts, then when I click on it, dies."
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by carbonrodney on 2007-05-10
Yep. Thats what it does. It comes up with a dialog box saying the new improvements for 2.5.0.4 and the 'Azureus did not close properly' box.

I think it has something to do with my dual boot system. Specifically that I soft linked ~/.azureus to /windows/path/Azureus/, it worked (loaded) once. And since I have restarted now it dies.

---

### Post by jackmc on 2007-05-10
I found that installing through "Add/Remove" didn't work, but doing it straight from the Azureus website was fine.

---

### Post by fenian on 2007-05-10
Open a terminal and run these commands...

> rm .azureus/.lock
rm .azureus/logs/*.log
rm .azureus/logs/save/*

Azureus should then be able to start.This problem seems to occur when Azereus crashes or doesn't shut down cleanly.

---

### Post by carbonrodney on 2007-05-11
> **fenian said:**
> Open a terminal and run these commands...



Azureus should then be able to start.This problem seems to occur when Azereus crashes or doesn't shut down cleanly.

Thanks, it does start. But now all my torrents are gone. Perhaps this is a good thing, if you can help me set it up so that it works both in windows and in ubuntu?

---

