---
title: "[SOLVED] Open in Terminal with Gusty?"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by neurostu on 2008-04-11
I have  a RHEL box that in Nautilus I can right click on a folder and select "Open Terminal" and a terminal is opened with inside the clicked directory.

Does anybody know how to do this in Gutsy?

---

### Post by bollix47 on 2008-04-11
In synaptic search for and install nautilus-open-terminal.

---

### Post by neurostu on 2008-04-11
Ok so I had installed that package but it didn't show up. I thought I did something wrong so I made this post.

I figured I had to restart nautilus so a log out then log in fixed the problem.

---

### Post by erginemr on 2008-04-11
While you are on it, you may also consider installing **nautilus-search-tool** and **nautilus-gksu** with:
```
sudo aptitude install nautilus-search-tool nautilus-gksu
```
which will add "file search inside the folder" and "open the folder as admin" items respectively to the right-click menu of Nautilus, which IMHO are two more very useful shortcuts.

---

