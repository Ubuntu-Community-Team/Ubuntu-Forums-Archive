---
title: "How to check CPU?"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by mech7 on 2008-03-13
How can i check what kind of CPU is in my computer with Ubuntu?

---

### Post by Rocket2DMn on 2008-03-13
You can do
```
cat /proc/cpuinfo
``` or ```
sudo lshw -C cpu
```

---

