---
title: "little problem after installing compiz"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by drsyntax on 2007-06-28
after i installed compiz and it works fine, but when my laptop boot it take about 2 minutes to load as in pic

anyone can help??

---

### Post by drsyntax on 2007-06-28
any one can help ???

---

### Post by drsyntax on 2007-06-28
i posted my problem at compiz.org forums and got this :

> As far as I can say the problem is related to a conflict between metacity and compiz. I think metacity can't start because compiz is already running but the session-manager waits for metacity to be loaded (or waiting times out after about 2 minutes). 

You can either remove 'gnome-wm' from your startup-programs (System/Settings/Sessions) or use gconf-editor to set the key /desktop/gnome/applications/window_manager to the value '/usr/bin/compiz'. Removing gnome-wm may only cause more trouble so try the second method first 

but the second soln didn't work ( may be i did something wrong ), so i tried the first soln and it fixed my problem
my first question is : what is 'gnome-wm' and what trouble it may cause if i removed it from start up ??

second question : every time i was starting my system i had to run 'compiz --replace' and 'gtk-window-decorator --replace' to run compiz and show my window borders, i added these tow commands to start up to make them rrun automatically , is there another way to make compiz start with my system rather than adding it to start up :D ?

Thanks

---

### Post by drsyntax on 2007-06-28
bump :S

---

