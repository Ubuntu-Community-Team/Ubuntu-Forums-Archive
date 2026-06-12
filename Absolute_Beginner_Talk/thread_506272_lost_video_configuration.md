---
title: "lost video configuration"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by gguzman on 2007-07-21
After disable nvidia unsupported driver my desktop is totally in blak, I can't do nothing.
Help please...

---

### Post by Majorix on 2007-07-21
Sounds like your xorg.conf file is changed.

There usually is a backup in the /etc/X11/ directory for xorg.conf. Check for it and if found, replace that with the edited xorg.conf file.

---

