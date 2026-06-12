---
title: "[SOLVED] how to remove swiftdove"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by DarinB on 2008-02-18
swoftweasel works great added swiftdove now i have crashes how do i remove swiftdove???????

---

### Post by jan quark on 2008-02-18
how do you have installed this application ? with add/remove, synaptic, terminal, downloaded a package from the internet?


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

### Post by DarinB on 2008-02-18
thanks now my system is on for now it was crashing every move...i removed swiftdove and i am back.

---

