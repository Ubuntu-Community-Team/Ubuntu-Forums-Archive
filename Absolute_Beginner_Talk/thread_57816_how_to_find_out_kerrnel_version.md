---
title: "how to find out kerrnel version"
date: 2005-08-17
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2005-08-17
how do i do it?

---

### Post by adwait on 2005-08-17
Use
```
dpkg -l | grep kernel 
```

---

### Post by doclivingston on 2005-08-17
To find out what kernel version you are running (the command adwait gave will tell you which ones are installed) run "uname -r" from a terminal. "uname -a" will give you the full info.

---

### Post by adwait on 2005-08-17
Aah.......oops!

---

