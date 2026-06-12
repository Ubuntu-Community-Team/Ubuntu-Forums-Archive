---
title: "need help to compile c program"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by _stanz_ on 2007-06-24
Hi there. My 1st post here.. haha..
Well, need some here. I wana compile and run a c program but got this error:

$ gcc 1.c
1.c:1:19: error: stdio.h: No such file or directory
1.c: In function &#8216;main&#8217;:
1.c:10: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
1.c:11:2: warning: no newline at end of file

wats wrong? what shd i do?
Tks!

btw: using synaptic, i  have gcc 4 installed alr

---

### Post by atria on 2007-06-24
Are you sure you executed that while in a default ubuntu console environment? Because the include paths should be already preconfigured.

It might also be due to your code too. Instead of
```
#include "stdio.h"
```
use
```
#include <stdio.h>
```

---

### Post by raul_ on 2007-06-24
sudo aptitude install build-essential

before you try compiling again ;)

---

### Post by _stanz_ on 2007-06-24
> **atria said:**
> 
```
#include <stdio.h>
```

alr in <> in my code.. i will try install essentials..
weird y isnt it installed by default

---

### Post by atria on 2007-06-24
Because not everyone needs compilers, heh

---

### Post by _stanz_ on 2007-06-24
wats next to do after i compiled and got the a.out file?

---

### Post by atria on 2007-06-24
Link it with a linker, namely ld.

Or you can change your gcc command to something like
gcc -o outputexecutable sourcecode.c

---

### Post by _stanz_ on 2007-06-24
dont know if its correctly done. i did it and got this:

$ gcc -o hello 1.c
1.c:11:2: warning: no newline at end of file

whats wrong? whats next?

---

### Post by atria on 2007-06-24
Ignore the warning, the executable should be produced already. Just execute the program with
```
./hello
```

---

### Post by _stanz_ on 2007-06-24
alrite!! tks so much!!

btw i have eclipse. is there a gd plugin to add to it so that it cant compile c programs too?
or pls recommend a gd program if any.

---

### Post by atria on 2007-06-24
Welcome, heh.

Compiling C programs with eclipse is definitely possible; it just functions as a gui frontend for gcc.
Check out CDT ([http://www.eclipse.org/cdt/downloads.php](http://www.eclipse.org/cdt/downloads.php))

---

