---
title: "[SOLVED] gcc problem"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by antisocialist on 2007-12-27
imm not sure if its the compiler (gcc) or something else, but the following doesnt work
i got a book ( c for dummies ) and when i make a code that SHOULD work, because it is so basic and it is in the book and shows it should work.
```
#include <stdio.h>

int main ()
{
	puts("Greetings, human!");
	return(0);
}
```
i put that as my code, dumb.c compile it with gcc using the command im suppose to, and then double clicked the executable file and nothing happened. why doesnt anything happen? the book says it is suppose to say "Greetings, human!" and it doesnt do anything,

if its ubuntu, then i can do all this from something else, (like debian) but i would prefer to do it on ubuntu

TIA,
antisocialist

P.S.
the program is attached, if you wanted to see, just download it and then right click and choose rename and rename it to dumb

---

### Post by p_quarles on 2007-12-27
Works fine for me. You need to make it executable:
```
chmod 744 dumb
```
Then, run it from the current directory:
```
./dumb
```

---

### Post by LaRoza on 2007-12-27
> **p_quarles said:**
> Works fine for me. You need to make it executable:
```
chmod 744 dumb
```
Then, run it from the current directory:
```
./dumb
```

You don't need the first command, only the second.

If you don't specify a name, it is called "a.out"
```

gcc dumb.c
./a.out

```

---

### Post by p_quarles on 2007-12-27
Really? I can't get it to run with the default permissions. Am I doing something wrong?

---

### Post by antisocialist on 2007-12-28
i did the command
gcc dumb.c -o dumb

is that ok for compiling it, or do i need to do something else

---

### Post by antisocialist on 2007-12-28
```
cd /dir/to/compiled/program
/dir/to/compiled/program/the_program
```
i did it

---

### Post by LaRoza on 2007-12-28
> **p_quarles said:**
> Really? I can't get it to run with the default permissions. Am I doing something wrong?

When I compile something, I don't have to chmod it.

---

### Post by p_quarles on 2007-12-28
> **LaRoza said:**
> When I compile something, I don't have to chmod it.
Gotcha. I had to because I downloaded it (yes?).

---

### Post by antisocialist on 2007-12-28
if you saved it to a root access only dir then you would need sudo to run it, otherwise i cant see why, mine is in sub folder of my home folder, and i didnt need sudo to run or compile it

---

