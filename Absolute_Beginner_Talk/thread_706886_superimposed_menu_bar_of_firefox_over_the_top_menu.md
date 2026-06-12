---
title: "superimposed menu bar of firefox over the top menu bar, like Applications Places Syst"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by blacksheep.baba on 2008-02-24
Hi...

I am having a problem with the top panel bar.
My 'Application Places System' menu is superimposed by the Firefox menu.
The Firefox menu just got fixed there with no functionality.

How can i get rid of the Firefox menu items from over the regular top panel menu items?

I am using ubuntu 7.10, upgraded it over the net.
If I need to put more info about my system, it would be I am running it from an acer TravelMate 4010 with 768RAM

Regards...


baba

---

### Post by bazzawill on 2008-02-24
You should be able to right click on it and click delete or move (you may need to uncheck lock to panel first)

---

### Post by blacksheep.baba on 2008-02-24
Hi Buzzawill...

Thanks for the reply, I unchecked the 'Lock ot Panel' 
Moved it to right and left, but the Firefox menu remains.

One other thing when I put the mouse over the Application item, the mouse over works and the Firefox menu hides under it.

Regards...


baba

---

### Post by bazzawill on 2008-02-24
Hmm not sure exactly what is going on have you tried loging out and logging back in and or restarting gdm or the machine. If that does not work you can reset gnome to it's default state with the following command from a terinal ```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

---

### Post by blacksheep.baba on 2008-02-24
bazzawill hi...

It worked, I ran the code from su and rebooted.
The top panel bar is clean now.

Thanks, it was a very pleasant experience.

:)

Regards...


baba

---

