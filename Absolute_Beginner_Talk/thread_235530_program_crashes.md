---
title: "program crashes"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by mlie on 2006-08-13
How do I use a program again after it crashes? I already have KTorrent and Amarok crashes.. But I can't use them anymore... :confused:

---

### Post by neilp85 on 2006-08-13
To check to see if there are still processes running from those apps try these commands:

ps -A | grep amarok
ps -A | grep ktorrent

If there are you want to kill those processes

killall -9 amarok
killall -9 ktorrent

Now you should be able to restart either of those apps.

---

