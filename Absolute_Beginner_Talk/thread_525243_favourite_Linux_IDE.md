---
title: "favourite Linux IDE?"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by Kenobi on 2007-08-14
Hi, I want to start coding under Linux, and I know about 5 different basic dialects in Windows (and I can prog almost everything I want)  but I'm absolute new to C++, Python, have no ideas about classes, any kind of Linux API...

so my question is: which IDE should I use that makes it the easiest as possible - that means status bar help to every command, a big searchable help system, easy command-sets, all-included-packages, able to do Graphics, Sound, and some Window Creating??

Please suggest your favourite and tell my a word about what is good about it,

thanks alot,
Kenobi

---

### Post by Genecks on 2007-08-14
What do you mean by IDE?
Do you mean distribution or flavor of Linux?
Linux is from Unix.
Unix was programmed in C.
You might want to learn C.

If you want device drivers, you should learn assembly language (ASM).

C and ASM are essential to Linux.
PERL is good to use with Linux.

Are you asking about a compiler for programming?
I would not know that answer.
I do know something. There are many free compilers.

---

### Post by Mordred on 2007-08-14
I wouldn't go to ASM or C...

If you want to build gtk GUI's in C++, you can use gtkmm:

[http://www.gtkmm.org/](http://www.gtkmm.org/)

As for the IDE, a lot of people like KDevelop or Anjuta.

If you want a somewhat more lightweight editor, jEdit or Geany are very nice.


You could also take a look at python, this is an easier programming language than C++

---

### Post by Kenobi on 2007-08-14
Hi Genecks,

I mean some "Integrated Developper Environment"s, a surface on which you code an run your programs, like Mordred proposed some. I'd like to know, Mordred, do these you suggested work "out of the box"?

---

### Post by constrictor on 2007-08-14
I think with IDEs it's down to the developer to choose what they want, or what works best for them. I like Geany because it's light and fast and handles all the languages i need. C++, Python, PHP, and Perl. And uses has a decent tool chain to compile and execute code that i write provided i have configure those tools correctly.

For python i have found Guido's own IDLE to be the best for my purposes it's fast, contains built-in python shell and built on TCL. It's not the prettiest of IDEs but for me it's one of the best.

I would like to use Eclipse, and Anjuta once in a while but there are too many overhead costs in terms of memory usage. If you have a lot of processor power and RAM then by all means try those too. I once tried Komodo-Edit 4.1 for python and PHP but that too being built on the Gecko engine (famous for mozilla firefox, thunderbird, and sunbird)  can be very slow sometimes especially if you put on the active syntax checking feature.

So what i will say is try them all. Settle for the one that best fits your purpose.

---

### Post by LaRoza on 2007-08-14
The "Programming Talk" forum has a sticky devoted to favourite IDEs. I personally don't use IDE, and prefer to compile, link and run from the comman line. Actually, when I use Vim, I also edit from the terminal.

---

### Post by wieman01 on 2007-08-14
It isn't specifically a Linux IDE but I used to prefer **JBuilder** for Java (Borland). Excellent programming environment.

---

### Post by Kenobi on 2007-08-14
Hello,

thanks for your replies so far. At the moment Anjuta and Geany seam to be the most preferred. Geany sounds especially good because it supports many languages. But you said: *"And uses has a decent tool chain to compile and execute code that i write provided i have configure those tools correctly."* Is it any way pre-configured so that it will run my programs?

---

### Post by rscott5 on 2007-08-14
I use Eclipse on the Windows side and I know that it is available to Linux as well. I like it a lot because it has a lot of tools useful to people learning new languages (like helping guess what functions and classes you want to use). The one gripe I have with it is that I'm pretty sure it runs on Java and it can be a little buggy because its open source, but I haven't used it on Linux before so I can't say how well it runs there. I would recommend you take a look at it, it works great for me when I'm writing Java and C++, not sure if it supports Perl and other languages though. [www.eclipse.org]("www.eclipse.org")

---

### Post by Inxsible on 2007-08-14
I second(or third or fourth) Eclipse !!

I use it at work all the time (altho in Windows :( ) and I installed the latest in my Linux too :)

Its great for a bunch of platforms and for different languages. And I think it also has a plugin for perl and php development.

---

### Post by constrictor on 2007-08-14
As long as you have the Command Line Interfaces Installed, so that if you have installed perl, or python or PHP-CLI and you can run java from the same command-line then by default geany will be able to compile and/or execute your code.

I have not gotten it to run PHP code because i mainly use my PHP with MySQL an so on, so it will be a tad cumbersome. It runs Python pretty well and compiles and builds my c++ code as well as my perl programs.

Geany is a good choice.

---

### Post by constrictor on 2007-08-14
It supports python with the pydev plugin and i think you can get it to run actionscript and flex as well both with plugins provided by the adobe labs (i think) but my problem with eclipse is the amount of system resources it consumes. I do not have a lot of horse power on my little laptop so i can't afford that much resource usage.

If you have a powerful machine then by all means go with eclipse.

---

### Post by yellowband on 2007-08-14
depending on your project, i would use LaRosa's approach and learn the commandline, specifically vim and some unix pipe commands.  i use this approach for C projects.

for stuff like java, javascript, php, html etc, eclipse is very good.  it is adaptable to many environments.  A great plugin for eclipse is aptana.  Aptana is for web-development, mostly AJAX, but other we b projects as well including PHP and ruby on rails. After using it for my web projects i would highly recommend it, even, i dare say, over dreamweaver.   Ya i said it.

There is also a C/C++ module for eclipse. a little tricky to set up though.  

And a python development module called pydev.

---

### Post by Hospadar on 2007-08-14
You may want to look into kdevelop for c++.  While I prefer the latest eclips/cdt If I was seriously developing for *nix in c/c++ I would most likely use kdevelop.  Anjuta is nice as well, but the code completion in eclipse and kdevelop I have found to be much more powerful and that sort of think is important to me because I'm doing a lot with other people's code.

---

