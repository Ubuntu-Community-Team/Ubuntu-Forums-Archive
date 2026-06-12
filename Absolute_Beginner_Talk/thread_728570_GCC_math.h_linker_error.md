---
title: "GCC math.h linker error"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by bdsatish on 2008-03-19
Hi all,


I use GCC 4.1.3 on Kubuntu 7.04. I'm trying to compile a simple C program (maths.c) :
```

#include <stdio.h>
#include <math.h>

int main(void)
{
  printf("%f",sin(2.0));
  return 0;
}

```

I used the command:
```

[bash]$ gcc -oMaths maths.c
```

But I get the strange linker error:

```
/tmp/ccCBY5E8.o: In function 'main':
maths.c:(.text+0x1b): undefined reference to 'sin'
collect2: ld returned 1 exit status
```

What is surprising is this: :Linker doesn't give error for "printf" but for "sin" . I tried everything. All the functions defined in <math.h> give this 'undefined reference' error, but functions from <stdio.h> & others do not give any error. Why is this & how to resolve it ?

---

### Post by Hospadar on 2008-03-19
The problem is that you arn't actually linking the object code of the library.  See [this]("http://www.network-theory.co.uk/articles/gccintro.html") page for more info. Basically you need to add a compiler flag to link the actual object code for the math library.
Try doing ```
gcc -oMaths maths.c **-lm**
```

In general if you need to link a library, the flag will follow the form -l<name of library>, for example, to link libpthread, -lpthread

---

### Post by bdsatish on 2008-03-19
Oh great, thanks ! I didnt know this !

---

