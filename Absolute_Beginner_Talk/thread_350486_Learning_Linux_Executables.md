---
title: "Learning Linux Executables"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by pride_chang on 2007-01-31
**Hi there !**
First of all, I am new to linux, and I know some of programming, like VB, VB.NET.
I am not a pro programmer, I can write simple console applications in C++.

Okay, I will go straight to my point, like Windows has "EXE" files, that are not viewable, and we make them by COMPILING our application, whether in VB or in C.

I noticed Linux executables don't have any exact file extension. Even if I write a script, it changes into Executable Icon, no matter what extension it is, like if there's a JPG, I change it's extension to anything, it still displays thumbnail. That's a plus point. 
But I really want to know, how to make Linux "EXE", that I mean to say, a file which is not viewable, not source. 

Here's another question, we write .configure, make install. Some commands like that, to make a Executable File, or Install that App in Linux, what if I had that same source folder, and I want to make or install that in Windows ? 

I thought maybe opening C++ Project File in Visual Studio may do the trick, but there's no C++ Project File, there are only .c and .h files.

And the last question, what is the BEST IDE in Linux for C++ ? As most(or maybe all) of the linux programs are Open Source, I wish to edit them and them compile them, how would I do that, I know, just edit the c files would do the job, but I want to RUN the app, then make it.

Hope you people got it.

And thanks to Ubuntu Team to bring Linux into Pakistan, or maybe into my City, thanks for shipping :) :D 
Thanks in advance.

---

### Post by punx45 on 2007-01-31
this question might do better in the programming section.. i'm sure a mod will move it if asked nicely.

---

### Post by LKRaider on 2007-01-31
Hi there!

Hm, okay, let me see where to start from...

Okay, binary executables in Linux are created just like on Windows: you compile them from source code.

Differently from Windows, Linux knows what a file contains, no matter the extension you put on it.

The ./configure, make , make install routine is how you compile most programs. They are a set of utils that help to configure the compilation, execute the compilation following those configurations and install the final binary program.
Who really does the compilation tho is [GCC - the Gnu Compiler Collection]("http://gcc.gnu.org/"). It compiles code for C, C++, Objective-C, Fortran, Java, and Ada languages. Also, GCC can compile for many platforms, including Windows, if the source code is written to run on Windows.

Normally, if you want to compile the same program to run on Windows, first you need to make sure the source code supports being compiled into a Windows binary - usually you can see this on the project website. If it can, you can cross-compile the program in Linux to run on Windows. This is not very easy to do as it requires correctly setup the compilers options and environment. The best is to check if the project has instructions on their documentation on how to compile on Windows, as they usually do.

Also, source code that has .c and .h files means it is written in C, not C++, so you need a C compiler for that source. GCC can do this.

Notice that you ALWAYS have to compile before you can RUN the C and C++ source code. This is no different in Windows either.
This is only different for scripting languages, like VBScript. There is no VBScript in Linux, but we have a lot of other much better scripting languages. If you are interested in those, I would recommend you take a look at [Python]("http://python.org/"), which is used a lot in Ubuntu.

About the C++ IDE, I would recommend [Anjuta]("http://anjuta.sourceforge.net"), you can get it on Synaptic.

There are many more, as you can see on these links:
[http://www.linuxselfhelp.com/HOWTO/C++Programming-HOWTO-12.html](http://www.linuxselfhelp.com/HOWTO/C++Programming-HOWTO-12.html)
[http://linuxmafia.com/faq/Devtools/ides.html](http://linuxmafia.com/faq/Devtools/ides.html)


Hope this helps and good luck! :)

---

### Post by pride_chang on 2007-01-31
Thanks !
I used Anjuta, but it doesn't seem to have "RUN", "COMPILE" function in menu :-s
Currently I am installing Eclipse. It's a multi language developing enviroment, I just need a good IDE, simple as well, for C++, similiar to Borland C++

"MAKE", this utility comes with build-essential (That's what I think), is there any alternative for Windows ?

Thanks for reply !
---

If you feel this topic should be in Programming Section, I don't mind if moved :D

---

### Post by LKRaider on 2007-02-03
Of course Anjuta can run and compile your programs. It is under the "build" menu -> compile, build and execute.

Check out this doc for more info:
[http://www.biology.usu.edu/courses/biol5200-1/HOW-TO/AnjutaHOW.pdf](http://www.biology.usu.edu/courses/biol5200-1/HOW-TO/AnjutaHOW.pdf)


The Eclipse IDE is big and very complete, specially for Java development (Eclipse itself is written in Java), but it supports other languages through plugins.


You can use the 'make' utility in windows by running it through [Cygwin]("http://www.cygwin.com/") or with [MSYS+MinGW]("http://www.mingw.org/"). The Cygwin installer will give you many of the linux utils very easily and a complete linux-like shell inside windows. If you are interested on the MSYS+MinGW approach tho, you can look at this [wiki page]("http://wiki.openttd.org/index.php/Mingw") I wrote on how to get it working.

---

### Post by pride_chang on 2007-02-04
**Thanks ! Thanks a lot !**

---

