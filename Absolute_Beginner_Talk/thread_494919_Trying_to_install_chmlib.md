---
title: "Trying to install chmlib"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by trunks14 on 2007-07-07
I'm trying to find a way to read CHM files, yes, i do know this topic *is covered* but i just can't find to understand how to install libraries and that stuff (makefile.am, makefile.in? AHHHHH).

Well, the first thing i tried was the simpliest:

sudo apt-get install gnochm

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnochm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gnochm has no installation candidate
```

then i tried to install it manually, but  then you got all these dependencies....PyCHM, CHMLIB, well the first thing to instally is chmlib but guess what, i don't know how to do this i don't really understand all that make stuff ¬¬

Now, the CHMlib documentation says this:

> The simplest way to compile this package is:

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

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.

For a start the configure command says:

```
configure: error: C compiler cannot create executables

```

WHY NOT? aren't unix-based systems supposed to be able to compile anything C out of the box?

i wanna cry :(

hope you can help me, I have this Java book in CHM which i really want to read, not relaying on Microsoft

---

### Post by deepclutch on 2007-07-07
I think you need to read [http://ubuntuguide.org](http://ubuntuguide.org)
and reg reading chm files in Linux,
try: apt-get install gnochm  
or
apt-get install xchm

for softwares in Debian based distros,u dont need to search softwares in internet.just use menu System>admin>synaptic manager.
and i hope u know the basics of Linux and local user is not permitted to modify(RWX) only root can do.
I feel u google for a good Ubuntu feisty new users guide.
next pls note that Linux/UNIX dont want anitvirus,antispywares etc etc.
and regarding ur tries with source compiling:
Dont try those source given from digit.its just illogical for eg;how it'll be if u get those .dll files,diffrnt config things etc wholesale to ur hand **instead** of installshield setup or simply "setup.exe"-the same thing in linux/unix are those gzipped(.gz) or bzipped(.bz2) source files;for eg:ur xmms source!.
So the thing is there are very good package managers which can fetch you and install software without searching internet like in windows.for eg: Debian or Ubuntu have apt and dpkg doing a wonderful job.for redhat/fedora .rpm is there,yum is there etc.
So never try those outdated source and if possible any source packages,get ur package manager works for you! [IMG]http://www.thinkdigit.com/forum/images/smilies/icon_smile.gif[/IMG]
for eg:in GNOME menu after Applications and Places,there is another menu called System which contains administration menu>in which there is synaptic manager.give ur local user password when prompted.
Do read below article very informative for Windows Users too: 
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by kosmic on 2007-07-07
Why are you trying to compile a program when you have the Fantastic Debian World under your finger ??

Go to "synaptic" then choose "Configurations" and then "Repositories" and check all of them "main, Universe, Multiverse"

Then "Reload" synaptic and search for "gnochm" and it should appear, Install and voila.


Now your next question :

Ubuntu by default dont install compilers and is libraries, if you need them just do :

sudo apt-get install build-essential

---

### Post by trunks14 on 2007-07-07
i knew it had to do with where synaptic borrows information about packages, thank you very much.

but for the sake of knowledge, is knowing about make useful or important for nonprogrammers?

---

### Post by deepclutch on 2007-07-07
after a deal of time.can try source compile with distros like LFS help u.even if u love more Source compile try BLFS.yes source compile is useful if optimized for ur pc arch.

---

