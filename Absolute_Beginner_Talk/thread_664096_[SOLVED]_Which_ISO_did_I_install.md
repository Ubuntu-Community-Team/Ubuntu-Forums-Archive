---
title: "[SOLVED] Which ISO did I install?"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by machosos on 2008-01-10
Ok so I was wondering if there is a way to find out which ISO i downloaded and installed???  The reason I ask is because I am not sure if I am right or not but I think my system can possibly work better under one install than the other???  Is this correct???  If so is the difference in performance worth the try of installing the other ISO???

---

### Post by Blutack on 2008-01-10
> uname -a

Will tell you if you are using 32 or 64 bit.

---

### Post by jken146 on 2008-01-10
In a terminal, type ```
uname -a
```

---

### Post by drs305 on 2008-01-10
In terminal

Version:
```
lsb_release -a
```

Kernel:
```
uname -a
```

Or, System, Admin, System Monitor, System tab.

---

### Post by machosos on 2008-01-10
so does anyone know if it would be worth it to try 32 bit if i currently have 64 on a 3.0 ghz pentium 4???

---

### Post by NullHead on 2008-01-10
Nope not worth it. I would just stick with gutsy x86_64

---

### Post by machosos on 2008-01-10
thanks everyone!

---

