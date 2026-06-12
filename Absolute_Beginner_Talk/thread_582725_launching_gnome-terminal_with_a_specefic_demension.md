---
title: "launching gnome-terminal with a specefic demension"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by nbv4 on 2007-10-20
I want to create a launcher that opens gnome-terminal with irssi running inside. I also want the gnome-terminal window to be a bit larger than the default size it launches at. How do I achieve this? I imagine it's a option I add to the launcher, but the gnome-terminal manpage doesn't have any such options listed...

---

### Post by dholbert on 2007-10-20
Use the flag
      --geometry=[width]x[height]
e.g.
   gnome-terminal --geometry=50x20

---

