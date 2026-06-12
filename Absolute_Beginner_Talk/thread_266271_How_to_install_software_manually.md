---
title: "How to install software manually"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by itisgood on 2006-09-27
hi everyone.

i have tried to install couple of new softwares , but it seems i cant install any of them

very generally, the install guide will say something like :

   $ ./configure --prefix=PREFIX
     $ make
     $ make install
     $ PREFIX/bin/apachectl start

then when i type >make. i always get

jyao@jyao-laptop:~/httpd-2.2.3$ make
make: *** No targets specified and no makefile found.  Stop.
jyao@jyao-laptop:~/httpd-2.2.3$

and i also tried to add some module.

jyao@jyao-laptop:~$ cd DBD-Pg-1.49
jyao@jyao-laptop:~/DBD-Pg-1.49$ perl Makefile.PL
Configuring DBD::Pg 1.49
Remember to actually read the README file!
OS: linux
PostgreSQL version: 80104 (default port: 5432)
Using DBI 1.50 (for perl 5.008007 on i486-linux-gnu-thread-multi) installed in /usr/lib/perl5/auto/DBI/
Writing Makefile for DBD::Pg
jyao@jyao-laptop:~/DBD-Pg-1.49$ make
cc -c  -I/usr/include/postgresql -I/usr/lib/perl5/auto/DBI/ -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -DPGLIBVERSION=80104 -DPGDEFPORT=5432 -O2  -DPERL_EXTMALLOC_DEF -Dmalloc=Perl_malloc -Dfree=Perl_mfree -Drealloc=Perl_realloc -Dcalloc=Perl_calloc -DVERSION=\"1.49\" -DXS_VERSION=\"1.49\" -fPIC "-I/usr/lib/perl/5.8/CORE"   Pg.c
[B]/bin/sh: cc: command not found
make: *** [Pg.o] Error 127[/B]
jyao@jyao-laptop:~/DBD-Pg-1.49$

it seeams my make just never work???

thanku for reading my post
any thoughts could be helpful.

---

### Post by meborc on 2006-09-27
you need to have build-essential package to build stuff from source... to get it:
```
sudo aptitude install build-essential
```

---

### Post by pay on 2006-09-27
and to get the dependencies try```
sudo apt-get build-dep <package>
```

---

### Post by itisgood on 2006-09-27
oh its great, 

thank u for your advice, it works, i installed it ,and now my make works.

but i did not do the thing in your 2nd reply, 

cuz i dont know what is the <package>?

or your mean when i download any package, i should install the dependency in this way?

---

### Post by Bachstelze on 2006-09-27
The build-dep xxx line will install all the packages (libs and such) required to build the package xxx, but it will only work if the package is in the sources repos (and you have them activated). Try to compile your stuff without running build-dep first, and see if it works.

---

### Post by Daniel15 on 2006-09-27
> but i did not do the thing in your 2nd reply, 

cuz i dont know what is the <package>?

or your mean when i download any package, i should install the dependency in this way?
Well, if you're installing source code that isn't in the repositories, you can't get the dependancies this way.

To get the dependancies of some code you have, first try running 'make'. If it can't compile, you'll probably get an error like: **Cannot find file xxxxx.h** (not sure of the actual text, but it's similar. It will mention a file name). Once you have the file name, go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/), under 'Search the contents of packages'. Put the file name in the box, and click 'Search'. For example, I was trying to compile a game, but it said that the file **SDL.h** wasn't found. Now, using the Ubuntu package search, I can see that the file is in the libsdl1.2-dev package. Simply install that package using Synaptic, and then try running 'make' again.

Note that if you read the README file, it will usually tell you what it needs. Since you're installing the program from source, you'll need the development (...-dev) package, rather than the compiled package. For example, if the script needs a library called 'foobar', you'll need to get the 'foobar-dev' package (note that this is just an example, there's no real foobar packge :P)

Also, 'make install' usually needs to be run as root, as it puts files into the /usr/local/bin directory. Once the make is successful, run it like:
```
sudo make install
```.

Finally, it's best to keep all your source code in /usr/local/src.

Hope this helps,
 --Daniel15

---

### Post by Rohbart on 2008-07-10
I tried it with heroes of might and magic V. But it says unable to find source package for Heroes. What can I do?

---

