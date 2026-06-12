---
title: "i've completely screwed up firefox"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by fuscia on 2005-11-08
don't even ask. how do i get rid of every last bit of it so that i can start fresh?

---

### Post by aysiu on 2005-11-08
My guess would be to open up Synaptic and mark it for "complete removal." Then, afterwards--just to be safe--do a file search for any file with the word *Firefox* in it and delete it.

Are you sure you don't just have a corrupt profile? What did you do to bork it?

---

### Post by Manny C on 2005-11-08
```
 mv ~/.mozilla ~/.mozilla.backup 
```

---

### Post by Kapre on 2005-11-08
[QUOTE=fuscia]don't even ask. how do i get rid of every last bit of it so that i can start fresh?[/QUOTE]

fuschia - go to Synaptic and uninstall it through there.

K

---

### Post by fuscia on 2005-11-08
additionally, the problem is that i have installed 1.5rc1. i uninstalled 1.0.7 through synaptic, but i still have 1.5rc1 on here. what i was originally trying to do was trying to get rid of these stupid little bookmark toolbar favicons that mar an otherwise lovely theme (blackjapan). someone on the mozilla forums suggested some code for my userChrome.css file. i realized i had to create the file and that's when the trouble started, involving permissions, not being in root when i thought i was, etc. and the worst thing: the code he suggested was for **adding** those stupid, little pieces of crap, not removing them. so then, i couldn't switch themes. i deleted my profile and reinstalled 1.5rc1 and ended up with the exact same mess i left off with.
so, i'm guessing i should just delete anything that says *firefox*? do i need to do 'sudo' first, or be in '#'?

---

### Post by Manny C on 2005-11-08
How did you install 1.5 rc1? The correct removal process depends on this.

---

### Post by fuscia on 2005-11-09
i ended up reinstalling breezy entirely. there were some other messes i'd made and i also wanted to strip it clean. problem solved...until next time. 

so, this time, i followed the direction in the wiki and it went better (i had forgotten that 'cd' takes me back home and didn't get one of the instructions the previous time).

the original problem (those dumbass favicons) has been solved.

thank, all.

---

