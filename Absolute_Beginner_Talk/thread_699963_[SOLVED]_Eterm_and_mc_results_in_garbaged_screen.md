---
title: "[SOLVED] Eterm and mc results in garbaged screen"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by siddartha on 2008-02-17
Although gnome-terminal shows mc the right way, with Eterm the screen is filled with garbage. What is the source of this problem?

---

### Post by mattismyname on 2008-02-18
Can you post a screenshot?

---

### Post by siddartha on 2008-02-19
The answer is that Ubuntu is Unicode ready and Eterm is not. So the graphical characters were shown wrong because they were encoded differently.

---

