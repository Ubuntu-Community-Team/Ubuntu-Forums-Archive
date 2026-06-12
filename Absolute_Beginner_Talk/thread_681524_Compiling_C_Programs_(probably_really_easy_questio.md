---
title: "Compiling C Programs (probably really easy question)"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Kougaiji on 2008-01-29
I am new to programming C, especially programming on linux, and I recently attempted to compile a simple helloworld program, but got the error that there is no such file or directory as stdio.h

How do I fix this?

returned the message with either "gcc filename.c" and "gcc -o filename filename.c"

Thanks :)

---

### Post by RomeReactor on 2008-01-29
Hi. Try installing this package:
```
sudo aptitude install build-essential
```
**stdio.h** is provided by libc6-dev.

---

