---
title: "Looking For A Simple C compiler"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by john585 on 2006-01-05
I want a simple C compiler.  Is there one built into the default installation of Ubuntu 5.10 or do I have to install one?   If so, what is easiest and simplest?

I'm learning C with [http://computer.howstuffworks.com/c.htm](http://computer.howstuffworks.com/c.htm) and am using djgpp in my Windows PC, but want to switch to Linux.  Any help would be appreciated. :smile:

---

### Post by Gustav on 2006-01-05
The standard c compiler is gcc. It's not installed by default but can be installed with:
```
sudo apt-get install build-essential
```

---

### Post by Kyral on 2006-01-05
And for an IDE I'd reccommend (aside from Emacs ;P) Anjuta or KDevelop

---

### Post by rubinstein on 2006-01-05
For a tiny compiler look at [http://fabrice.bellard.free.fr/tcc/](http://fabrice.bellard.free.fr/tcc/)

gcc is the standard compiler (collection) for GNU/Linux (and Ubuntu) so you also can have a look at [http://gcc.gnu.org/](http://gcc.gnu.org/)

---

### Post by john585 on 2006-01-05
Thank you.  I tried the first suggestion and it looks like I am set now.  :p 

john@ubuntu:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils dpkg-dev g++ g++-4.0 gcc gcc-4.0 libc6-dev libstdc++6-4.0-dev
  linux-kernel-headers make
Suggested packages:
  binutils-doc debian-keyring gcc-4.0-doc lib64stdc++6 manpages-dev autoconf
  automake1.9 libtool flex bison gcc-doc gcc-4.0-locales libc6-dev-amd64
  lib64gcc1 glibc-doc libstdc++6-4.0-doc stl-manual
Recommended packages:
  libmudflap0-dev
The following NEW packages will be installed:
  binutils build-essential dpkg-dev g++ g++-4.0 gcc gcc-4.0 libc6-dev
  libstdc++6-4.0-dev linux-kernel-headers make
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/10.2MB of archives.
After unpacking 41.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
Selecting previously deselected package binutils.
(Reading database ... 59101 files and directories currently installed.)
Unpacking binutils (from .../binutils_2.16.1-2ubuntu6_i386.deb) ...
Selecting previously deselected package linux-kernel-headers.
Unpacking linux-kernel-headers (from .../linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.3.5-1ubuntu12_i386.deb) ...
Selecting previously deselected package gcc-4.0.
Unpacking gcc-4.0 (from .../gcc-4.0_4.0.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.0.1-3_i386.deb) ...
Selecting previously deselected package libstdc++6-4.0-dev.
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.0.1-3_i386.deb) ...
Selecting previously deselected package make.
Unpacking make (from .../archives/make_3.80-9_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.10ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Setting up binutils (2.16.1-2ubuntu6) ...

Setting up linux-kernel-headers (2.6.11.2-0ubuntu13) ...
Setting up libc6-dev (2.3.5-1ubuntu12) ...
Setting up gcc-4.0 (4.0.1-4ubuntu9) ...
Setting up gcc (4.0.1-3) ...

Setting up make (3.80-9) ...

Setting up dpkg-dev (1.13.10ubuntu4) ...
Setting up libstdc++6-4.0-dev (4.0.1-4ubuntu9) ...
Setting up g++-4.0 (4.0.1-4ubuntu9) ...
Setting up g++ (4.0.1-3) ...

Setting up build-essential (11.1) ...
john@ubuntu:~$:D

---

### Post by coredump on 2006-01-05
If you want to verify that you have the 'gcc' compiler, try:

gcc -v

which should print the GCC version number (amongst other things).

I've been using GCC on Ubuntu (5.04 on PowerPC, Beige G3) but I've found a couple of things that are missing on the default setup.  One is the 'term.h' header file, which is part of the 'ncurses' library, which I needed to compile my favourite text editor.  Also missing are 'bison' and 'flex', the GNU versions of 'yacc' and 'lex', for writing compilers.  It's unlikely that you'll need any of these, but do be aware that sometimes a textbook or web page might get you to write a program on the assumption that some header file, library or program is present, when it's not.

If you see what I mean...

---

