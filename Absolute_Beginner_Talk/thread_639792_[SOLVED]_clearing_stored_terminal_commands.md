---
title: "[SOLVED] clearing stored terminal commands"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by mc4man on 2007-12-13
While i find using the stored commands in the terminal (arrow up, down) very useful mine's become very bloated - 400+ since gutsy rc1. Is there any way to clear them all out?

---

### Post by Dr Small on 2007-12-13
```
gedit .bash_history
```
```
Ctrl+A
```
```
Delete
```
```
Ctrl+S
```

---

### Post by tech9 on 2007-12-13
history -c

:)

---

### Post by mc4man on 2007-12-13
tried the easiest  -  history -c
works -thanks to both replies

---

### Post by Dr Small on 2007-12-13
Yeah, I never knew about history, so that would be the easiest route ;)

---

### Post by tech9 on 2007-12-13
> **mc4man said:**
> tried the easiest  -  history -c
works -thanks to both replies

your welcome! :)

---

