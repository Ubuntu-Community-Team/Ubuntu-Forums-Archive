---
title: "Screensave on then logout"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by lucky_chouhan on 2007-01-09
Hi recently i am face new problem when my ubuntu screen saver is start then i press keboard or move my mouse button then login windows show then i type username and password and all session start (it feel like a restart).

Even I use automatically login.
why

---

### Post by ajmorris on 2007-01-09
it is because it "locks" the computer when the screensaver starts. To fix this go to system > Preferences > Scressnsaver and unitck the "lock screen when screensaver is actvie" box.

---

### Post by lucky_chouhan on 2007-01-09
time for testing.

thanks for your help

---

### Post by pawpaw on 2007-01-14
> **ajmorris said:**
>  To fix this go to system > Preferences > Scressnsaver and unitck the "lock screen when screensaver is actvie" box.
is there any other way to fix this ? ... when I try that ^, I get a terminal-like screen, then gettting sent back to login.

---

### Post by pawpaw on 2007-01-15
hmm I also get a "log-out" if I run nvidia x server settings/opengl tab, could the problem be video setting related ?

---

### Post by pawpaw on 2007-01-17
rightie-o, I got this thing sorted out by installing  the newest version of [envy]("http://albertomilone.com/nvidia_scripts1.html")

---

