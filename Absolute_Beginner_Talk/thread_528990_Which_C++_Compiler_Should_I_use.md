---
title: "Which C++ Compiler Should I use?"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by jdg.gehrig on 2007-08-18
I am running XUbubtu & KUbuntu Feisty Fawn and am new to Linux.

I know how to program under Windows but I can't Program in Linux Yet. I was wondering if anyone could suggest a good C++ compiler, preferably similar to Visual Studio. I would like it to Run on my slower laptop (366mhz 128mb ram) that runs XFCE and my Desktop which Runs KDE. I need a C++ Compiler and I would like a Visual Basic Compiler also if there is one for Linux.

What is the Best C++ Compiler For Me?

Is there a C++ Compiler where I can Design the Window Visually?

The Compilers I Run Under Windows are:
Dev-C++
Visual C++
Visual Basic


Also if you have any links to websites that would help me Learn C++ in Linux I would appreciate it

Thanks in advance, John

---

### Post by Malibu Illusion on 2007-08-18
Those are IDEs, not compilers...

gcc = compiler.  G++

---

### Post by jdg.gehrig on 2007-08-18
visual studio is a compiler it is a combination of a IDE and a Compiler is there anything like this in linux?

I know about gcc but is there an ide that uses that uses it in the background?

---

### Post by Max Luebbe on 2007-08-18
As far as C/C++ goes gcc is THE compiler, period.
Unless you use intel's proprietary compiler that is, which is still a command line tool.

There are tons of front ends though - Eclipse with the CDT plugin, KDevelop, Emacs, all depends on your style of how you like to get things done.

---

### Post by jdg.gehrig on 2007-08-18
Do you know of any websites that cover C++ programing under Linux?
or is it close enough to windows for me to be able to figure it out?

I'm going to use Kdevelop if it matters.

also tutorials on KDevelop?

Thanks for the help!

---

### Post by fredj on 2007-08-19
Almost all Linux programs come with documentation so you could start by reading the manual for
whichever IDE you choose to use and the documentation for the C++ compiler.
The good thing about the Linux compiler is that you can get the real source code for almost any
sort of application you can think of. Something that is not so easy to obtain for windows.

---

### Post by Paulmd on 2007-08-19
> **jdg.gehrig said:**
> Do you know of any websites that cover C++ programing under Linux?
or is it close enough to windows for me to be able to figure it out?

I'm going to use Kdevelop if it matters.

also tutorials on KDevelop?

Thanks for the help!

```

#include <stdio.h>
int main (void){
  printf("Hello, World!");
  return 0;
}

```

Works just as well in Windows (well, DOS, really) as in Linux. C++ is C++, only thing different is there are possibly a few different libraries for system specific stuff.


You should be able to google for tutorials. 

Here's one of the first hits in google. Lots more.

[http://women.kde.org/articles/tutorials/kdevelop3/](http://women.kde.org/articles/tutorials/kdevelop3/)

---

