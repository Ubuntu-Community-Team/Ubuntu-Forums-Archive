---
title: "[SOLVED] Feisty sources.list"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by satterle on 2008-03-10
I'm running Feisty. I noticed in sources.list that all the references are to Gutsy. Is this correct or is my sources file outdated? Should I replace all "gutsy" with "feisty"?

---

### Post by taurus on 2008-03-10
How did you get it to change to Gutsy?  Did you change them by hand or did you try to upgrade from Feisty to Gutsy at one time?

If you are running Feisty, you should use Fiesty repos in /etc/apt/sources.list.

---

### Post by satterle on 2008-03-10
Nevermind. I'm got confused about which name goes with which number. I'm on 7.10 which I thought was Feisty but appears to be Gutsy. Damn, it's enough to learn this cool new system without having to keep these names straight!!!!   :-D

---

### Post by forrestcupp on 2008-03-10
I suspect you may have unknowingly upgraded to Gutsy.  In a terminal, type:
```
lsb_release -a
```
That will tell you for sure which version you are actually using.

Edit:
Too late.  That command is a good one to know, though.

---

### Post by wolfen69 on 2008-03-10
.

---

