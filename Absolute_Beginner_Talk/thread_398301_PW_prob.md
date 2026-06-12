---
title: "PW prob"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Shmook on 2007-03-31
When I try to load certain programs: QTParted, Wireless Assistant -- the program pops up with a window saying something to the effect that I may not have access to all options since I'm not logged in as root. 

Since other programs prompt for a password at this phase, I don't really understand what's going on and how to access these programs...

Any ideas?

---

### Post by Jorge32 on 2007-03-31
try with 
```
gksudo
``` typed before the command of the program you wish to open in a terminal. it should give you "administrator properties", it makes you enter as root

---

### Post by Shmook on 2007-03-31
hmm...how do I ask the terminal to run this program that I otherwise only know how to load through the GUI menu?

---

### Post by Maestro23 on 2007-03-31
> **Shmook said:**
> hmm...how do I ask the terminal to run this program that I otherwise only know how to load through the GUI menu?

Ex: For qtparted

> gksudo qtparted

---

