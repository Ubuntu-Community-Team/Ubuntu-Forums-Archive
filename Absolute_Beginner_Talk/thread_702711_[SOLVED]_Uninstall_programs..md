---
title: "[SOLVED] Uninstall programs."
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by DamagePlan on 2008-02-20
How do I uninstall programs?

I need to uninstall Frost wire but I dont know how to this because I didn't install  the App using the Add/Remove programs.


Cheers
Dp

---

### Post by amingv on 2008-02-20
What method did you use to install it?

---

### Post by jan quark on 2008-02-20
Removing Packages in Terminal

for packages installed with synaptic
```
sudo apt-get remove --purge package
```

for downloaded packages
```
sudo dpkg -r package
```

---

### Post by DamagePlan on 2008-02-20
Thanks :)

---

