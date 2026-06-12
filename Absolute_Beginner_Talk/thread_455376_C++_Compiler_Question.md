---
title: "C++ Compiler Question"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by StevenP9891 on 2007-05-26
I'm new to programming. I have a version of the GNU C++ compiler installed on my computer, yet I dont have any clue of how I'm supposed to compile the code for a basic program I wrote.

---

### Post by KIAaze on 2007-05-26
_Read the manual:_
```
man gcc
```
```
man g++
```

Ok, now that was the brutal not so helpful response. ^^

_Here's a more helpful one:_
To compile a simple hello world program:
-C code:
```
 gcc -o hello hello.c
```
-C++ code
```
 g++ -o hello hello.cpp
```

Optionally, you can also simply use:
```
make hello
```
if the program is named hello.c or hello.cpp.

make is normally used with a Makefile which contains all the necessary compilation info (for libraries, etc).

Have you already programmed in C/C++ before or not?
If not you should of course also look for tutorials on the net.
And if you don't know it yet, here's an extremely useful link when programming:
[http://www.cppreference.com/index.html]("http://www.cppreference.com/index.html")
(There is even a [Firefox search plugin]("http://mycroft.mozdev.org/download.html?name=cppreference&sherlock=yes&opensearch=&submitform=Search") for it!!!)
[B]TIP: Typing man <function/header> will give you info about C/C++ functions and headers.
Very useful when you are offline. ;)[/B]

_Now assuming you know how to program in C/C++:_
If you are using libraries, use the -L and -l options:
```
 g++ -L/lib_dir -lmylib -o hello hello.c
```

To include headers, use the -I option:
```
 g++ -I/header_dir -o hello hello.c
```
A very useful thing when creating huge programs is the [Makefile]("http://www.hsrl.rutgers.edu/ug/make_help.html").
It allows you to compile a program by simply typing "make", install it by typing "make install", remove all compiled files by typing "make clean". :)

_Looking for an IDE? (i.e: click on button to compile ^^)_
Now if you want to use a GUI for creating your program like MS Visual C++ or Borland C++ under Windows, you can do so under GNU/Linux. ;)
Here are some IDEs (Integrated Development Environment) for GNU/Linux:
-[Anjuta]("http://anjuta.sourceforge.net/") (Only one I really used until now. Very practical to create GTK apps with Glade. :) )
-[Code::Blocks]("http://www.codeblocks.org/") (cross-platform)
-[KDevelop]("http://www.kdevelop.org/") (has an RPM creation feature, but I have been unable to find a .deb creation feature :( )
-[Eclipse]("http://www.eclipse.org/") (java-based, so it might be slow, and i's also more java oriented. I never really managed to compile something with it... Seems bloated and complex. A lot of people say it's great howvever. :/)

See also:
[http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments]("http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments")

Most, if not all, IDE under GNU/Linux automatically create a Makefile for your program. :D

[Under Windows there is also [DevC++]("http://www.bloodshed.net/devcpp.html") if you are looking for a free one.
Code::Blocks also works under Windows.]

---

