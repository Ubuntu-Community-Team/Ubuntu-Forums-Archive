---
title: "Compiling a C++ program"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by FuzZy2006 on 2006-07-18
I've learned c++ at school using Visual Studio and I'd like to try the same thing on linux. I have Kate, Kdevelop and other developing programs. To see their capabilities i wrote the simplest c++ program: ```
#include < stdio.h>

void main()
{
    printf("\nHello World\n");
}
```
Then ```
gcc hello.c
``` and i tried to execute the a.out file that appeared but nothing, the only thing that appeared was the ASCII Table. The errors that came from compiling were:
```
~$ gcc hello.c
hello.c:1:20: error:  stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:5: warning: incompatible implicit declaration of built-in function ‘printf’
hello.c:4: warning: return type of ‘main’ is not ‘int’
hello.c:6:2: warning: no newline at end of file

```

---

### Post by taurus on 2006-07-18
You need to install gcc and all the neccessary files first.  Open a terminal and type

```

sudo apt-get install build-essential

```
Now, compile your program again...

---

### Post by mostwanted on 2006-07-18
That's actually not a C++ program but a C program. Of course, technically most C programs are also C++ programs, but there's no reason calling it a C++ program when you only use C features and C libraries :)

---

### Post by FuzZy2006 on 2006-07-18
Those are already installed.

---

### Post by mostwanted on 2006-07-18
Maybe the extra space in < stdio.h> is to blame?

Also, main is usually declared as an int type, not void. Then you return 0 at the end to signal that the program ends without error.

---

### Post by FuzZy2006 on 2006-07-18
Loool, that was it. Thx

---

### Post by Malac on 2006-07-18
Yep it's the space in <stdio.h>

Hope this helps.

---

### Post by FuzZy2006 on 2006-10-05
i had a similar pb once ago. about that ```
error in function main you might try:
``` 
```
#include <stdio.h>
int main()
{
    printf("\nHello World\n");
return 0;
}
```

---

