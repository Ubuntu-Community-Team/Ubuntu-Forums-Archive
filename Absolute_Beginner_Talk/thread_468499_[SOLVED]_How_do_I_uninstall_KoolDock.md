---
title: "[SOLVED] How do I uninstall KoolDock"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-06-08
KoolDock's started crashing on me a little too much and I want to get rid of it now. But I also want to remove all the KDE crap that I installed with it. How do I know what packages to un-install ?

---

### Post by ronocdh on 2007-06-08
> **Inxsible said:**
> KoolDock's started crashing on me a little too much and I want to get rid of it now. But I also want to remove all the KDE crap that I installed with it. How do I know what packages to un-install ?
If you mean remove all of KDE and revert back to GNOME, then the commands you want are:
```
sudo aptitude remove kubuntu-desktop
sudo aptitude install ubuntu-desktop
```

---

### Post by Inxsible on 2007-06-08
I never installed the whole kubuntu-desktop. While installing kooldock, i did
```
sudo aptitude install kooldock
``` and it asked me to download a few more kde packages, since I use Gnome. I want to remove those too now.

---

### Post by wolfen69 on 2007-06-08
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)      excellent site for how to clean up your system.

---

