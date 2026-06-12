---
title: "hard drive &quot;clink clunk&quot; noise?"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by juanzo007 on 2008-01-10
Hey folks...

5 year old computer with it's fist linux system on it, i can feel the hard drive knocking.  Time for a new HD soon, I take it?

---

### Post by eolson on 2008-01-10
That's my guess .... make sure you've got everything backed up that needs backing up.

There is a utility for testing your hardrive,  but the name slips my memory at the moment. Ill check google.

---

### Post by Xavieran on 2008-01-10
Could be...you could use clonezilla to clone the install and then install it on the new hard drive...

[http://clonezilla.sourceforge.net/]("http://clonezilla.sourceforge.net/")

---

### Post by eolson on 2008-01-10
O.K. found it

from the terminal
  sudo apt-get install smartmontools

and I think the particular utility in there that you want is smartctl

Useful link (as in directions) 

[http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

---

