---
title: "Solving &quot;panel already running&quot; error, &quot;no panels&quot; problem"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by SuperKingKongMegaNewbie on 2007-01-02
I just ran into the "no Gnome panels" problem myself. (Yes, Gnome. I don't know about KDE etc.) This is what I did (and what all the newbies might want to do) to fix it.

I pressed Alt+F2, entered **gnome-system-monitor** and then clicked the Run button.
[COLOR="Gray"]Alternatively, if the Alt+F2 does nothing (heard that it happens), you can Right-click on the desktop and create a launcher that executes the **gnome-system-monitor** command, and then launch it from your desktop.[/COLOR]

When the System Monitor window appeared, I went to the *Processes* tab and located the **gnome-panel** process (it's status was Zombie :evil: ), then I right-clicked on it and chose to kill it (that's just the thing that should be done with zombies).

The panel appeared! \\:D/ 
[COLOR="Gray"]If by some unnatural and completely abnormal reason it doesn't appear, you can try the first step using **gnome-panel** instead of **gnome-system-monitor**.[/COLOR]
[B]
Please comment[/B] if this thread was helpful or not.
If it's good, it stays.
If it's bad, it goes. (In this case, you might want to try to search the forum for an advice with a bit more brain behind it. Perhaps, try "panel already running"!)

---

### Post by spockrock on 2007-01-02
you could also open terminal and do, "killall gnome-panel"

---

### Post by SuperKingKongMegaNewbie on 2007-01-02
Sure thing, the terminal comes in quite handy every once in a while, just keeping it nice and graphical.
Plus, the System Monitor is a good thing to learn too.
I like to leave the terminal alone as long as the graphical tools are on par.

---

