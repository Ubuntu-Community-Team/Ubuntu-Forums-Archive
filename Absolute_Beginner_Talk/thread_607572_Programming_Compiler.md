---
title: "Programming Compiler"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by SkippyIsForYou on 2007-11-09
I am currently taking programming classes in school using C++. The compiler we use is Microsoft Visual Studio .NET.

Are there any compilers available in Linux that are similar to Visual Studio?

And if so, a walkthrough for installing and using it?

Thanks! Sorry for the newbie question!
~Skippy

---

### Post by tyfius on 2007-11-09
There is at this moment not a single free tool that can compete with Visual Studio.
There are some tools that come close (anjuta, kdevelop, even the latest monodevelop release has C++ support), but they all lack one big thing: a decent debugger.

Since these IDE's use G++ you are sure to have the latest and standard C++ compiler.

---

### Post by SkippyIsForYou on 2007-11-09
awwww

ok thanks!

---

### Post by doctorbighands on 2007-11-09
I'm a beginning programmer myself, and I started in Visual Studio. In my search for a replacement IDE in Ubuntu, I've settled on a program called "Geany," and I couldn't be happier with it. If you're accustomed to the look and feel of VS, then Geany is the way to go, if you ask me. You'll see a lot of folks recommending something called Anjuta; I tried it, and not only could I not get it to work very well, but I found it to not be particularly intuitive, either.

As far as a compiler goes, it's g++ around here. It integrates into Geany once you have it, so you need only use one program. Start with getting ahold of g++; open a terminal window and punch in the following:
```

sudo apt-get install g++

```
Then, once you have that, go to Add/Remove and get a copy of Geany. Write yourself a program (make it a Hello World, if you like, just to try things out), save it somewhere, then hit F8, F9, and F5, respectively, to build/compile/execute. Couldn't be easier!

Hope this helps!

---

### Post by vambo on 2007-11-09
> **tyfius said:**
> There is at this moment not a single free tool that can compete with Visual Studio.
There are some tools that come close (anjuta, kdevelop, even the latest monodevelop release has C++ support), but they all lack one big thing: a **decent debugger.**

Since these IDE's use G++ you are sure to have the latest and standard C++ compiler.
Ahem .. ever heard of gdb?

---

### Post by tyfius on 2007-11-09
> **vambo said:**
> Ahem .. ever heard of gdb?
Yes, but it is not a match for the Visual Studio integrated debugger.

---

### Post by Paul820 on 2007-11-09
Codeblocks is really good, you can use gdb from within the IDE. You get get the latest from here [http://forums.codeblocks.org/index.php?PHPSESSID=062dfa0008aedc64c3b6c7549604cc77&board=20.0]("http://forums.codeblocks.org/index.php?PHPSESSID=062dfa0008aedc64c3b6c7549604cc77&board=20.0")

---

### Post by psusi on 2007-11-09
emacs will handle all of your front end editing, building, and debugging needs.  Like most things in linux, it has a much steeper learning curve than MSVC, but once you learn how to use it, it is infinitely more powerful.

---

### Post by atlascomplete on 2007-11-15
Geany is pretty easy to use, I like it. But then again, I am a huge newb when it comes to programming.

---

### Post by kpkeerthi on 2007-11-15
You may also try Eclipse with CDT

---

### Post by kpkeerthi on 2007-11-15
Or Netbeans with C/C++ pack.

---

### Post by kd7swh on 2007-11-15
I use Emacs and Eclipse. 

check out this site for a list of IDEs:

[http://linuxmafia.com/faq/Devtools/ides.html](http://linuxmafia.com/faq/Devtools/ides.html)

---

### Post by Griff on 2007-11-15
You said you're just learning c++ in a school environment right?  I'd suggest NOT using an IDE for a while.  Learn like the people before you did: text editor and terminal.  You're the debugger. :)

---

