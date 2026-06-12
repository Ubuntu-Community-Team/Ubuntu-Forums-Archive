---
title: "required X11 libraries"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by LouWho on 2007-03-22
Hi

Fairly new to Linux, very new to Ubuntu.  I unzipped fltk-1.1.6 (required for some work that I am doing), went to './configure' and got 'c compiler cannot create executables'.
I got by that by doing '$ apt-get install libc-dev g++'.  Did the ./configure again and got the 'configure could not find the required X11 libraries", did the 'sudo apt-get build-dep libfltk1.1' that I found in another posting here and tried again...I still get the same error.
what to do?  T:) hanks

---

### Post by WW on 2007-03-22
A convenient way to get the C/C++ compilers, along with the **make** command and some other  stuff, is to install the packge **build-essential**.

I have compiled fltk, but I don't know which packges were required--I probably had a lot of them installed already.  One that you will almost certainly need is **libx11-dev**.

You can make sure you have them both with the command
> sudo apt-get install build-essential libx11-dev

---

### Post by WW on 2007-03-22
P.S. You didn't say why you were compiling FLTK from source.  Did you know that FLTK is available from the Ubuntu repositories?  Here is the result of doing a search for **fltk** at packages.ubuntu.com:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=fltk&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=fltk&searchon=names&subword=1&version=all&release=all)

---

### Post by LouWho on 2007-03-22
I did the command....
build-essential is already the newest version
libx11-dev is already the newest version
0 upgrades, installed, etc., etc.

Tried the ./configure and get same error
configure could not find...
line 8268 exit aborting numeric argument required.

Why am I doing this...
First I must use fltk 1.1.6.  As part of a piece of our product I must do pretty much the same thing on Windows, Linus, and Solaris. My instructions are, (on Linux and Solaris),
./configure
make
make install

I will be doing this, (along with a few other things), on the Ubuntu VM, then putting this into a perl script, and then the perl will be executed on the three different build systems.  I am learning Linux, perl, etc as I go, (I have the windows part done).  Actually, some months ago I had done this successfully on a Fedora system, but after a hard disk crash that was all lost, along with my notes.  So, I am trying to get this done manually to see that it can be done, before I write the perl script.

I appreciate any help.  Thanks

---

### Post by WW on 2007-03-22
Ubuntu breezy had FLTK 1.1.6. Here is a link to the src package on packages.ubuntu.com:
   [http://packages.ubuntu.com/breezy/source/fltk1.1](http://packages.ubuntu.com/breezy/source/fltk1.1)
This shows the "build-depends" of the package.  Try installing all the *-dev packages indicated with the red icons.   (You say you already ran **sudo apt-get build-dep fltk1.1**, so this might not help--but perhaps the build-dependencies have changed, and the dependencies for 1.1.7 are not packaged the same in dapper or edgy as they are for 1.1.6 in breezy.)

By the way, the error "line 8268 exit aborting numeric argument required." is strange.

---

