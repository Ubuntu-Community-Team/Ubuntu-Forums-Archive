---
title: "Terminal doesn't recognize standard libraries"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by ConMan318 on 2008-04-05
Hello everyone.  I have just installed Ubuntu, and I'm having problems in the terminal compiling.  I wrote a 'hello, world' program just to test it out ( I am not new to C, just to Linux ), and I am getting errors.  For some reason, the compiler isn't recognizing the C standard libraries.  Here is the error:

test.c:1:18: error: stdio.h: No such file or directory
test.c: In function ‘main’:
test.c:4: warning: incompatible implicit declaration of built-in function ‘printf’

and the program:

#include<stdio.h>

int main ( void ) {
   printf( "Hello, world!\n" );
   return 0;
}

I've also tried including some other libraries, it doesn't recognize any of them.  I saved this program as test.c and compiled it in the terminal with gcc test.c

How can I get the compiler to recognize the libraries?

---

### Post by bubba_169 on 2008-04-05
Open a terminal and type:

```
sudo apt-get install build-essential
```

Try compiling again to see if that solves it?

---

### Post by Joeb454 on 2008-04-05
I assume you are aware that after installing the build-essential package, if you use the same command to compile, it will output to a.out :)

---

### Post by ConMan318 on 2008-04-05
Thank you, Bubba, that did fix the compiling errors, and yes I do know that it will output to a.out

Now I have a new problem: it compiles just fine, but it won't run the program...

connor@connor-laptop:~$ gcc test.c
connor@connor-laptop:~$ a.out
bash: a.out: command not found

I also tried renaming the file with the -o thing, and when I try to run it, it gives the same thing.  I am pretty sure I am in the right directory, since a.out is in the list of things if i type 'ls'.  Do I need to type something else to run the program besides just the name of the program?

---

### Post by Joeb454 on 2008-04-05
prefix the filename with ```
./
```

So if you're file is a.out you would use ```
./a.out
```

---

