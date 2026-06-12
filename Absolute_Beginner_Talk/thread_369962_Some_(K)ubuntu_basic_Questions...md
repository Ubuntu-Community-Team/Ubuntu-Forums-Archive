---
title: "Some (K)ubuntu basic Questions.."
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by WardLoockx on 2007-02-25
I still have some things that I can't find out to set it properly if somebody can help?

1. When I do apt-get install, the freshly installed program never appears in my menu (I always habe to edit the menu,save it so he reloads my system configuration). Is it possible to do this command line?

2. Is it possible to start all windows maximized?

3. When I have few programs open and I go to my desktop and open another program he pops up all the other programs with my new program on top of it. Is it possible to NOT raise the programs already open?

---

### Post by nereid on 2007-02-25
Ad 1
Only programs with a menu entry will add an entry to the menu. Most programs don't have an entry.

Ad 2
Sure, just maximize your specific window and then click on the window icon. Go to the window behavior and save the size (I'm sure you can also change the behavior in the systems settings that every window will start maximized).

Ad 3
I'm not sure if I do understand you correctly, but you have some applications running minimized and after you start a new program all apps will be restored with the newest on top?

---

### Post by WardLoockx on 2007-02-25
> **nereid said:**
> Ad 1
Only programs with a menu entry will add an entry to the menu. Most programs don't have an entry.

Ad 2
Sure, just maximize your specific window and then click on the window icon. Go to the window behavior and save the size (I'm sure you can also change the behavior in the systems settings that every window will start maximized).

Ad 3
I'm not sure if I do understand you correctly, but you have some applications running minimized and after you start a new program all apps will be restored with the newest on top?

Ad1: But if there is a menu list entry how can I refresh the menu ?
Ad2: Can't find window size settings :S
AD3: Yes that is what I mean :)

---

### Post by nereid on 2007-02-25
Normally a new menu item should appear after the program has been installed, at last after you've logged out of KDE and login again.

2.
Right click on the icon. Go into the first submenu (Advanced or something like that) and choose behaviour of this window (more or less ;) ).

I haven't got a clue for the reactivation problem. In the worst case you could rename your .kde folder in your home directory and relogin into KDE. A new .kde folder will be created with the default configuration if the problem still persists then I don't know, sorry ;)

---

### Post by WardLoockx on 2007-02-25
> **nereid said:**
> Normally a new menu item should appear after the program has been installed, at last after you've logged out of KDE and login again.

2.
Right click on the icon. Go into the first submenu (Advanced or something like that) and choose behaviour of this window (more or less ;) ).

I haven't got a clue for the reactivation problem. In the worst case you could rename your .kde folder in your home directory and relogin into KDE. A new .kde folder will be created with the default configuration if the problem still persists then I don't know, sorry ;)

Problem 2 is solved! Thanks

3. It's not a fault of KDE it has been always like this.

---

### Post by BarfBag on 2007-02-25
To refresh your GNOME desktop (without logging off), type:

> killall gnome-panel

I don't know how to do it in KDE, but it's a start.

---

