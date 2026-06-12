---
title: "compiling"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by M3lted on 2006-01-11
hi guys
Im still fairly new to linux and im trying to compile a program.
iv never done this before and i could use some help.
here's the deal.
when i do ./configure this is the outcome
```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... none
checking dependency style of gcc... none
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... yes
checking for LIBXML2... yes
checking for LIBXSLT... yes
checking for OPENSSL... yes
checking for libcurl... libcurl gevonden in /usr/lib.
checking for curl.h... curl.h gevonden in /usr/include/curl.
checking for libpcre... libpcre gevonden in /usr/lib.
checking for pcre.h... pcre.h gevonden in /usr/include.
checking for GTK... yes
checking for libgtkembedmoz... libgtkembedmoz gevonden in /usr/lib/mozilla.
checking for gtkmozembed.h... gtkmozembed.h gevonden in /usr/include/mozilla/gtkembedmoz.
checking if Mozilla has GTK2 support... yes
checking if we need to build the GUI frontend... yes, using Mozilla as HTML rendering engine
checking if we need to build the console frontend... yes
checking if the HTTP auth plugin ./ftd_http_plugin.linux64.so.2.0 works... no
checking if the HTTP auth plugin ./ftd_http_plugin.linux32.so.2.0 works... yes
checking if your compiler has 'stack-smash-protector' support... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating ftd_core/Makefile
config.status: creating ftd_core/data/Makefile
config.status: creating ftd_core/include/Makefile
config.status: creating ftd_core/src/Makefile
config.status: creating gui_errhandler/Makefile
config.status: creating gui_errhandler/include/Makefile
config.status: creating gui_errhandler/src/Makefile
config.status: creating gui_config/Makefile
config.status: creating gui_config/include/Makefile
config.status: creating gui_config/src/Makefile
config.status: creating console/Makefile
config.status: creating console/include/Makefile
config.status: creating console/src/Makefile
config.status: creating gui/Makefile
config.status: creating gui/include/Makefile
config.status: creating gui/include/images/Makefile
config.status: creating gui/src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

```
now when i do make nothing happens
so someone told me i neeed to use a flag's
something like this.
example.

./configure --with-mozilla-libraries=/opt/mozilla/lib --with-mozilla-headers=/opt/mozilla/include

but this should lead to the path where my files are located
but the thing is ,i cant find it and im kinda stuck here

any 1 understand what i mean , and who can help me out here lol 
im getting kinda frustrated :(

---

### Post by nkhansen on 2006-01-11
When you say that 'nothing' happens, what excactly happens? is it like:

$ make
$ 

or more something like
$make
:ERROR: Polaron flow has been inverted :ERROR:

$

---

### Post by Sef on 2006-01-11
Before you started compiling, did you install build essentials?  It is necessary if you want to compile.

command: sudo apt-get build-essential

---

### Post by M3lted on 2006-01-11
[QUOTE=nkhansen]When you say that 'nothing' happens, what excactly happens? is it like:

$ make
$ 

or more something like
$make
:ERROR: Polaron flow has been inverted :ERROR:

$[/QUOTE]

Its more like this :)

```

name@name:~/Desktop/ftd-1.0.alpha3$ make
bash: make: command not found
name@name:~/Desktop/ftd-1.0.alpha3$

```

:)

---

### Post by ubuntumaneh on 2006-01-11
So, you need Sef's solution:

sudo apt-get install build-essentials

---

### Post by M3lted on 2006-01-11
[QUOTE=Sef]Before you started compiling, did you install build essentials?  It is necessary if you want to compile.

command: sudo apt-get build-essentials[/QUOTE]

LOL
That Was it what i needed :)

thx very much haha

btw it was apt-get install build-essential  ;)

---

### Post by Sef on 2006-01-11
:oops: ty for the correction.  I fixed it.

---

### Post by M3lted on 2006-01-11
ah well doesnt matter i'm happy enough i got my program working :)
that program was the only reason i sticked with xp lol so i can dump xp now :D

---

