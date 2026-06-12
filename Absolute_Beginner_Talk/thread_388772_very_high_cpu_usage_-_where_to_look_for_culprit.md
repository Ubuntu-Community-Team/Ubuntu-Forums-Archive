---
title: "very high cpu usage - where to look for culprit"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by larrybrazos on 2007-03-19
i felt my system lagging recently and have been noticing my cpu usage is very high . . .
i have looked in the system monitor and my cpu will be bouncing from 80-90 % usage, but the highest process usage is with gnome-system-monitor at 6-10%, basically i see no run away processes there . . .

i have been experimenting alot with my system, and i am not sure where i tripped, so i was wondering where i can begin my investigation beyond the gui system monitor to figure out what is making the system lag.

i would like to avoid reinstalling to fix the problem.

---

### Post by cstudent on 2007-03-19
Do you have system monitor set to show all processes? It's default is just to show the users processes.

What I do is view all processes and sort the display on CPU to bring the highest cpu users to the top.

---

### Post by lamalex on 2007-03-19
did you do ps -a? did it list anything out of order? what about top?

---

### Post by Kateikyoushi on 2007-03-19
Try "top" in terminal and see whether it shows the same as the system monitor.

---

### Post by larrybrazos on 2007-03-19
found it . . .
mount.ntfs-3g

---

### Post by larrybrazos on 2007-03-19
i am running an external western digital hard drive, and fooled around alot with different types of mounting solutions, so it is very possible i have some problem there.  guess i will start retracing my steps . . .

---

