---
title: "Package Installer"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by vordrix on 2008-01-09
Anytime I go to install anything through package manager I get the error "E:The package limewire-basic needs to be reinstalled, but I can't find an archive for it.", then the program closes. How do I fix this error?

---

### Post by Nimaran on 2008-01-09
This may be a dumb question, but do you have limewire installed?

---

### Post by wolfen69 on 2008-01-09
try in terminal:
```
sudo dpkg --configure -a
```

---

### Post by LowSky on 2008-01-09
> **wolfen69 said:**
> try in terminal:
```
sudo dpkg --configure -a
```

yup that should fix most issues

---

