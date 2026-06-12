---
title: "Update notifier"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by esteban2x on 2006-04-12
On my ver of Ubuntu, I'm running "update notifier". Already, it did an update and ins talled what it had to like 132 files. Ok, still, I don't know how to check my version here.  I tried control, alt, f1 but that just takes me to a black screen. I'd like to know if the updater changes me from my original 5.04 to a newer version.

---

### Post by krusbjorn on 2006-04-12
If you are on 5.04, you need to change every "hoary" to "breezy" in your /etc/apt/sources.list file, if you want to upgrade to the current version. 

You have to open it as root, so run "sudo gedit /etc/apt/sources.list" from a terminal (or if you are using KDE, replace "gedit" with "kate").

---

