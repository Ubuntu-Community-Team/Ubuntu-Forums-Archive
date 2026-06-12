---
title: "Ubuntu winipcfg equivalent"
date: 2005-12-24
forum: Absolute Beginner Talk
---

### Post by kiku2 on 2005-12-24
Hello,
Was wondering if there is a command in ubuntu to reset my ethernet adapter? In heavy traffic times using win98 it helps to reset adapter to get online. Thanks for your help.

---

### Post by kaamos on 2005-12-24
Assuming your interface is eth0
```
sudo ifdown eth0
sudo ifup eth0
```

---

### Post by kiku2 on 2005-12-24
Yes mine is eth0. Thanks for the info.

---

