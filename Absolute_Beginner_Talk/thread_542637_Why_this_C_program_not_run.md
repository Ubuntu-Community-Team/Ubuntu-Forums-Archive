---
title: "Why this C program not run"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by mthalis on 2007-09-04
/* 13L04.c: Using gets() and puts() */
 #include <stdio.h>

 main()
 {
 char str[80];
 int i, delt = `a' - `A';

 printf("Enter a string less than 80 characters:\n");
 gets( str );
 i = 0;
 while (str[i]){
 if ((str[i] >= `a') && (str[i] <= `z'))
 str[i] -= delt; /* convert to upper case */
 ++i;
 }
 printf("The entered string is (in uppercase):\n");
 puts( str );
 return 0;
 }

I run this command i got below message how can correct it

ucsc@ucsc02:~/Desktop$ gcc -o 13L04 13L04.c 
/tmp/ccypdZAd.o: In function `main':
13L04.c:(.text+0x37): warning: the `gets' function is dangerous and should not be used.
ucsc@ucsc02:~/Desktop$

---

### Post by mlentink on 2007-09-04
You may get more response by posting questions like these in [this forum]("http://http://ubuntuforums.org/forumdisplay.php?f=39")

---

### Post by bashologist on 2007-09-04
```
Why this C program not run
```
It can be run, that's just a warning.

```
satan@ubuntu:~$ ./13L04
Enter a string less than 80 characters:
s
The entered string is (in uppercase):
S
satan@ubuntu:~$ 

```

You forgot to put your code in a code tag to keep the indentation.
```
/* 13L04.c: Using gets() and puts() */
#include <stdio.h>

main()
{
	char str[80];
	int i, delt = `a' - `A';
	
	printf("Enter a string less than 80 characters:\n");
	gets( str );
	i = 0;
	while (str[i])
	{
		if ((str[i] >= `a') && (str[i] <= `z'))
			str[i] -= delt; /* convert to upper case */
		++i;
	}
	printf("The entered string is (in uppercase):\n");
	puts( str );
	return 0;
}
```

Here's some good information.
[http://en.wikipedia.org/wiki/Gets](http://en.wikipedia.org/wiki/Gets)

---

### Post by paul.drover on 2007-09-04
To get rid of the warning, use fgets instead of gets. Gets, because it has no concept of how large the input data will be, will happily write excess data beyond the size of the receiving buffer. So if, in this case, someone were to enter 81+ characters, they are writing data into other areas. This, in the past, has been used to compromise systems. So the warning is there to make the coder aware of potentially unsafe coding. Fgets solves this issue by setting a maximum input size.
Paul.

---

### Post by Paulmd on 2007-09-04
> **mthalis said:**
> /* 13L04.c: Using gets() and puts() */
 #include <stdio.h>

 main()
 {
   char str[80];
   int i, delt = `a' - `A';

   printf("Enter a string less than 80 characters:\n");
   gets( str );
   i = 0;
   while (str[i]){
     if ((str[i] >= `a') && (str[i] <= `z'))
       str[i] -= delt; /* convert to upper case */
    ++i;
   }
   printf("The entered string is (in uppercase):\n");
   puts( str );
   return 0;
 }

I run this command i got below message how can correct it

ucsc@ucsc02:~/Desktop$ gcc -o 13L04 13L04.c 
/tmp/ccypdZAd.o: In function `main':
13L04.c:(.text+0x37): warning: the `gets' function is dangerous and should not be used.
ucsc@ucsc02:~/Desktop$

Actually, the program did compile fine. A warning is not the same as an error. Did you try to run it? Linux has this slightly annoying thing, where to run you program use ./myprogram, or it tells you that the command isn't found.



If you want the warning to go away, you use a different function besides gets. there are several alternatives: scanf(), getch(), getchar(). the latter 2 being used in a loop.




Some C pointers:

o    Use indenting, it makes the program more readable

o    main should be declared one of 2 ways. int main (void), or int main(int argc, char ** argv)  

o    the use of some library functions, found in string.h, and ctype.h would make this program easier. isalpha(), toupper(), strlen. well the professor is probably making you write toupper, so you can't use it :)

o   You should take care not to read more characters than the maximum length of the string. this is why the compiler is complaining about gets(), as there is no checking. extra characters go into never-neverland, and may crash the program, and can be used maliciously by hackers to run arbitrary code on your machine. Not that it's a big deal in this little thing, but if you mean  to program for a living, it becomes a concern.


o while(str[i]) is funky. you're looking for the null on the end of the string, but that might not happen in a string beyond the defined length. Or one of exactly 80 characters.  Program may work, may crash in this case, depending on pure luck.

---

### Post by dwhitney67 on 2007-09-04
> **Paulmd said:**
> Linux has this slightly annoying thing, where to run you program use ./myprogram, or it tells you that the command isn't found.

I tend to agree (because I have witnessed the same with Solaris, Fedora Core, etc), however when I installed Ubuntu, I was surprised that the default Bash environment included a ./ in the PATH environment variable.  Thus there isn't a need (at least not with my 7.04 distro) to precede the executable program with the ./.

---

