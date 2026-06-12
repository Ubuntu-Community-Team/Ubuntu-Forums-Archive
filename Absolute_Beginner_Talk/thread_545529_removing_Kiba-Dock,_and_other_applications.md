---
title: "removing Kiba-Dock, and other applications"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by Scapegoat427 on 2007-09-07
How do I remove Kiba-dock, and Kiba-Dock settings, from my computer? In general, how do I remove applications that are not listed under add/remove?

---

### Post by Ub1476 on 2007-09-07
Just open the terminal and do this:

```
sudo apt-get remove kiba-dock
```

Or any other application.

For settings and such, go to your home folder, click ctrl+h (shows hidden files) and delete the kiba-dock folder.

If you installed through the commands:

```
./configure & make & make install
```, you'll need to locate the folder where you installed it, (that would say in what directory you wrote those commands) and write:```
 make uninstall
```

---

### Post by Scapegoat427 on 2007-09-07
Thanks a ton. Its been causing my computer to freeze when I had desktop effects turned on

---

