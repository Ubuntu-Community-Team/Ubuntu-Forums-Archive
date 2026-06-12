---
title: "workarounds for firefox kernel panics?"
date: 2005-02-07
forum: Apple PPC Users
---

### Post by adamw on 2005-02-07
I seem to be getting a LOT of kernel panics when I use firefox, mozilla, and epiphany.  About three or so a day.  This is with a Powerbook 1.5ghz, 1GB RAM, running Warty 4.1.  Has anyone experienced this problem and know any workarounds?

---

### Post by jjramsey on 2005-02-10
[QUOTE=adamw]I seem to be getting a LOT of kernel panics when I use firefox, mozilla, and epiphany.  About three or so a day.  This is with a Powerbook 1.5ghz, 1GB RAM, running Warty 4.1.  Has anyone experienced this problem and know any workarounds?[/QUOTE]

Are you sure that it's the browsers per se that cause the kernel panics? Check out [this thread](http://www.ubuntuforums.org/showthread.php?t=12388) and see if anything looks familiar.

---

### Post by adamw on 2005-02-10
If you haven't noticed, I posted in the thread you linked to (I'm not having heat problems).  Well, I can't be 100% sure that the mozilla engine is causing the kernel panics.  If anything, though, it is causing the problem to surface most easily.  If I do get a kernel panic, it happens roughly 95% of the time when I am using mozilla.  It rarely happens when I am using the command-line, and I normally spend more time on the command-line then I do with mozilla.

---

### Post by jjramsey on 2005-02-10
[QUOTE=adamw]If I do get a kernel panic, it happens roughly 95% of the time when I am using mozilla.  It rarely happens when I am using the command-line, and I normally spend more time on the command-line then I do with mozilla.[/QUOTE]

The command line is usually less resource-intensive. Still, just to rule out that its the browser, I'd do something like attempt a kernel compile, just as a stress test.

---

### Post by adamw on 2005-02-14
I did do a kernel compile a week ago without any trouble, but the kernel compile took about 30 mins and the problem normally occurs roughly every 2-3 hours.  I have gotten a panic twice when running apt-get update, though.  Is there a crashlog somewhere on my system I could look at when this happens to track it down?

---

