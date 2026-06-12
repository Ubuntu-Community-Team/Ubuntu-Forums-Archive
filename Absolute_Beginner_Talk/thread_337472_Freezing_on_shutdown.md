---
title: "Freezing on shutdown"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by john.n on 2007-01-13
Hi, any help, just installed ubuntu 6.10, its freezing every time i try to shut it down. Its on a Compaq presario, amd turion64. any usual causes...?

---

### Post by tonyr1988 on 2007-01-13
Don't know if it'll give you anything helpful, but you could try:

> sudo shutdown -h now

and see if it spits out anything useful. Do you have any applications up while shutting down? Use:

> gnome-system-monitor

to see all your processes running. See if anything's hiding in the background that didn't close properly.

---

