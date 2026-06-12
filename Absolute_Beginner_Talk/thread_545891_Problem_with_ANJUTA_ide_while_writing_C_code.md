---
title: "Problem with ANJUTA ide while writing C code"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by shankhs on 2007-09-08
I have Just installed ANJUTA by

sudo apt-get install anjuta

Wen I tried To write a simple C program like:
#include<stdio.h>

int main()
{
printf("\nHello");
return 0;
}
I got the following error messages:

test.c:8:18: error: stdio.h: No such file or directory
test.c: In function ‘main’:
test.c:12: warning: incompatible implicit declaration of built-in function ‘printf’

I am clueless.How to add file or directory in ANJUTA?
Plz help.I am anewbie to linux.

---

### Post by shankhs on 2007-09-08
I am using 7.04 Feisty Fawn.
I dont know how to see the edition of ANJUTA.

---

### Post by lisati on 2007-09-08
I'm not familiar with ANJUTA or how to tinker with its settings.

Have you tried using GCC from the terminal to compile the file? If so, did you get a similar error message?

You might have to use something like:
```

sudo aptitude install build-essential

```

---

### Post by shankhs on 2007-09-08
Thanx lisati,
It was a gr8 help.
Not only 2 me but 2 my classmates also.

---

