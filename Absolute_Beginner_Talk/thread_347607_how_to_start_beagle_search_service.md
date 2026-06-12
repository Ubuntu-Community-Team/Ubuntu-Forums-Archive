---
title: "how to start beagle search service"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-01-27
I installed beagle but everytime I search I have to click START SEARCH SERVICE which is annoying, I want it to automatically start the search service. Beagle is in my startup session, and I have it checked to automatically index. Any ideas?

---

### Post by aidanr on 2007-01-27
i think it's "beagled" that should be in your startup items

---

### Post by syalam on 2007-01-27
sorry i made a typo, 'beagled' is in my startup session. but i dont see it in my process list

---

### Post by aidanr on 2007-01-27
:-k 

[quote=http://beagle-project.org/Starting_Beagle_Daemon]Enabling/Disabling the Daemon

Beginning with Beagle 0.2.14, the Beagle daemon can be started automatically when you log in by using the beagle-settings tool. Simply click the "Start search & indexing services automatically" check box, and the next time you log in the Beagle daemon will start automatically. Uncheck it if you don't want the daemon to start on your next login.[/quote]

^make sure that's checked

if that doesn't work, type beagled in a terminal and see doe's it give any errors, and also post the output of 
```
ls -Al ~/.config/autostart
```

---

### Post by Biker on 2007-01-27
Beagle 2.14 is not in the default repository so you must start beagle for Gnome this way:

1. Menu System, Preferences, Sessions
2. Tab 'Startup Programs'
3. Add startup command 'beagled --bg'

I am running Beagle 2.15.1 under Edgy. There is an option now called 'Start search & indexing services automatically' but it is the same result as I describe above here.

---

### Post by syalam on 2007-01-28
it seems everytime I close the beagle search window it kills the beagled process, so the next time i want to search i have to re-enable the service...help?

---

