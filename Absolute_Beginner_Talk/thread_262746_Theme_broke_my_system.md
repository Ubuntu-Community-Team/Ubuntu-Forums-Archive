---
title: "Theme broke my system"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by Josey on 2006-09-22
I somehow managed to install a broken theme and need to know how to set my theme back to default in failsafe mode.
Thanks.

---

### Post by CatKiller on 2006-09-22
I've not come across this as a problem, but if the Theme Manager isn't working for you, you might try the Configuration Editor (**gconf-editor**) and navigate to apps/metacity/general and change the theme key to Human.

Actually, I've just tried that, and it only changed part of the theme. The other keys are desktop/gnome/interface/gtk_theme and desktop/gnome/interface/icon_theme

---

### Post by Perfect Storm on 2006-09-22
Changed the title to something more helpful.



What's the name of the theme?
Is it on Gnome or KDE?

---

### Post by Josey on 2006-09-22
It's the gnome desktop.
Now after I login to gnome nothing happens.
I've tried removing and reinstalling ubuntu and gnome desktop desktop with synaptic but no change.

---

### Post by Perfect Storm on 2006-09-22
cd /home/<username>/.themes
rm -rf <offending theme>


That should make gnome go back to default theme.

---

### Post by elpuerco on 2006-09-22
Piggy backing on this thread....

Where is the Theme Manager?  I have looked in my Kmenu and Adept but cannot find it.

I have looked in the desktop config and cant see where one changes the theme?

---

### Post by Brunellus on 2006-09-22
> **elpuerco said:**
> Piggy backing on this thread....

Where is the Theme Manager?  I have looked in my Kmenu and Adept but cannot find it.

I have looked in the desktop config and cant see where one changes the theme?
Please do not hijack/piggyback threads.

---

### Post by Josey on 2006-09-24
Worked like a charm.
Thanks alot. :)

---

