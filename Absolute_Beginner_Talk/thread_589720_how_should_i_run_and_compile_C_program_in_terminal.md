---
title: "how should i run and compile C program in terminal ??"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Aamir Aziz on 2007-10-24
i've written a c program in text editor nano which is placed in my home directory  i.e

#include <stdio.h>

int main()
{
        char name[64];
        printf("Hi! What's your name? ");
        scanf("%s", &name);
        printf("Hello, %s! Welcome to Ubuntu (GNU)/Linux!\n", &name);

        return 0;
}

  but the problem is i don't know how should i run and compile this program in terminal to get output ???

---

### Post by sphm on 2007-10-24
> $ gcc code.c -o yourprogname

if it doesn't work try: *gcc --help*

---

### Post by mahiyar on 2007-10-24
That is to say that the above code is saved in any directory as code.c then running the above like sphm said from the same directory, then running the program as ./yourprograme (going by the above example) BTW in the line of printf of your program &name should be replaced by name.

---

### Post by danm-koder on 2007-10-24
the post above is very accurate on compilation, you should use GCC to compile:

```
$ gcc code.c -o programName
```

Now, for runnin' it :

```
$ ./programName
```

that sould do the trick...

---

### Post by marcusklaas on 2007-12-12
hey it says permission is denied when i try to run from terminal like dat .. but the program aint owned by root. ....

wtf?

i tried

sudo ./my1337program

but that doesn't work

what ar i doing wrong?

thx

---

### Post by doas777 on 2008-01-12
> hey it says permission is denied when i try to run from terminal like dat .. but the program aint owned by root. ....

well you've probably already solved this on your own, but you likely have the file set for no execute.try running:

```
chmod +x ./my1337program 
```

to mark it as executable. that is commonly the source of your problem.

---

### Post by naugiedoggie on 2008-01-12
> **Aamir Aziz said:**
> i've written a c program in text editor nano which is placed in my home directory  i.e

#include <stdio.h>

int main()
{
        char name[64];
        printf("Hi! What's your name? ");
        scanf("%s", &name);
        printf("Hello, %s! Welcome to Ubuntu (GNU)/Linux!\n", &name);

        return 0;
}

  but the problem is i don't know how should i run and compile this program in terminal to get output ???

Hello,

If you are teaching yourself programming or otherwise studying C, run, don't walk from nano.  Either vi or emacs will be your friend.  There is a [**slew of macros**]("http://vim.wikia.com/wiki/Category:C") available for vi to help you with your programming and emacs comes with [**cc-mode**]("http://cc-mode.sourceforge.net"), which provides the same kinds of help.  

It's a pain to have to take time to learn some of these things right away, but they will save you much time and grief as you are writing your programs -- not least because they will help you detect coding errors as you make them, rather than waiting for the compiler to inform you at the end of the cycle.

Thanks.

mp

---

