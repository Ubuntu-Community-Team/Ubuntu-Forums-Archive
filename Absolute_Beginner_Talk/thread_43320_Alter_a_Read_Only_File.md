---
title: "Alter a Read Only File?"
date: 2005-06-21
forum: Absolute Beginner Talk
---

### Post by halfpower on 2005-06-21
I need to ad a line to file /etc/modprobe.d/arch-alias.  The file is read only.  Can anyone tell me how I can alter it?

---

### Post by scourge on 2005-06-21
Use sudo: ```
sudo gedit /etc/modprobe.d/arch-aliases
```

---

