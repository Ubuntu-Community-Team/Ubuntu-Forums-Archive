---
title: "Compiling a Program"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-10-17
There is a Program that I have downloaded that must be compiled.
I've never compiled anything in my life and would like to know
what I need to do so.  I am assuming I will need to install some
compiling programs from the Repositories.  Could someone
help me with the tools I need.... Thank you.

Here is the program I wish to compile.
the author stated that he's got a new
version out but it must be compiled.

[http://sourceforge.net/projects/freera](http://sourceforge.net/projects/freera)

---

### Post by Paul820 on 2007-10-17
From the terminal type
> sudo apt-get install build-essential

Looking at the docs you also need SDL

> sudo apt-get install libsdl1.2-dev

---

### Post by Orbital75 on 2007-10-17
Thanks...... :)

---

### Post by Paul820 on 2007-10-17
I don't know if you know how to compile it, if you do, ignore this, if you don't then extract the archive to your desktop and in the terminal go to the folder

> cd ~/Desktop/freera++/

Then just type

> make

There is no configure file.

---

### Post by Sef on 2007-10-17
Read [How to Install Anything in Ubuntu]("http://www.monkeyblog.org/ubuntu/installing/").

---

### Post by Orbital75 on 2007-10-17
> **Sef said:**
> Read [How to Install Anything in Ubuntu]("http://www.monkeyblog.org/ubuntu/installing/").

Great Informative Site !!!!!

---

