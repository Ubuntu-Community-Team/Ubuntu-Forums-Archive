---
title: "When using wine, cd drive won't open"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Dev'olution on 2008-02-05
Hi,

Whenever I access a setup on a cd, that involves following cd's after it, Wine seems to lock the CD-Rom and I am unable to eject my cd to transfer over to the next one

An example is Sims 2, which uses 4 cd's.

Can anyone help?

Kristian

---

### Post by jordanmthomas on 2008-02-05
What happens if you run
```
eject
``` from a terminal?

---

### Post by Dev'olution on 2008-02-05
It won't let me, says an application is holding it.

---

### Post by Dev'olution on 2008-02-05
Sorry guys, don't mean to bump, but i need to install an important business app with 6 cd's :(

---

### Post by Trail on 2008-02-05
```
wine eject
```

---

### Post by malibusurfer2 on 2008-03-10
Thank you for the tip! I created a desktop icon to run it. Right click on desktop, choose Create launcher, Type: Application in terminal, Name: give it a name, Command: wine eject.

I am running Quicken with Wine in Gutsy.

---

