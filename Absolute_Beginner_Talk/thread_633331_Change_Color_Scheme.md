---
title: "Change Color Scheme"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by prodigalson666 on 2007-12-06
I was wondering if there was a way to change the human theme color that appears after the login screen until the desktop finally appears, I'd like to change that beigeish looking color, Thanks

---

### Post by skymera on 2007-12-06
try:

system>admin>login window

should be an option in thee

---

### Post by drs305 on 2007-12-06
Alternatively:

```
gksu gedit  /etc/gdm/PreSession/Default
```
Change line 61 from #dab082 (peach) to #<anycolorcode>

---

### Post by prodigalson666 on 2007-12-06
Excellent! Thank you gentlemen both methods worked!

---

