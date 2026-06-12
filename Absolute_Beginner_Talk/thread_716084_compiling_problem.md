---
title: "compiling problem"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by AlperSina on 2008-03-05
alper@alper-pc:~$ gcc toplama.c
toplama.c:1:18: error: stdio.h: No such file or directory
toplama.c: In function ‘main’:
toplama.c:9: warning: incompatible implicit declaration of built-in function ‘printf’
toplama.c:11: warning: incompatible implicit declaration of built-in function ‘scanf’
toplama.c:19:2: warning: no newline at end of file



what does that mean and what can I do about it?:confused:

---

### Post by Vadi on 2008-03-05
Try this:

```
sudo apt-get install build-essential
```

And compile again (by default, Ubuntu doesn't include all of the essential compiling tools, not to take up space that won't be used. Installing that package easily sets everything up for you though).

---

