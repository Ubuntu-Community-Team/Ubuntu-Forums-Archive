---
title: "Manually run dpkg --configure -a'"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by clemkonan on 2007-05-21
Please refresh my memory I was trying to install Java run time 6 and ran into a problem. How to I run dpkg --configure -a' manually?

Thanks

---

### Post by Kobalt on 2007-05-21
Open up Applications > Accessories > Terminal, and enter : ```
sudo dpkg --configure -a
```

---

### Post by taurus on 2007-05-21
Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```

---

