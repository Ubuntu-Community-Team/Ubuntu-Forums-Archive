---
title: "Minimize wine window in Gnome"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by billstei on 2006-11-27
I have a window running a program with wine and then I click the minimize button and it flies off the screen.  Where did it go?  I know it's still running because I can see the process in System Monitor.  How do I get the window back up?

---

### Post by 56phil on 2006-11-27
The same thing happened to me last week. I chose to kill the process and start over. If there's another way to deal with I'd like to know too. ](*,)

---

### Post by CatKiller on 2006-11-28
I've always had Wine windows show up in the Window List, along with all the other open applications. Does Alt-Tab still work?

---

### Post by cronholio on 2006-11-28
I experienced the same. The window appeared again when I minimized all other windows (one-by-one, not using the show Desktop button).

---

### Post by billstei on 2006-11-28
Thanks for the ideas, but I don't see it in the Window List, and after minimizing all other (non-wine) windows it did not reappear.  It is interesting to note that the minimizng animation lines go off into the corner of the screen, versus the regular programs whose animation goes to the center of the panel where they have a normal task bar button appearance.

---

### Post by billstei on 2006-11-28
Oops, forgot to try the Alt-Tab idea, and YES! I can see the program in the Alt-Tab window and switch to it.  Good enough as a work around, but I take it wine windows are supposed to be in the normal task bar?  Bug or is my panel mis-configured?

---

### Post by bodhi.zazen on 2006-11-28
The way I do it is to run the "enable virtual desktop" option in winecfg.

Yes this gives an ugly gray window, but wine applications are easier to manage and do not get lost....

Like this:

[img]http://mmendes.jb0.org/img/winecfg.png[/img]

Only I increase the size of the desktop to 1280x1050

---

### Post by billstei on 2006-11-28
Thanks that works great.

---

### Post by bernardfrancois on 2007-01-13
Cool!

Here I did the same thing with winesetuptk.

---

