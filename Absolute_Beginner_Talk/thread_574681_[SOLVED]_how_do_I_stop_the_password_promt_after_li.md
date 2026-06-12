---
title: "[SOLVED] how do I stop the password promt after lidclose then open?"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by MacHaddock on 2007-10-13
Hello I know I have read somewhere around here how to do this before but I can't find it now (the search engine in the upper right corner ain't all that good.) so I have to ask for some help on it again.

I have the power management set to black my screen when I close the lid of my laptop. When I open it again I'm promted for password. How do I make it stop promting me for the password? That is my question.

Thanks

---

### Post by francisco_athens on 2007-10-14
In the screen saver settings app there should be a check box for locking the screen, uncheck that box..

---

### Post by strabes on 2007-10-14
Hit Alt+F2, type in gconf-editor. Run it. Browse to /apps/gnome-power-manager/lock. Uncheck "blank_screen." Then restart gnome-power-manager:```
killall gnome-power-manager
gnome-power-manager &
```

---

### Post by MacHaddock on 2007-10-14
I still wanted it to blank the screen when I close the lid so I did almost what you said.
I did this part
> Hit Alt+F2, type in gconf-editor. Run it. Browse to /apps/gnome-power-manager/lock.  but instead of unchecking "blank-screen" I found three settings that said lock_on_blank_screen, lock_on_suspend and lock_on_hibernation and I unchecked them I restarted the gnome-power-manager like you said:
```
killall gnome-power-manager
gnome-power-manager &
```

and that did the trick.
Thanks man I love this forum.

=D>

---

