---
title: "gksudo nautilus killed themes, froze windows [7.10]"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by IWood on 2007-11-02
Hrm. Not sure if this is a bug or not, so I thought I'd check.

command gksudo nautilus launched Nautilus...not only did Nautilus not have a theme, all other open windows were also stripped of themes and borders.

In addition--and this is more bothersome--the windows became immovable. I could resize them, but not reposition them.

So...what's up with that?

---

### Post by Hospadar on 2007-11-02
that's very curious, are you using compiz? how about emerald?

---

### Post by MrFSL on 2007-11-02
```
gksudo nautilus --no-desktop
```

From nautilus --help
> Do not manage the desktop (ignore the preference set in the preferences dialog).

---

### Post by the yawner on 2007-11-02
If you're using a theme that is saved on your home folder only then running nautilus as root (via sudo) will use the default theme.

---

