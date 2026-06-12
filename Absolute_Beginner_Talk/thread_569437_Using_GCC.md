---
title: "Using GCC"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by anoopyadav on 2007-10-07
HI. I've encountered few problems regarding the use of gcc.

1). Warnings relating implicit declarations of printf() scanf() etc.
2). Following Error:
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status

I'm quite new to linux so any help will be great.
Thanx.

---

### Post by Celegorm on 2007-10-07
Try ```
sudo apt-get install build-essential
``` in the terminal.

---

### Post by anoopyadav on 2007-10-12
I'm still getting the error regarding implicit declarations. Any idea what i'm doing wrong??? I just tried compiling a simple Hello World! program but no output file.

---

### Post by Shin_Gouki2501 on 2007-10-12
use -h then get a parameter check so try to specify an outputfile

---

### Post by jordanmthomas on 2007-10-12
Well, this may be a dumb question but is
```
#include <stdio.h>
```
in your c file?

To compile, you should just have to
```
gcc -o hello helloworld.c
```
or something similar.

Even if you don't put the include, printf should still work, but warnings are not fun.

---

### Post by anoopyadav on 2007-10-15
Nope, still getting the same freakin' warning. Gosh! any other tricks...

---

### Post by LaRoza on 2007-10-15
With the first warning, that is a sign that the header <stdio.h> was not included.

---

