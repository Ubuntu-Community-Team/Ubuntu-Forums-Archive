---
title: "[SOLVED] gdm pannels"
date: 2008-07-05
forum: Apple Hardware Users
---

### Post by jrdjrd on 2008-07-05
Hi, I have a 1.25GH emac G4 dual booting ubuntu and osx. One time when I booted ubuntu the whole bottom panel was blank. the top panel was bland except for my app launchers and the power button.

Why is this happening?

---

### Post by pytheas22 on 2008-07-05
Sometimes the Gnome panels get flaky.  Next time it happens, try:
```

kill $(ps -e | grep gnome-panel)
gnome-panel
```

It might help.

---

### Post by jrdjrd on 2008-07-07
sorry, didn't work

---

### Post by pytheas22 on 2008-07-07
Sorry it didn't help.  The next best thing to try is:
```

mv ~/.gnome ~/.gnome-OLD
mv ~/.gnome2 ~/.gnome2-OLD
```

This will wipe out your current Gnome configuration and replace it with a fresh one using default settings.  If you don't mind having to start over again, this command will hopefully get rid of whatever was causing the gnome-panel problem.

---

### Post by jrdjrd on 2008-07-10
I got it, i just added the menu items using the add to panel thing

---

