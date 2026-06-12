---
title: "How to stop ubuntu from dimming the monitor"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by prolapsedisk on 2007-07-17
After a certain period of inactivity, ubuntu shuts down the monitor. Is there anyway to disable this behaviour? I'm using fluxbox, but it's probably not a fluxbox specific problem.

---

### Post by 505 on 2007-07-17
Go to the menu System, Preferences, Power management and slide the  slider for display to never.

---

### Post by AnRa on 2007-07-17
You can modify this behaviour using **gnome-screensaver-preferences** ;)

---

### Post by dreadlord_chris on 2007-07-17
> **prolapsedisk said:**
> After a certain period of inactivity, ubuntu shuts down the monitor. Is there anyway to disable this behaviour? I'm using fluxbox, but it's probably not a fluxbox specific problem.

Ya, if you're like me and a number of others - changing the Power Managment or Screen Saver settings will have no effect on this.

[http://ubuntuforums.org/showthread.php?t=478892](http://ubuntuforums.org/showthread.php?t=478892) shows the changes I had to make to my **xorg.conf** to make my monitor stay on permanently.

---

### Post by prolapsedisk on 2007-07-18
Thank you! I'll try those out. I was trying out about the same thing but assumed it was in the console settings in /etc/console-tools BLANK_TIME, and that didn't quite work.

---

### Post by Golyadkin on 2007-07-18
My monitor sometimes gives me trouble. When it goes standby, moving the mouse or hitting the keyboard doesn't bring it back. That is why I simply disabled power management.

---

