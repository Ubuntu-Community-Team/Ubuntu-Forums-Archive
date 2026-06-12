---
title: "aptitude error"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by uk_sphinx on 2006-10-01
i

---

### Post by aysiu on 2006-10-01
Try this: ```
sudo nano -B /etc/apt/sources.list
``` Delete (Control-K) the 39th line. Then save (Control-X, Y, Enter)

---

### Post by uk_sphinx on 2006-10-01
cushty m8
got it sorted
know what i did wrong now

---

### Post by aysiu on 2006-10-01
It's not a common problem, but the error says there's a line that's incorrect in the /etc/apt/sources.list and even tells us what the line is.

You don't have to count the lines, just find the one that says *[http://thc.segfault.net/papers.php](http://thc.segfault.net/papers.php)* and delete it.

---

