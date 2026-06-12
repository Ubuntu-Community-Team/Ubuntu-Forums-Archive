---
title: "i have a problem with compiling"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by Wellig on 2007-09-26
What could the problem be, if I get a massage like this when compiling:

> /usr/bin/ld: cannot find -lXtst
collect2: ld returned 1 exit status
make: *** [driver] Error 1


---

### Post by 900donuts on 2007-09-26
what are you trying to compile?

---

### Post by Dr Small on 2007-09-26
Exactly... What are you trying to compile ?
Perhaps if we had the name, we could recommend how to do it, or a command to install it from the repositories.

By the way, to compile applications from source, you will need build-essentials

```
sudo apt-get install build-essentials
```

Dr Small

---

