---
title: "GLIB error with GNUCash?"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2007-03-03
Hello,

I've been trying to install gnucash 2.0.5 (now using this guide: [http://www.linuxmint.com/forum/viewtopic.php?t=1283)](http://www.linuxmint.com/forum/viewtopic.php?t=1283)). I get upto ./configure where I end with an error saying this: 

checking for GLIB - version >= 2.4.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error:
*** GLIB >= 2.4 is required to build Gnucash; please make sure you have the
*** development headers installed. The latest version of GLIB is
*** always available at [ftp://ftp.gnome.org/pub/gnome/sources/glib/](ftp://ftp.gnome.org/pub/gnome/sources/glib/).

I've been playing around and installing and uninstalling glib, but i don't think that's the actual problem. I don't have a clue how to go further. This has actually been the deepest I've ever been "into" linux (command line and stuff..)

Any help..?

---

### Post by OzDad on 2007-04-30
Ellooo,
I got my 'no compiler' error fixed,
I got my 'cannot find ltdl.h' problem sorted,
I now also have this same problem with glib.
Exact same message as above.
Any help would also be appreciated.
Thanks, OzDad
[www.waroonaambulance.com.au](www.waroonaambulance.com.au)

---

### Post by OzDad on 2007-04-30
Ellooo,
I managed to find glib-2.4.0.tar.gz at the following address,
[http://ftp.acc.umu.se/pub/GNOME/sources/glib/2.4/](http://ftp.acc.umu.se/pub/GNOME/sources/glib/2.4/)

It failed the ./configure as it needed gettext.

I managed to find gettext at the following address,
[http://ftp.gnu.org/pub/gnu/gettext/gettext-0.14.5.tar.gz](http://ftp.gnu.org/pub/gnu/gettext/gettext-0.14.5.tar.gz)

This I was able to download, unpack, configure and make.

Still cannot configure the glib as it comes up with,
configure error:
*** you must have either have gettext support in you C library, or use the
***GNU gettext library. ([http://www.gnu.org/software/gettext/gettext.html](http://www.gnu.org/software/gettext/gettext.html))

Is this not what I just did?

---

