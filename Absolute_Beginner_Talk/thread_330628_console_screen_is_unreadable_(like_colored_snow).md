---
title: "console screen is unreadable (like colored snow)"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by fsando on 2007-01-03
Hi
System:
notebook asus w1j, ati x1600, screen 1680x1050
Situation:
some days ago my problem with gui screen resolution was solved here:
[http://www.ubuntuforums.org/showthread.php?t=325732](http://www.ubuntuforums.org/showthread.php?t=325732)
After that when I enter a console with Alt+Ctrl+F2 (or any other F1-F6 key) the screen is unreadable, it looks like colored snow or something like that.
I guess I should change som settings in xorg.conf?

---

### Post by ajgreeny on 2007-01-03
xorg.conf has no effect on your terminal screens as x is not running them so the answer must be something else.  Have you changed anything else at all that could impact on your terminal?

---

### Post by MkfIbK7a on 2007-01-03
could you post a screenshot that may help...

---

### Post by fsando on 2007-01-03
> **ajgreeny said:**
> xorg.conf has no effect on your terminal screens as x is not running them so the answer must be something else.  Have you changed anything else at all that could impact on your terminal?
As far as I know I installed the ati driver (fglrx) that everybody recommended and made some changes to xorg.conf. As it is a notebook I didn't change any hardware.
Something must be responsible for driving the screen though?
> **wert613 said:**
> could you post a screenshot that may help...
I tried with PrtSc - how do I make a screen dump?
Edit: I tried PrtSc in the unreadable console but it didn't work

---

### Post by MkfIbK7a on 2007-01-03
not sure...

---

### Post by fsando on 2007-01-03
SOLVED
Here it is suggested to remove 'quet splash' from the boot menu which solves the problem - strange.

[http://www.ubuntuforums.org/showthread.php?t=328751]("http://www.ubuntuforums.org/showthread.php?t=328751")

---

