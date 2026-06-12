---
title: "keyboard (enter) problems"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by ineedhelpnow on 2007-11-19
i have a hewlett packard keyboard and the enter key does not work yet the num pad enter key works. any ideas on how to fix it?

---

### Post by PointyWombat on 2007-11-20
Is you keyboard selected as the proper one under system -> preferences -> keyboard? There are several HP models there which may work for you.

If not, you can run 'xev' in a terminal and note the keysym details of the return key that works, and the return key that doesn't. Then you can map the non-working one using the xmodmap command. Read the man page for xmodmap for examples.

---

