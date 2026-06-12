---
title: "[SOLVED] How do you make a wine program load at startup?"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by rouge568 on 2007-06-20
I want to run an installed program (ypops) at startup. Unfortunately, it's a windows carry-over, and I have no idea how to start a program that uses wine automatically. Any help?

---

### Post by Sushubh on 2007-06-20
check out: [http://fetchyahoo.twizzler.org/](http://fetchyahoo.twizzler.org/)

---

### Post by rouge568 on 2007-06-20
Nah, I'll to stick with ypops.
But it still doesn't answer the original question - how would you load a wine program at startup?

---

### Post by Sushubh on 2007-06-20
just a guess... cant you make a shortcut with command:

wine path/applicationame

and add it to boot?

---

### Post by rouge568 on 2007-06-20
This may sound stupid, but where exactly is C:\\, aka the program files for wine apps? I can't find any in /usr/share

---

### Post by TheRingmaster on 2007-06-20
> **rouge568 said:**
> This may sound stupid, but where exactly is C:\\, aka the program files for wine apps? I can't find any in /usr/share
that directory is under ~/.wine

---

### Post by rouge568 on 2007-06-20
Thanks - I think I found the easiest solution:
Under the launcher menu, go to the program, right click, and "add this launcher to the Desktop."
Then, on the desktop, go to the properties of the launcher, the launcher category, and there is your command to put in the autoload.

---

