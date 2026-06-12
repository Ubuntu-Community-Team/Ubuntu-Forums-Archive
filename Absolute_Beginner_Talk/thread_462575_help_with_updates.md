---
title: "help with updates??"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by yazeed1984 on 2007-06-02
hello im a new user of ubuntu and there is a problem in the updates when i click the updates to install this message comes out::
[PHP][PHP]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. [/PHP][/PHP]


please help:(:(

---

### Post by taurus on 2007-06-02
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo aptitude update
```

---

### Post by yazeed1984 on 2007-06-02
hanks taurus it worked;)

---

