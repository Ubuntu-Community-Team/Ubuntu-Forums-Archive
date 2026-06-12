---
title: "problems installing with configure files"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by ralph4100 on 2005-11-16
Every time I try to configure or compile I get errors like this one...

```
root@ubuntu:/opt/cftp-0.12# ./configure
creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH
root@ubuntu:/opt/cftp-0.12#
```

sometimes I get "no c compiler in $PATH" instead of no acceptable cc....

---

### Post by Kyral on 2005-11-16
```
sudo apt-get install build-essential
```

I know I misspelled that....

---

### Post by ralph4100 on 2005-11-16
after I installed build essential, I tried my configure file again:

```
root@ubuntu:/opt/cftp-0.12# ./configure
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking whether the C compiler (gcc -g ) works... yes
checking whether the C compiler (gcc -g ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for tgetent... no
checking for tgetent in -ltermcap... no
checking for tgetent in -lcurses... no
checking for tgetent in -lncurses... no
configure: error: can't find termcap (emulation) library
root@ubuntu:/opt/cftp-0.12#

```

---

### Post by ralph4100 on 2005-11-16
I tried another and got this (after installing build essential):

```
checking for GLIB - version >= 1.2.3... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: gFTP needs GLIB 1.2.3 or higher
root@ubuntu:/opt/gftp-2.0.18#
```

---

### Post by kruz on 2005-11-16
i would most def go with

sudo apt-get install GLIB 
sudo apt-get install gcc  
sudo apt-get install make

---

### Post by Kyral on 2005-11-16
Make and GCC are installed with Build-Essential

So should glib. But

```
sudo apt-get install libglib2.0-dev
``` should fix it

---

### Post by ralph4100 on 2005-11-17
```
root@ubuntu:/opt/glib-2.8.0# sudo apt-get install libglib2.0-dev
Reading package lists... Done
Building dependency tree... Done
Package libglib2.0-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libglib2.0-dev has no installation candidate
root@ubuntu:/opt/glib-2.8.0#
```

I did the above after installing glib 2.8.0 (I thought).

I downloaded the glib source, and tried to install, and it needed gettext.

I downloaded gettext, and installed it into /opt because that's where lampp was installed so I thought /opt was an install folder or something. I did ./configure in the gettext file, then make, then make install, and everything went smoothly.

Then I installed glib and it worked. Then I tried to install gftp again, to no avail! because it still needed glib! did I install in the wrong folder or do I need to run glib or what?

---

### Post by ralph4100 on 2005-11-17
Also, this is my error when I try to install cftp (not gftp):

```
root@ubuntu:/opt/cftp-0.12# ./configure
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking whether the C compiler (gcc -g ) works... yes
checking whether the C compiler (gcc -g ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for tgetent... no
checking for tgetent in -ltermcap... no
checking for tgetent in -lcurses... no
checking for tgetent in -lncurses... no
configure: error: can't find termcap (emulation) library
root@ubuntu:/opt/cftp-0.12#

```

---

### Post by ralph4100 on 2005-11-17
btw, could someone tell me the following things:

(1) what is apt-get?
(2) if I use a process of ./configure followed by make followed by make install, what am I doing?
(3) after I install, how do I run?
(4) do I need to restart after installing?

---

### Post by odin on 2005-11-17
[QUOTE=ralph4100]btw, could someone tell me the following things:

(1) what is apt-get?
(2) if I use a process of ./configure followed by make followed by make install, what am I doing?
(3) after I install, how do I run?
(4) do I need to restart after installing?[/QUOTE]


(1) apt is a tool ubuntu has for software management.It would be like synaptic but in command line(actually I think synaptic uses apt for downloading and installing,synaptic would be like an interface easier to use)

(2)./configure=you are getting the information about your system "make" will need to compile the source(assuming you have what that program needs,otherwise you will get errors but I can see you already know that)

make= compiling the source

make install= installing the program in your system

In less words,you get the source code compile it and install it.

(3) well I dont know exactly what you mean but that depends on what you are installing.

(4) I really love to answer this question: NOOOO!!! That's one of the reasons I love Ubuntu and linux in general(by restart I guess you mean reboot your computer)


Probably some of the definitions I gave you are not really accurate but If I havent wasted my time the 6 months I'm using ubuntu that should give you an idea.

hope it helps

---

### Post by IndigoMontoya on 2006-06-02
for those of you with a similar problem, I fixed this by installing the ncurses development (sudo apt-get install  libncurses5-dev)

---

