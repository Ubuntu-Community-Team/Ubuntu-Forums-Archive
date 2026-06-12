---
title: "Anjuta executing problem"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by RamZie on 2006-11-07
I am working on my transition to Ubuntu and i have a programming problem. I am new to linux :)
When I try to execute Hello world program, I get an error::

Warning:
The target executable does not exist for this Project

How can i solve this ?
Thanks.

---

### Post by Dullin on 2006-11-07
You need to be more specific.

What program are you using to make this error come up.
With what and how did you make your hello world program.
What different avenues did you try to make it work.
If it seems difficult to say, just post a screenshot.

---

### Post by RamZie on 2006-11-07
Hm.. I will try, but there is not much to say. I made a new C terminal project, and anjuta made a hello world program.
During the making of a project among other lines, anjuta printed:
Makefile.am:6: AM_GNU_GETTEXT in `configure.in' but `po' not in SUBDIRS
Makefile.am:6: AM_GNU_GETTEXT in `configure.in' but `intl' not in SUBDIRS

Build/build and build/compile worked fine. When i pressed build/execute (f3) it said no executable target..

In another project I created when trying to build i got a message :
make: ***No targets specified and no makefile found. Stop.

---

### Post by RamZie on 2006-11-07
[IMG]http://www.inet.hr/~rapletik/Screenshot.png[/IMG]

---

### Post by FraserKp on 2007-02-22
I saw this once - in my case it was because I didn't install all the prerequisites (things like automake aren't installed with Anjuta when you grab it from the Ubuntu package manager).

Anjuta will tell you what is missing when you use the new application wizard - so look carefully at all of these messages and make sure you install everything it asks for.

---

### Post by tL0z on 2007-09-19
> **FraserKp said:**
> Anjuta will tell you what is missing when you use the new application wizard - so look carefully at all of these messages and make sure you install everything it asks for.
That's not true, at least mine doesn't do it.

Has anyone solved this problem? I'm trying to program in C++ in Ubuntu but it seems it's not possible, both Anjuta and Eclipse doesn't work when running the program... :|

---

### Post by tL0z on 2007-09-20
This is kinda urgent. :(

---

### Post by tL0z on 2007-09-21
why is the support here so poor?

---

