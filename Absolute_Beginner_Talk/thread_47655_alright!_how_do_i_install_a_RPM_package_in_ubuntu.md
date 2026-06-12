---
title: "alright! how do i install a RPM package in ubuntu?"
date: 2005-07-09
forum: Absolute Beginner Talk
---

### Post by ligerdave on 2005-07-09
how?

---

### Post by adwait on 2005-07-09
first,
sudo alien <filename>

then, a .deb file will be created, after tht, install using

sudo dpkg -i <filename>

---

### Post by ecadre on 2005-07-09
Is this a good idea?

---

### Post by tonym on 2005-07-09
Its worth a try,  I've done it on Debian systems without problems.  If it doesn't work you can just remove with dpkg.  If there isn't a .deb this can be better than getting the source and compiling  -  you can keep track of what you have installed via apt/aptitude/synaptic.

---

### Post by SGC on 2005-07-09
[QUOTE=ecadre]Is this a good idea?[/QUOTE]
 When it works, it is a good idea, but 90% of times the converted packages will not work.

---

### Post by ecadre on 2005-07-09
[QUOTE=SGC]When it works, it is a good idea, but 90% of times the converted packages will not work.[/QUOTE]


Yes, that's what I was wondering.  At a guess I would have though it would be liable to throw up all sorts of problems with the placement of files and dependencies etc.

---

