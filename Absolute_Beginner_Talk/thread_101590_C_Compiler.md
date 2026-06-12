---
title: "C Compiler"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2005-12-10
Hello,

for compiling my c-programs i've installed gcc- and libc6-package but i cann't compile my programs.
to compile a program i type :
```

gcc -o test test.c

```
and i get the error:
```

test.c:1:18: error: stdio.h: No such file or directory
test.c: In function ‘main’:
test.c:4: warning: incompatible implicit declaration of built-in function ‘printf’

```
could you informe me pl?
thanks

---

### Post by Knomefan on 2005-12-10
I'm not sure, but I think you need the libc6-dev package.

---

### Post by linux-beginner on 2005-12-10
[QUOTE=Knomefan]I'm not sure, but I think you need the libc6-dev package.[/QUOTE]
thank you, 
it works now.
bye!

---

