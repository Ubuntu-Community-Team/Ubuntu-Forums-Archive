---
title: "i need help on removing a program [Resolved]"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by durundal on 2006-11-18
hello, I am using Edgy and I have installed a program that I don't know how to remove.  It originally came in an .rpm package but i used a tool to convert it to a .deb and then I installed it.  It installed successfully, but the program fails to open, so how can I remove this program?

---

### Post by taurus on 2006-11-18
Probably with

```
sudo dpkg -r <package name>
```

---

### Post by aysiu on 2006-11-18
If you installed it with *dpkg* or *gdebi*, you can remove it the way you would any other .deb--using Synaptic, Adept, or *aptitude*: ```
sudo aptitude remove *nameofprogram*
```

---

### Post by durundal on 2006-11-18
cool thanks for the help

---

