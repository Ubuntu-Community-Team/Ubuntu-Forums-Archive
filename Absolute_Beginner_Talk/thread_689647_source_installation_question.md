---
title: "source installation question"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by thebestofall007 on 2008-02-06
hello, i am new at installing programs from source and i am wondering that it means when the terminal outputs "make: *** No targets specified and no makefile found.  Stop.
" after inputting "make"?  this is typically have the problems. heres a snapshot to help. i want to get the hang of installing from source so i do not have the terminal scare me off of linux like it typically does some people.

---

### Post by ptn107 on 2008-02-06
You need to specify a command after *make*, such as *make install* or *make clean*.  Find the *makefile* in the source folder your trying to build, open it with a text editor, and browse through the file to see what options you can specify for *make*.

This might help.
[http://www.gnu.org/software/make/manual/make.html#Goals]("http://www.gnu.org/software/make/manual/make.html#Goals")

---

