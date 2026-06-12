---
title: "so ive killed my apt-get"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by Mrwasab1 on 2007-03-23
well i have been playing around with apt-get trying to install dosbox so i could play some old school games...

lets just say i got as far as downloading dosbox and no further

ill give you a bit of history, i was going through the step by step instructions on how to install dos box and it says to do a ./configure then make etc..

however ./configure was returning an error as seen below 

```
mrwasabi@penguin101:~/downloads/dosbox-0.70$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version 1.2.0 not found!

```

thats where it started going wrong. i went in search of some SDL package, from the many thousand and i couldnt figure out what to do.

i played around with my depositories and now when i attempt to do sudo apt-get update i get the following

```
mrwasabi@penguin101:~/downloads/dosbox-0.70$ sudo apt-get update
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)

```

i have gone to this website [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
and rebuilt my source.list, however i still get that same error message

Here is a copy of my current source.list

```
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://au.archive.ubuntu.com/ubuntu edgy main restricted 
deb http://au.archive.ubuntu.com/ubuntu edgy-updates main restricted
deb http://security.ubuntu.com/ubuntu edgy-security main restricted

deb-src http://au.archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://au.archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://au.archive.ubuntu.com/ubuntu edgy universe multiverse 
deb http://au.archive.ubuntu.com/ubuntu edgy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse

deb-src http://au.archive.ubuntu.com/ubuntu edgy universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu edgy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security universe multiverse

# Upstream Wine
# GPG key: 387EE263
deb http://wine.budgetdedicated.com/apt edgy main 

deb-src http://wine.budgetdedicated.com/apt edgy main

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb http://medibuntu.sos-sts.com/repo/ edgy free non-free 

deb-src http://medibuntu.sos-sts.com/repo/ edgy free non-free

```


ive spent 3 hours on this already, i am at my wits end and all i want to do is play an old school dos game...

can someone please help me kill 2 birds with one stone and explain what i do to install dosbox and secondly but more importantly tell me what i am doing wrong with the depositories...

thanks

---

### Post by taurus on 2007-03-23
Open a terminal and edit your /etc/apt/sources.list.d/edgy-universe.list

```
gksudo gedit **/etc/apt/sources.list.d/edgy-universe.list**
```
and place a # in front of second line in there to command it out.  Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Mrwasab1 on 2007-03-23
ahhh /etc/apt/source.list.d

why didnt i see that before!?!?!?! :mad: 

thanks so much!! :) 
and thanks for the speedy reply!

by any chance you would know how to solve the dos box issue?

---

### Post by taurus on 2007-03-23
I think you need the libsdl-dev package.  Open synaptic and search for libsdl then.

---

### Post by Mrwasab1 on 2007-03-23
excellent! all working perfectly now.. where were you 3 hours ago :p
thanks again:KS

---

### Post by taurus on 2007-03-23
> **Mrwasab1 said:**
> where were you 3 hours ago :p
thanks again:KS

Probably eating dinner.  ;)

---

