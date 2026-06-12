---
title: "What my system specs?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by moebob24 on 2008-01-13
How can I view my system specs? Is there a system menu that I can view?

---

### Post by steeleyuk on 2008-01-13
System > Preferences > Hardware Information ?

Its either under Preferences or Administration, can't remember off the top of my head.

---

### Post by p_quarles on 2008-01-13
Another way is to run this series of commands in the terminal:
```
 sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
```
This will make an web page with your hardware info, and then open up Firefox to that page.

---

### Post by steeleyuk on 2008-01-13
I should have known about that lshw command, would have helped me do a UNIX assignment much easier..

---

