---
title: "apt-get install"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by ABX on 2007-10-30
How can I check a program version before installing it with apt-get install program_name?

---

### Post by haldean on 2007-10-30
```
apt-cache show packagename
```
should do the trick!

or if all you want is the version:
```
apt-cache show packagename | grep -i version
```

---

### Post by carlosjuero on 2007-10-30
Try ```
apt-get install program_name -s -V
```

This tells apt-get to not actually download/install, and to display verbose version information.

---

### Post by ABX on 2007-10-30
Thanks

---

