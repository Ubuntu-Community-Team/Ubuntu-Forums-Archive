---
title: "Terminal startup of Firefox uses userchrome, kmenu startup does not"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by ahurd on 2008-03-27
In just installed Gutsy I have copied userchrome from backup to the new FF profile. It has two purposes 1) icons only (no text) in Bookmarks Toolbar (BT), 2) multi-row display in BT. When I start FF by kmenu, neither happens. When I start via terminal, both work perfectly, as they did in previous install (Feisty). Anyone have any idea what is happening? Apparently it is unsafe (and inconvenient) to start FF via terminal Thanks.

---

### Post by chucky chuckaluck on 2008-03-27
i don't know why you are having that problem, but you could try writing a new menu entry for firefox (right-click on kmenu icon and "edit menu"). when you write the new entry, make sure you use the same exact command you use to start firefox from the terminal.

---

### Post by ahurd on 2008-03-27
Thank you for reply. Did that but it did not help. Strange problem, possibly a bug?

---

### Post by chucky chuckaluck on 2008-03-27
> **ahurd said:**
> Thank you for reply. Did that but it did not help. Strange problem, possibly a bug?

did you check in .mozilla to see if you had more than one profile? that's the only thing i can think of (with my fairly limited abilities).

---

### Post by ahurd on 2008-03-27
Solved. Permissions problem.

---

