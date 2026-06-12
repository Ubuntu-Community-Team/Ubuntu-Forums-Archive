---
title: "more C header problems"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by coyotech on 2008-02-02
I installed the essential build program, and no problem there, but it still doesn't find the headers. I've read the manual and comments on the subject. Probably I'm missing something. I have a file called "shitfire.c" in my home directory
#include <stdio.h>
void main()
{
printf("\nShit Fire and Save Matches\n");
}

when I go to compile it, it can't find stdio.h. using "gcc shitfire.c" I've tried using -std and some other options, but it doesn't recognize them. I've tried with quotes around the file name, moving it to different locations and copying the library files into the home directory. None of that has worked. That's why hello world became **** fire and save matches :-)

How do you compile a c program and have the compiler find the headers?

---

### Post by dstew on 2008-02-02
It might be a file path problem. Try the command **locate stdio.h** to see if you can find the file anywhere on your system. By the way, how did you install the build-essential package?

---

### Post by coyotech on 2008-02-02
I used sudo apt-get install build-essential to install it. It seemed to go fine, and when I ran the command again, it found build-essential and said it was up-to-date.

stdio.h is in several locations on the computer, including the same directory as the c file.

---

### Post by Paul820 on 2008-02-02
To compile it you need the name of the source file and the name for the output. Example
> gcc -o nameOfOutputFile nameOfSource.c
For more information type this in the terminal
> man gcc

---

### Post by coyotech on 2008-02-02
ok, thanks. I'll give that a try, and see how it goes. I looked at the man gcc, but it didn't help much. I tried some of the switches, but it kept saying it didn't have them...I'll try it again.

---

### Post by dstew on 2008-02-02
Try ```
#include "stdio.h"
```That should work if the header file is in the same directory as the source file.

---

### Post by coyotech on 2008-02-02
:lolflag::
I think I've got it! Thanks for everyone's help.
I was doing a c program, which I knew. But I didn't know you should use gc for a c program and gcc for a c++ program. Maybe that's not the real reason it worked, but at any rate, when I used gc to run the c program I got an error, but at least it could find the headers!

tzofiya@lynnux:~$ gc shitfiresimple.c
Error: shitfiresimple.c:2: syntax error near line 2
context:  >>> void <<<  main()

Here's the code:
#include <stdio.h>
void main()
{
printf("\nShit Fire and Save Matches\n");
}

I don't know why it objected to void...I was just following a beginning tutorial...but at least it's not the same old problem of not being able to find the headers.

---

### Post by Cypher on 2008-02-02
Change it to the following
```

#include <stdio.h>

int main(void)
{
    printf("Hello World\n");

    return 0;
}

```

---

### Post by coyotech on 2008-02-02
gcc doesn't work, geany doesn't work because it calls gcc, anjuto just throws up a text editor and doesn't compile anything. It gives an error about a null uri in the terminal. Now I'm going to try kdevelop and see if that does any better. Maybe I need to re-install the whole OS or try a different version of Linux. gc isn't a real command, but at least it tries. But it doesn't comprehend even basic calls, although it at least tries to compile it. Probably because it's not the right command.

Ubuntu seems kind of crippled where programming is concerned, and that's the reason I installed it, because the classes want you to do c programming only in unix or linux. It's been many days and alot of work downloading things manually, configuring things manually, just to find it still doesn't work. 

Would another version of Linux be better for this purpose? I'm already in trouble in these classes due to all these problems. Spending a few more days installing another OS wouldn't make it any worse, if I c programming could be forced to work on another version before midterms.

---

### Post by Cypher on 2008-02-02
The header files are included in the "libc6-dev" package. and installing build-essential should get you all of these things.

I can't imagine that you're having a hard time getting GCC to work. 

This works on my machine
```

~$ which gcc
/usr/bin/gcc
~$ gcc --version
gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

~$ cat > hello.c
#include <stdio.h>

int main(void)
{
   printf("Hello World\n");
   return 0;
}
~$ gcc -o hello hello.c
:~$ ./hello
Hello World

```

---

### Post by coyotech on 2008-02-02
Thanks for your help and patience, cypher, dstew and paul--you've given me several things to try out, so I'll go try those before doing anything rash. 

My brain is burned out from days of trying to get this to work--the only nerve left is the grouchy one! I'll quit complaining and test what you've suggested.

For the questions, I do have the libraries installed, and the system can find them fine. I installed the libraries individually last week, downloading them and all their dependent files until it seems I finally got them all. build-essential seems ok, and that libc-6 is in there. I don't know the locations of the installations though. They all installed with the add applications application, or apt-get and I didn't give them any different installation locations. They should be in the default locations. I checked on the c library today, after installing build-essential, using the apt-get update command, and it found the library and didn't need to do anything.

Maybe there is some change I need to make to the gcc configuration...maybe downloading everything manually last week threw something off?

---

### Post by coyotech on 2008-02-02
Sorry! I was repeating myself.

---

### Post by coyotech on 2008-02-02
much progress!
The header problem seems to be gone now, and at first it still didn't work right. But each time I run it and try it again, and turn things on and off, it gets better. At last, it actually worked, using cypher's last example. I didn't change anything between tries, just did it over and over again.

You also gave me the answer to the void problem--put it inside the parenthesis instead of in front of main. Thanks again.

I think I must have messed up the installations by installing out of order. Several people seem to be having the same problem. Maybe that's what's causing it. If you go online to the program installation sites to find out about installing c rather than reading through the help file, you end up following a trail of downloads and don't know about build-essential. Possibly if you install the libraries individually they don't end up where gcc and build-essential expect them to be. That's just a theory...

---

### Post by Cypher on 2008-02-04
> **coyotech said:**
> much progress!
You also gave me the answer to the void problem--put it inside the parenthesis instead of in front of main. Thanks again.

Well the ordering in my function as opposed to yours is different because I used "int main (void)" indicating that my MAIN function is going to return an INT and it accepts no arguments, thus the void. If you do "void main(void)", then your function returns and accepts nothing.

Some compilers will let you get away with the "void main(void)" function declaration, but since MAIN is the function that gets called first, most compilers will want at least a "int main(void)" declaration and some return value to send back to the shell to make things happy.

So if you run my program and then type "echo $?" at the command prompt, you will get a value of 0. This is the return value from my program, you can confirm that by changing the "return 0" at the end of the program to something else, re-compile, run and do "echo $?" and the number will change..

---

