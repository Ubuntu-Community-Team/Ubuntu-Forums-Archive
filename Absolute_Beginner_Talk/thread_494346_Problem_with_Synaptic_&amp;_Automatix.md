---
title: "Problem with Synaptic &amp; Automatix"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-07-06
Ok, I have done several updates through synaptic and automatix and during the install process, i am prompted to "insert cd labeled.......¨ prompting me for my ubuntu cd.  Now ive been fortunate enough lately in that ive actually had an ubuntu cd handy, but i wont always have my cd wallet nearby.   Is there any way i can change this to where it doesnt prompt me for a cd?

---

### Post by confused57 on 2007-07-06
> **ITdrummer said:**
> Ok, I have done several updates through synaptic and automatix and during the install process, i am prompted to "insert cd labeled.......¨ prompting me for my ubuntu cd.  Now ive been fortunate enough lately in that ive actually had an ubuntu cd handy, but i wont always have my cd wallet nearby.   Is there any way i can change this to where it doesnt prompt me for a cd?
Open a terminal(Applications---Accessories---Terminal) to edit your sources.list:
```
cd /etc/apt
sudo cp sources.list sources.list_backup
gksudo gedit sources.list
```

Place a # in front of the CD source  listed near the top of the file...quit & save.

---

