---
title: "Install *.tar.bz2 problem"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by hacklab on 2007-09-23
I've extracted the file 

then i write

./configure and then make:

configure: error:

The msgfmt command is required to build libpurple.  If it is installed
on your system, ensure that it is in your path.  If it is not, install
GNU gettext to continue.

roko@linux:~/Desktop/pidgin-2.2.0$ make
make: *** No targets specified and no makefile found.  Stop.

what to do?

---

### Post by Nikitas350 on 2007-09-23
run the command "sudo apt-get install build-essential" (it requires internet connection) and try again....:popcorn:

---

