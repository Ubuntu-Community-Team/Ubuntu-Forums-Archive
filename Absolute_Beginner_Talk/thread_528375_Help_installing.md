---
title: "Help installing"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by hackxxcrack on 2007-08-17
im trying to install a progam, these are the instructions:

1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

But when i type make it says:
make: *** No targets specified and no makefile found.  Stop.

And when i type make install (sudo make install too) it says:
make: *** No rule to make target `install'.  Stop.


Anyone could help?

---

### Post by Hobo Joe on 2007-08-17
Well, first I think I should ask what you are installling?


Second, 'make' will not work unless you have the terminal operating in the directory of the program the you are trying to compile, so that is most likely the issue.

---

### Post by hackxxcrack on 2007-08-17
> **Hobo Joe said:**
> Well, first I think I should ask what you are installling?


Second, 'make' will not work unless you have the terminal operating in the directory of the program the you are trying to compile, so that is most likely the issue.

Im installing some kinda toolbar, and im in the folder... it just doesnt works

---

