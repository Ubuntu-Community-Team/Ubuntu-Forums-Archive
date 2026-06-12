---
title: "What is linux made of!"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-10-10
Is linux made od C++?
Are the apps made in C++ (The ones thast run native on linux)
IS there any ide's for C++ and a compiler? I want to get into it. :)

---

### Post by blendmaster on 2006-10-10
As far as I know, Linux is built using C, and Ubuntu is built with Python.

(though correct me if I'm wrong) ;)

---

### Post by jd65pl on 2006-10-10
[linux.org]("http://www.linux.org/") may hold some of the answers to your questions!

---

### Post by David_T on 2006-10-10
Linux is written in C, to be compiled with the gcc compiler.  You can download the source at kernel.org.
The book by kernighan and ritchie is considered the classic on C, and I'm sure you can find a bunch of tutorials on the web that show you how to write things in C using the gcc compiler.

---

### Post by IYY on 2006-10-10
Apps can be made in many languages: C, C++, Python, Perl, Lisp, Java, C# (mono), and others. Linux, the kernel, is written in C.

---

### Post by Ben Sprinkle on 2006-10-11
So then most of the main executables here on linux are made in C?

---

### Post by Lord Illidan on 2006-10-11
The kernel is made in C, that much I do know.

You can write apps in most any language..python,c,c++..whatever!

---

### Post by petersjm on 2006-10-11
Whilst the kernel is in C, it seems that Python is a favourite for many apps.

---

### Post by bluenova on 2006-10-11
If you want to get into coding, everyone I've spoken to would really recomend Python. Take a look here:
[http://www.python.org/about/gettingstarted/](http://www.python.org/about/gettingstarted/)

---

### Post by wieman01 on 2006-10-11
A lot of blood & sweat. Apart from that the kernel is plain C.

---

### Post by fiztlen on 2006-10-11
[Linux is People!]("http://en.wikipedia.org/wiki/Soylent_Green")

Actually, if you don't mind a metaphorical moment, people might not be a bad answer.  Made of a lot of volunteered time and effort, or as weiman01 put it: > A lot of blood & sweat.

---

### Post by Delkster on 2006-10-11
> **Goat Spirit said:**
> Is linux made od C++?
Are the apps made in C++ (The ones thast run native on linux)

The kernel (the core of the operating system) has been written in C, as have most of the basic UNIX commands.

The GNOME desktop environment, which is the default graphical desktop in Ubuntu, has also been written (mostly) in C, whereas KDE, the default desktop for Kubuntu, has been written mostly in C++.

Some of the base system tools have been written in Perl, Python or other interpreted high-level languages.

Many (also graphical) applications and utilities have been written in C or C++, depending on your choice of desktop (see above), but particularly nowadays many developers have also chosen to use high-level languages such as Python, and some also use C#. In applications and tools developed by Ubuntu/Canonical itself, Python is widely used.

So, since all Linux-based full-scale operating systems are always constructed from a number of independent components developed by independent projects, the whole system isn't written in any single language (and it probably shouldn't be -- the right tool for the right job and so on). That said, C is traditionally used quite widely on UNIX/Linux.

> IS there any ide's for C++ and a compiler? I want to get into it. 
There's G++, the GNU C++ compiler, which is just that, a compiler, to be operated from the command line. It's not an editor or IDE where you'd write your code.

As for IDEs, for KDE there's at least KDevelop (which I've never used) and for Gnome there's Anjuta. Both also work across the desktop borders, as do applications in general. There's also some kind of a C/C++ plugin or extension for Eclipse but I have no idea how well it works.

---

### Post by Ben Sprinkle on 2006-10-11
I am talking about like apps, executables.
I always thought python was for the web, you can compile it into an executable?
I have been doing java and vb for awhile so I know some of this.

---

### Post by Ben Sprinkle on 2006-10-11
Wait a sec, most people say C is good for making apps.

---

### Post by skymt on 2006-10-11
You can write a Linux application in almost any language you can think of, Python included. Python isn't "compiled", but since the interpreter is included with Ubuntu, Python applications will run on any Ubuntu system.

---

### Post by Ben Sprinkle on 2006-10-11
Alright I'll try some Python then, I want to make a program but if it's not compiled, it caan be edited by anyone?

---

### Post by petersjm on 2006-10-11
> **Goat Spirit said:**
> if it's not compiled, it caan be edited by anyone?

Edited by anyone is good, yeah? I mean, this is open-source we're talking about! :)

---

### Post by Ben Sprinkle on 2006-10-11
I want closed source, I don't do open source on every project I do. That's why I wanted C.
I will try out both and see which I like when I get home.

---

### Post by Ben Sprinkle on 2006-10-11
Acutally ferget that. ^
I will just keep working in my best, Java. Open source also. :)

---

### Post by skroll on 2006-10-11
> **Goat Spirit said:**
> I want closed source, I don't do open source on every project I do. That's why I wanted C.
I will try out both and see which I like when I get home.

No offense, but open source is the reason GNU/Linux is where it's at.  You're supposed to share what you d.

---

### Post by Ben Sprinkle on 2006-10-11
> **Goat Spirit said:**
> Acutally ferget that. ^
I will just keep working in my best, Java. Open source also. :)
Actually no, you do not **have** to share it.

---

### Post by petersjm on 2006-10-12
> **Goat Spirit said:**
> Actually no, you do not **have** to share it.

No, you don't. There's no law saying you have to. But isn't the *point* of Linux and Linux-apps *to be open source and freely available to all*?

The Ubuntu philosophy states:

> that software should be available free of charge, that software tools should be usable by people in their local language and despite any disabilities, and that people should have the freedom to customise and alter their software in whatever way they see fit.

---

### Post by puppy on 2006-10-12
In my experience people have been loathe to recommend closed source programs to me in linux so, if you want your apps to be popular, keep them opensource  ;) 

The whole philosophy of the linux community (and what gives us an unsurmountable advantage over the Windoze community) is that we are able, in fact encouraged, to look at, alter and improve code if we want to - I believe that the primary benefit of this is that with all those people being able to scrutinise how apps are written, there is virtually no chance that a program writer could sneak malware into the code... that's one of the main reasons that linux remains trojan/virus free :D

I might also say, and perhaps this is more important, I am convinced that linux is made of slugs and snails and puppy dogs tails, so there :p

---

### Post by xpod on 2006-10-12
It`s made of "sugar and spice and all things nice".......NOW you just get yer heird doon cause you should be in school learning your ABC first

---

### Post by Ben Sprinkle on 2006-10-12
I already Learned my abc. ;)
Time to learn my C++. :)

Well I will probably always have open source anyway. Some apps I keep closed source though.

---

### Post by petersjm on 2006-10-12
I'm not a programmer. I'd love to learn, but don't have the time. Best I can do is HTML, JavaScript and CSS. But I would have thought that if you created this nifty little program that does all sorts of whizzy stuff, you'd want to open up the code for others to see so you can say "Hey, look at my coding; see how clever I am?!" :) I don't know... Maybe I'm being naive?

---

### Post by Ben Sprinkle on 2006-10-12
Well in the windows world, you want to keep as much stuff as you can to your self. I have been developing Java and VB applications in linux for over a year now, they get a bit greedy. Have to learn the linux ways. :)

---

