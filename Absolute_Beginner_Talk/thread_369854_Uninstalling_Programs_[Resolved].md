---
title: "Uninstalling Programs [Resolved]"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by Jphenow on 2007-02-25
Say I installed some programs via konsole that won't happen to show up in Add/Remove, what can I do, is it unlike Windows in where I can just delete the file or is there more I must do???

---

### Post by taurus on 2007-02-25
You can remove it from a terminal with the apt-get or aptitude.

```
sudo aptitude remove **program_name**
-or-
sudo aptitude --purge remove **program_name**
```

Even though some programs won't show up in the menu, you can still run them from a terminal by typing in the name of those programs.

---

### Post by Jphenow on 2007-02-25
Ah I see, well thanks much!

---

