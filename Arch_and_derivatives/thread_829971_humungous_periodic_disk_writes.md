---
title: "humungous periodic disk writes"
date: 2008-06-15
forum: Arch and derivatives
---

### Post by insane_alien on 2008-06-15
okay, i've been noticing this lately, periodicly(every two hours or so) my disk starts thrashing and gnome-system-monitor shows it as a disk write. 

i have no idea what is causing this.

can anyone tell me how to find out?

(sorry for missing letters and such but my keyboard is startingto fail on me and my usb keyboard is being used elsewhere.

---

### Post by Barrucadu on 2008-06-15
Do you have any cron jobs or other timed processes running?

Also, doesn't gnome-system-monitor have a way to show what is using the disk?

---

### Post by handy on 2008-06-16
Yes, the system monitor will show you what the cpu usage is of all programs/services on your machine, that should give a really good clue as to what is behind the activity.

---

