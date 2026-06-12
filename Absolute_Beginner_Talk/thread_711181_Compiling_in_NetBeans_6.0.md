---
title: "Compiling in NetBeans 6.0"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by berria on 2008-02-29
Before nothing, I ask for excuses for my English!

when I try to compile a project in C with NetBeans 6.0, It gives me an error: 


main.c:8:19: error: stdio.h: No such file or directory
main.c:9:20: error: stdlib.h: No such file or directory
main.c: In function ‘main’:
main.c:16: warning: incompatible implicit declaration of built-in function ‘printf’


what's the problem?
Do I lack the libraries?
How can I obtain them?

Thank you for the help!!

---

### Post by taurus on 2008-02-29
You need the build-essential package before you can build/compile anything from source.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by berria on 2008-03-05
Thank you very much!
Eskerrikasko! (in my languaje...)

---

