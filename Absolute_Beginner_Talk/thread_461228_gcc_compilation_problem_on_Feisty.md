---
title: "gcc compilation problem on Feisty"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by iZmu on 2007-06-01
Hi there, while I had Edgy installed on my laptop I used it a lot to compile C programs and never had any problems. Now, under a newly Feisty installation I get the same error over and over, even with a "hello world"...
This is it:

$ gcc wtv.c
wtv.c:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
$

I have everything that is needed to compile, i think (all gcc dependencies, build-essential, ...) and still the output is always the above error...

---

### Post by Bachstelze on 2007-06-01
```
ls -l /bin/sh
```

what gives ?

---

### Post by iZmu on 2007-06-01
tks for the quick reply ;)
It gives this :-?
lrwxrwxrwx 1 root root 9 2007-06-01 15:39 /bin/sh -> /bin/bash
What is it supposed to mean?

---

### Post by Cypher on 2007-06-01
What does the wtv.c file contain??

Also, try "cpp wtv.c" and tell us what it says..

---

### Post by iZmu on 2007-06-03
wtv.c:

main {
}

cpp wtv.c output:
---------------
# 1 "wtv.c"
# 1 "<built-in>"
# 1 "<command line>"
# 1 "wtv.c"
main {

}
----------------
and it doesn't compile the file..
any suggestions? :(

---

### Post by iZmu on 2007-06-04
does anybody have a clue on how to solve this?
I keep getting the same error...

**name.c:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token**

it always points to the line where the opening brace of main is...

---

### Post by kevdog on 2007-06-04
Im sorry, but I seemed to have missed it, 

Can you just list the contents of the one file you are trying to compile -- the c program.

If you list it I can try it on my machine.

---

### Post by iZmu on 2007-06-04
For all i know, the code isn't very important since i'm getting the error on every single program i try to compile, but take this one for instance:

-------------- name.c --------------
#include <stdio.h>
#define age 19

main() {
printf("\n\nage: %d\n\n",age);
}
-------------- name.c --------------

$ gcc name.c
name.c:4: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
$

---

### Post by Cypher on 2007-06-04
Please do the following in the terminal and show us the output
```

dpkg -l | grep libc6

```

---

