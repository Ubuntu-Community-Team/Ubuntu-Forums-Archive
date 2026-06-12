---
title: "Monitor driver"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by Roost 12 on 2007-04-13
I have read quite a few threads/tutorials on setting up graphics in Linux and all seem to be more or less the same when it comes to monitors - none of them go past manually editing resolutions and refresh rates. Is reconfiguring xserver (sudo dpkg-reconfigure xserver-xorg) really the only option? Surely it must be possible to install monitor drivers. Drivers for quality monitors usually contain colour management files (.icm files in Windows). That "Generic Monitor" title strikes me as wrong. It remembers me of question mark in Windows (unknown device, i.e. no driver installed).

So to sum up my question: how can I throughoutly set up my monitor? :)

---

### Post by D10 on 2007-04-13
You just edit your xorg.conf file to the output ranges of your monitor. Way back when I use to edit my xorg.conf for  monitor settings quite a bit , but myself I haven't had to edit for a monitor in a long time. 

Maybe time I upgrade my monitors :) .


D10

---

