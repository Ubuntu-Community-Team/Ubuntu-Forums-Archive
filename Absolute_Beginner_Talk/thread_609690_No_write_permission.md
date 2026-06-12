---
title: "No write permission"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-11-11
I am trying to install quake 4 on my computer, but when I get to the point where I need to enter my install path, it says
No write permission to /usr/local/games/quake4
anyone know what to do

---

### Post by Dapman01 on 2007-11-11
:(

---

### Post by carlosjuero on 2007-11-11
are you trying to install as your normal user? To install in that location you need to install as root (run the installer as sudo).

I installed Quake 4 into my home folder to avoid that.

---

### Post by taurus on 2007-11-11
Whatever command you use to install quake 4 from a terminal, include the **sudo** in front of it if you want to write to anything outside of your own $HOME.

```
**sudo** command
```

---

