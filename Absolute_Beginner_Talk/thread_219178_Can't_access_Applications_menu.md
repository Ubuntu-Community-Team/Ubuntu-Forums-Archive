---
title: "Can't access Applications menu"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by eulipion2 on 2006-07-19
Hello,
I installed Xubuntu for the first time today, got it working, then decided to tinker around and see what was what.  So in the Applications menu, or at least that's what it says now, I went to settings->menu options or something like that, and now in my upper left corner I have an Applications menu, but nothing drops down when clicked, meaning I can't exit X, can't open a new terminal.  In fact, the only thing I can open is Firefox because it had a shortcut in the toolbar next to the menu.  What happened to my menu?  How do I fix it?

Thanks

---

### Post by OU812 on 2006-07-20
Right click the desktop. This should bring up the apps menu. Also try restarting the panel by hitting alt-f2 and at the run prompt enter

xfce4-panel

john

---

### Post by eulipion2 on 2006-07-21
Thanks!!!!!

---

### Post by K.Mandla on 2006-07-21
Just FYI, there was a nasty bug that ate the Applications menu when you tried to edit the menu configuration. There's a trick to get it back; you can find it [here]("https://launchpad.net/distros/ubuntu/+source/xfce4/+bug/47776"). It was fixed in updates, but if you haven't updated your machine lately, it might still be there.

Either way, just in case. ... :)

---

