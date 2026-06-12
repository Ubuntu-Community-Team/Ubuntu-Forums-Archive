---
title: "i don't get how to install this app"
date: 2005-08-26
forum: Absolute Beginner Talk
---

### Post by z3r0-c0d3r on 2005-08-26
I found a application to connect my phone to linux but i don't understand how to install from the source.
here's the link to the program
[http://www.icewalkers.com/download/tsemgr/1805/dld/](http://www.icewalkers.com/download/tsemgr/1805/dld/)
does anyone know how to this? or where to find a debian package?

---

### Post by vruum on 2005-08-26
the generic way to install from source is, in a terminal, to change into the directory you've extrected the files to, and type:

./configure
make
sudo make install

./configure will more than likely fail with an error message that something could not be found, try installing that something from synaptic. and start again. also, it looks like development of the package stopped last year, so it might require some libs that are outdated or uninstallable. or it might just work.

---

### Post by Lord Illidan on 2005-08-26
If it doesn't work, give us the output, not whine because it doesn't work, because you willnot get any help that way!

---

### Post by z3r0-c0d3r on 2005-08-26
when i type "./configure" i get this:
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking for gtk-config... no
configure: error: gtk-config not found. Gtk is required for tsemgr
```

then when i type "make" I get this:
```
make: *** No targets specified and no makefile found.  Stop.
```

and when i type "make install" i get this:
```
make: *** No rule to make target `install'.  Stop.
```

---

### Post by az on 2005-08-26
"gtk-config not found. Gtk is required for tsemgr"


You need the -dev files for gtk1.2.  Look in synaptic.  You will probably also need to install the xlibs-dev packages, too.

Whatever the last line of the ./configure script complains about, you need to install.  -dev packages are the developmental headers that you need to install when you want to compile an application to use those librabies.

This is a gtk1 application and not a gtk2 application.  Install the -dev packages for gtk1 (look at the version numbers of the package if you are in doubt)

---

