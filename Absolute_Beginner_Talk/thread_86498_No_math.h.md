---
title: "No math.h?"
date: 2005-11-05
forum: Absolute Beginner Talk
---

### Post by Freddie on 2005-11-05
Today I wanted to try out a program that I made on my Mac, now it is written in ANSI C so I did not expect any problems, but when I tried to compile the program I was horrified to find out that /usr/include/math.h did not define any functions (e.g. tan cos sin)! Could someone please tell me why ubuntu is missing part of the C standard library (or has an incomplete version of it)? Is it some kind of joke?

---

### Post by gord on 2005-11-05
works perfectly fine for me, are you sure your including math.h right? are you sure /usr/include is on your include path to gcc? 

just to note, if ubuntu had an incompleate c standard library, most programs wouldn't compile ;).

---

### Post by Freddie on 2005-11-05
Yes, it is on my include path. math.h does exist, but it is incomplete (no functions). What should I do?

---

### Post by gord on 2005-11-05
have you tryed using C++ templates. 
```

#include <math.h>
using namespace std;

int main(void) {
    float tmp;
    tmp = cos(20.0);
    return(1);
}

```

that should compile fine. and im not sure you need the namespace thing.. i just don't want to open eclipse to test it right now... saying that its a bit of a memory hog is an insult to memory loving pigs everywhere.

---

### Post by Freddie on 2005-11-05
That works, however it does not work from C
```

#include <math.h>

int main ()
{
     cos(20);
     return 0;
}

```
Fails saying that cos is undefined.

---

### Post by gord on 2005-11-05
okay, screwed my head back on now. sorry for not getting it right before but its been a long time since iv done anything in pure C. 

just add -lm to the linker, it will link to libm and should work fine :)

---

