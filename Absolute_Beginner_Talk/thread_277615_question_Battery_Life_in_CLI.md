---
title: "question: Battery Life in CLI"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by braddcadd on 2006-10-14
If I spend most of my time in CLI (not xterminal), it seems like my battery life is the same as when I run gnome the entire time.

---

### Post by adwait on 2006-10-15
How do you get to the CLI? If you do so by pressing Shift+Alt+F1, gnome is still running in the background. If you want to close gnome, after getting to the CLI use
```
sudo /etc/init.d/gdm stop
```

---

### Post by kidders on 2006-10-15
Hi there,

Adwait's suggestion is perfectly sensible, however you still may not notice much difference, unless you're using a sensible CPU power governor. People usually extend battery life by powering down their CPU when it's not working too hard.

---

