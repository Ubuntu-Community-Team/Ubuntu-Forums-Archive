---
title: "Which files needed for terminal commands?"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Sand Lee on 2007-04-29
What files do i need to run this set of commands in the terminal or any similar commands i may come across when trying to install a Linux app. Right now I am using a new install of Feisty and i am trying to install mail notification 4.0 

```
$ ./configure
$ make
$ make install

```

---

### Post by zetsumei on 2007-04-29
you won't need any files.  just download the app ./configure it the make it then make install.

---

### Post by annda on 2007-04-29
if you want to *compile* your programs from sources, you need the compilers. they all in a package that you can easily install:

```
sudo apt-get install build-essential
```

but you can *install* most programs from synaptic.

UPDATE: a guide to compiling on ubuntu:
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by Sand Lee on 2007-04-29
I've tried that earlier but i recieved errors like:

. /configure no such file or directory
configure: error: C compiler cannot create executables
make: *** No targets specified and no makefile found.  Stop.
configure: error: unable to find the GTK+ library
configure: error: unable to find the GNOME libraries

I searched google for help and tried installing these files:

build-essential
libgtk2.0-dev
libeel2-dev
libedataserverui1.2-dev
libgmime2.1-dev

that's how the error message changed after each try..:confused:

Oh and thanks for teh linky annda

---

