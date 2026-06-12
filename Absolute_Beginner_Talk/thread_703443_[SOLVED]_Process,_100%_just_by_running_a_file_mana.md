---
title: "[SOLVED] Process, 100% just by running a file manager?"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-02-21
I remembered natulious( did i spell it right), did not run even though I am double-clicking this one folder, then something happened. I have 100% cpu use, running nothing!

---

### Post by Joeb454 on 2008-02-21
Open up a terminal (Applications>Accessories>Terminal) and type ```
killall nautilus
``` this should kill the nautilus process, which will then restart itself.

Does your problem remain after that?

---

### Post by karlo on 2008-02-21
> **Joeb454 said:**
> Open up a terminal (Applications>Accessories>Terminal) and type ```
killall nautilus
``` this should kill the nautilus process, which will then restart itself.

Does your problem remain after that?

well, i restarted the whole system. my theory is just the same as yours, you see I launched nautilus at first, it ran, but after the second and the third, nothing happened...

---

### Post by karlo on 2008-02-22
[b]If somebody sees this, report this to the Launchpad of Ubuntu, probably this is a BUG...

Temporary solution: RESTART.. probably because of a bug.[/b]

---

