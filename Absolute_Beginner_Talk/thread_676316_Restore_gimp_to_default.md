---
title: "Restore gimp to default"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by SpinningAround on 2008-01-23
Is there any way to restore gimp to default, as it looked when you first started it?

---

### Post by rhc on 2008-01-23
You can try **complete removal** option from Synaptic.

---

### Post by sisco311 on 2008-01-23
yes you can remove the .gimp-2.4 directory from your home folder(press Ctrl+h in nautilus to show hidden files). next time you run gimp will recreate this directory with the default setting files
the terminal command is:
```
rm -rf ~/.gimp-2.4/
```

---

