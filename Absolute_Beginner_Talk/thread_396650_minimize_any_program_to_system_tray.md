---
title: "minimize any program to system tray"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by lunaz on 2007-03-29
i run a bnet chat bot, javaop, and want to minimize it to sytem tray instead of the bottom panel. how do i do it?

---

### Post by solar george on 2007-03-29
Try using alltray.

You can either add a new repo to synaptic to get it or you can install the autopackage. 


I would use the autopackage


[http://alltray.sourceforge.net/]("http://alltray.sourceforge.net/")

---

### Post by lunaz on 2007-03-30
well that auto thingy didnt work so i added that guy's repo to the sources list. i did aptitude update & install alltray, but now i dono how to use it. he dont have any instructions..

---

### Post by martinw89 on 2007-03-30
For me AllTray was in Add/Remove, but it sounds like you got it.  To use it, just start the program and click on the window you would like to minimize.  Or, type "alltray" before a program's name to start it minimized to the tray.

---

### Post by lunaz on 2007-03-31
this is what i added to the startup programs thingy, and it doesnt work, that i know of. i dont see any lil icons anywhere. if i go to my /home/javaop/Core folder in file manager i can dbl click that JavaOp2.jar file & it does its thing fine but i want it to start up minimized to the system tray like gaim.

```
alltray /home/gail/javaop/Core/JavaOp2.jar
```

---

