---
title: "Amarok - Don't add .wma files to collection"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by DanManIt on 2007-11-04
Right now, my amarok is automatically adding all of my wma files to my music collection. I don't want it to do this. What can I do to get it to not add them?

---

### Post by SunnyRabbiera on 2007-11-04
it scans to whatever directory you want it to, if you had wma files in your music directory and that was where you directed amarok to then theres your problem.
you could just move the wma files to another folder.

---

### Post by DezSP on 2007-11-04
Or you could...

chown -R root *.wma
chmod -R 700 *.wma

To make them unreadble unless you're the super user. Amarok should then ignore them.

---

