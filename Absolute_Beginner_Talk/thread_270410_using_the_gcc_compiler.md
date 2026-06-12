---
title: "using the gcc compiler"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by sedi on 2006-10-03
Hi,

I'm trying to learn C at the moment but I just don't manage to get anything compiled even though the necessary compilers are installed. I use KDevelop to create the source files and as far as I can tell there's no such thing as a button to push to compile. So I tried it with terminal commands for the gcc compiler but no luck either.

What I tried was:

gcc -o chapter1.c

and I was in the folder where chapter1.c is stored. The man page for gcc didn't really help me either. What am I doing wrong?

---

### Post by ironfistchamp on 2006-10-03
I think it should be

```


gcc chapter1.c -o chapter1


```

Then you ./chapter1 to run it.

I hope that is right I haven't programmed with C in a while.

I am currently using python. Maybe you should check it out.

Ironfistchamp

---

### Post by David_T on 2006-10-03
You just need to tell gcc what to call the compiled program (object file).

```
gcc -o chapter1 chapter1.c
```

Or this works too, it will just give you something called a.out instead of naming your program:

```
gcc chapter1.c
```

OR, thirdly, you could write a file called Makefile in the directory your c program is in, and put something like this in it:

```

chapter1:    chapter1.c
                  gcc -o chapter1 chapter1.c

```
After the colon, that's an actual tab, not just spaces.
Then you just have to type "make".  Some editors like vim and emacs and others I'm sure have a button that will do the equivalent of typing the command "make" and hitting enter for you, as well.

Have fun!

---

### Post by sedi on 2006-10-03
Thank you for your help. Now I have an excecutable file. It doesn't work but I guess there's a mistake in my source code.

---

