---
title: "running iwconfig mode at startup"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by Bezvardis on 2006-08-24
Could anybody please tell me how I can run the command```
sudo iwconfig ra0 mode Ad-Hoc
```
at startup? I use this to share internet wirelessly via Ad-Hoc network, but it would not execute automatically if I put it in the startup list, because it requires password.

Many thanks in advance

---

### Post by Bezvardis on 2006-08-25
Well I see nobody has replied... Maybe it is some kind of a too simple a question that is answered already too many times, but I cannot find where - searched for hours in both these forums and in Google with no results...

---

### Post by P_Squiddy on 2006-11-30
Haven't played with Ubunut's rc.local yet, but putting your command without the "sudo" part in that file should do the trick.  Basically, rc.local is where you put "administrative startup tasks" that don't fit elsewhere.

---

