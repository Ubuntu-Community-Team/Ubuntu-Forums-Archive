---
title: "Difference in Version"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by rrkano on 2007-04-13
What's the difference between 6.06 and 6.10 Server Edition...is one better than another? Or do they both basically have the same components?

Thanks

---

### Post by 23meg on 2007-04-13
6.06 is a long term support release that has seen about two months of bug fixing work to make it more stable. It will be supported for much longer periods than a regular release (three years for desktops, five years for servers). 6.10 is a regular release, but the time that went into 6.06 was taken out of *its* (normally six month) development time, so it's regarded as a "less stable" releease, though in practice it may not be (actually, hasn't been for most use cases). 

Regarding components, a general answer would be yes, but specifics may vary; 6.10 naturally has newer versions of everything.

In case you're not aware, 7.04, the next version after 6.10, is due in less than a week.

---

### Post by rrkano on 2007-04-13
Thanks for the info, I really do appreciate it. I loaded 6.06 Server on a box...it looks like it's a command line interface (no gui). I thought I saw a version of ubuntu that had a gui front end, or is that the desktop version? 

Thanks

---

### Post by zvacet on 2007-04-13
Version with GUI is desktop version,but if you want GUI on you server 
```
sudo aptitude install ubuntu-desktop
```

If you like GNOME  and
```
sudo aptitude install kubuntu-desktop
```
 
If you prefer KDE

---

### Post by 23meg on 2007-04-13
It's a good idea to do a ```
sudo aptitude update
``` before each of those commands as well.

---

