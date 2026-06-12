---
title: "Firestarter"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2006-04-13
Hey all.  I installed firestarter.  I had used automatix.  When I uninstalled, I used synaptic.  I still get a password prompt at start up and it still says something along the lines (cannot run child something).

I had asked before, but didn't get a response that will remove the program completely.  I have tried:
1) Reinstalling
2) Uninstalling completely
3) Uninstalling 

Thanks!

---

### Post by dreamsINdigital on 2006-04-13
Follow this guide to uninstall stuff installed with Automatix:
[http://ubuntuforums.org/showthread.php?t=90797](http://ubuntuforums.org/showthread.php?t=90797)

29) firestarter:
Code:

sudo apt-get remove firestarter

Now go to system --> preferences --> sessions -->startup programs and remove
"gksudo firestarter"

---

### Post by brandoncolorado on 2006-04-13
[QUOTE=dreamsINdigital]Follow this guide to uninstall stuff installed with Automatix:
[http://ubuntuforums.org/showthread.php?t=90797](http://ubuntuforums.org/showthread.php?t=90797)

29) firestarter:
Code:

sudo apt-get remove firestarter

Now go to system --> preferences --> sessions -->startup programs and remove
"gksudo firestarter"[/QUOTE]

Thanks!

---

