---
title: "i just don't get this"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-01-28
ok, so i'm trying to install this graphical version of links - [http://links.twibright.com/](http://links.twibright.com/)
i've got it downloaded and untarred and i ran ./configure (after figuring out i was doing something really stupid with it - see other stupid thread) and i got all this crap...

[i]Usage: configure [options] [host]
Options: [defaults in brackets after descriptions]
Configuration:
  --cache-file=FILE       cache test results in FILE
  --help                  print this message
  --no-create             do not create output files
  --quiet, --silent       do not print `checking...' messages
  --version               print the version of autoconf that created configure
Directory and file names:
  --prefix=PREFIX         install architecture-independent files in PREFIX
                          [/usr/local]
  --exec-prefix=EPREFIX   install architecture-dependent files in EPREFIX
                          [same as prefix]
  --bindir=DIR            user executables in DIR [EPREFIX/bin]
  --sbindir=DIR           system admin executables in DIR [EPREFIX/sbin]
  --libexecdir=DIR        program executables in DIR [EPREFIX/libexec]
  --datadir=DIR           read-only architecture-independent data in DIR
                          [PREFIX/share]
  --sysconfdir=DIR        read-only single-machine data in DIR [PREFIX/etc]
  --sharedstatedir=DIR    modifiable architecture-independent data in DIR
                          [PREFIX/com]
  --localstatedir=DIR     modifiable single-machine data in DIR [PREFIX/var]
  --libdir=DIR            object code libraries in DIR [EPREFIX/lib]
  --includedir=DIR        C header files in DIR [PREFIX/include]
  --oldincludedir=DIR     C header files for non-gcc in DIR [/usr/include]
  --infodir=DIR           info documentation in DIR [PREFIX/info]
  --mandir=DIR            man documentation in DIR [PREFIX/man]
  --srcdir=DIR            find the sources in DIR [configure dir or ..]
  --program-prefix=PREFIX prepend PREFIX to installed program names
  --program-suffix=SUFFIX append SUFFIX to installed program names
  --program-transform-name=PROGRAM
                          run sed PROGRAM on installed program names
Host type:
  --build=BUILD           configure for building on BUILD [BUILD=HOST]
  --host=HOST             configure for HOST [guessed]
  --target=TARGET         configure for TARGET [TARGET=HOST]
Features and packages:
  --disable-FEATURE       do not include FEATURE (same as --enable-FEATURE=no)
  --enable-FEATURE[=ARG]  include FEATURE [ARG=yes]
  --with-PACKAGE[=ARG]    use PACKAGE [ARG=yes]
  --without-PACKAGE       do not use PACKAGE (same as --with-PACKAGE=no)
  --x-includes=DIR        X include files are in DIR
  --x-libraries=DIR       X library files are in DIR
--enable and --with options recognized:
  --enable-debuglevel     set internal checking level
        -1 - recover from segmentation faults
         0 - no checks (fastest)
         1 - check memory leaks
         2 - leaks with file/line accuracy, memory red zone, pattern filling
  --enable-javascript     use javascript interpreter
  --with-libfl            use libfl
  --enable-graphics       use graphics
  --without-gpm           compile without gpm mouse
  --with-ssl(=directory)  enable SSL support
  --without-svgalib       compile without svgalib graphics driver
  --without-x             compile without X Window System graphics driver
  --without-fb            compile without Linux Framebuffer graphics driver
  --without-directfb      compile without DirectFB graphics driver
  --without-sdl           compile without SDL graphics driver
  --without-pmshell       compile without PMShell graphics driver
  --without-atheos        compile without Atheos graphics driver
  --with-x                use the X Window System
  --without-libjpeg       compile without JPEG support
  --without-libtiff       compile without TIFF support[/i]

i know i'm supposed to configure options, but i have no idea how to proceed. i'm looking for the simplest way possible, but with the option to edit the configuration later (if that can be simple, as well). i'd like as many features enabled as possible.

i was dropped on my head, as an infant, and have had trouble with this sort of thing ever since.

---

### Post by tageiru on 2006-01-28
There is really no need to compile it yourself. The links2 package in Ubuntu starts in graphical mode if you pass it the -g parameter.

---

### Post by fuscia on 2006-01-28
[QUOTE=tageiru]There is really no need to compile it yourself. The links2 package in Ubuntu starts in graphical mode if you pass it the -g parameter.[/QUOTE]

if i 'pass it'? i'm sorry, i don't know what you mean by that.

---

### Post by tageiru on 2006-01-28
[QUOTE=fuscia]if i 'pass it'? i'm sorry, i don't know what you mean by that.[/QUOTE]
The links2 application takes a number of arguments. Open up a terminal and write "man links2" to get a list of them. The -g flag tells the application to not run in terminal mode, but through a graphical interface.

---

### Post by fuscia on 2006-01-28
[QUOTE=tageiru]The links2 application takes a number of arguments. Open up a terminal and write "man links2" to get a list of them. The -g flag tells the application to not run in terminal mode, but through a graphical interface.[/QUOTE]

i entered "links2 -g" and ended up with a text based version of links. the one i was trying to install looks like this...

[img]http://links.twibright.com/shots/shot2.png[/img]

it appears to be something different. even if it's the same, i'd still like to know how to do this right. thanks for the help.

---

### Post by cwaldbieser on 2006-01-28
[QUOTE=fuscia]i entered "links2 -g" and ended up with a text based version of links. the one i was trying to install looks like this...

[img]http://links.twibright.com/shots/shot2.png[/img]

it appears to be something different. even if it's the same, i'd still like to know how to do this right. thanks for the help.[/QUOTE]
At the terminal try:
```

$ links2 -version
Links 2.1pre16

```
This is the version I have (from the repositories), and when I launch "links2 -g" I definitely get the graphical mode instead of the text mode.

The man pages say it is not supposed to go to text mode if it can't figure out your video card, but maybe that is what you are experiencing anyway?

---

### Post by fuscia on 2006-01-28
okay, you guys, i just realized that i am capable of being more of a retard than i ever thought possible. thank you for your help and your patience. i'm all set.

---

