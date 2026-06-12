---
title: "view hardware info"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by lynxus on 2007-11-05
Hi guys,
Quick question hopefully.

How do i view what hardware i have from the terminal..

Outputting something like CPU speed,make, ram, hdd size / free . etc.



Thanks
Graham

---

### Post by steve.horsley on 2007-11-05
**sudo lshw**
does it for me. It generates lots of onfo, so I like ot pipe it either to a file, like this:
**sudo lshw > hardware.txt**
or to less which allows me to scroll through it ("q" to quit):
**sudo lshw | less**

But whatever you do, do a simple 
**sudo ls**
first to get rid of the pesky password prompt.

---

