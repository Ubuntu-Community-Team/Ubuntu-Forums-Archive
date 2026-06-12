---
title: "[SOLVED] task manager in ubuntu?"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by sayuki288 on 2007-10-21
is there a task manager-like application in ubuntu?

where you can close program and stuff?

---

### Post by overlord.gaurav on 2007-10-21
Go to System>>Administration>>System Monitor.

---

### Post by Qwerty_ on 2007-10-21
Something like

System>Administration>System Monitor?

---

### Post by sayuki288 on 2007-10-21
can i open system monitor using run application?

---

### Post by sayuki288 on 2007-10-21
lolx its like windows :lolflag:

---

### Post by Qwerty_ on 2007-10-21
Yeah the system monitor I guess is like an equivalent to one in windows.

Also if you want to just kill an application you can open a terminal and type

```
xkill
```

You will then have a cross as a cursor and anything you click will be killed.

---

### Post by Shazaam on 2007-10-21
Another way to see (and manage once you know your way around the cli) what's running is to open a console (terminal) and type this in...
```
top
```

---

### Post by nchase on 2007-10-21
> **Shazaam said:**
> Another way to see (and manage once you know your way around the cli) what's running is to open a console (terminal) and type this in...
```
top
```

top works, i guess, but it has always been difficult for me to navigate. a "better" (more intuitive, easier to use) commandline program, in my opinion, is htop.

```
sudo apt-get install htop
```

then just run it by typing htop in a terminal or using the menu item that is created under "System Tools"

---

