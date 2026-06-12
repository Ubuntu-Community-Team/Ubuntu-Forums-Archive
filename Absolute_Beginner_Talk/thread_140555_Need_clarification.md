---
title: "Need clarification"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by chameleon on 2006-03-06
Hi,
I wonder if someone could clarify something for me. I'm trying to install a piece of software called OpenMusic, which requires gtk2 to work. I'm not sure if this is already on Breezy Badger. I couldn't find it on Synaptic, but I did find libgtk2. Is this the same thing? I take it that the 'lib' part is just short for 'library'. Gtk also has certain dependencies, one of which is glib, but I couldn't find that on Synaptic. The full set of packages I need is -

gtk,
atk
glib
pango
cairo
jpegsrc
libpng
pkg-config
tiff

What I have is -

libgtk
libatk
libpango
libcairo
libjgep
libpng
pkg-config
libtiff

Are these packages the same, or will I have to install all the stuff myself? Sorry if this seems a stupid question, but I'm (surprise surprise) a bit of a beginner, particularly when it comes to configuring/installing new software.

Many thanks

---

### Post by christhemonkey on 2006-03-06
They should be the correct packages yes.  Though glib is libglib.

---

### Post by chameleon on 2006-03-06
Chris,
Thanks, just as I suspected. And of course libglib is there, don't know why I didn't see it before.

---

### Post by az on 2006-03-06
You need the "-dev" package to compile something for a library.

For example, look for libgtk2-dev if your source application says you need the gtk2 libraries to compile the program.

---

### Post by chameleon on 2006-03-06
Yes, I've made sure I've got all the dev packages installed (through Synaptic). Where would be the best place to put gtk canvas? I find that this is my biggest worry when installing - putting things in the right place (though I think I read somewhere that in most cases it doesn't actually matter).

Also, it says on the GTK site that 'the GNU libiconv library is needed to build Glib if your system doesn't have the iconv() function for doing conversion between character encodings'. Can't find iconv or libiconv on Synaptic, though. I presume if Ubuntu already has libglib it doesn't matter?

---

### Post by chameleon on 2006-03-07
I tried to configure gtkcanvas, but got this at the end -

```
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gtk-config... no
checking for GTK - version >= 1.2.0... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: GTK not installed

```

I've picked up a bit of knowledge about environment variables by googling, but I still don't really know what to do. I typed 'locate libgtk' and found the following at the bottom -

```
/usr/lib/libgtkspell.so.0.0.0
/usr/lib/libgtkspell.so.0
/usr/lib/libgtksourceview-1.0.so.0
/usr/lib/libgtksourceview-1.0.so.0.0.0
/usr/lib/libgtkhtml-2.so.0.0.0
/usr/lib/libgtkhtml-2.so.0

```

I'd untarred gtk canvas to /usr/bin (actually the directory is called omlinux-gtkcanvas-4.7.1.beta, it's one of the OpenMusic packages). I then added /usr/lib to PATH in omlinux-gtkcanvas-4.7.1.beta - same error during configure. I then added libgtk-x11-2.0.so.0 - same result again. I wish I understood what I was doing wrong, because I bet it's really simple, and I'll probably kick myself when one of you guys tells me!

---

### Post by az on 2006-03-07
Why are you untarring things?  Just use the packages!

Also, it seems you app needs gtk 1


dora@dora:~$ apt-cache search gtk1
libglib1.2 - The GLib library of C routines
libgtk1.2 - The GIMP Toolkit set of widgets for X
libgtk1.2-common - Common files for the GTK+ library
libgtk1.2-dbg - Debugging files for the GIMP Toolkit
libgtk1.2-dev - Development files for the GIMP Toolkit
gtk-engines-geramik - Geramik GTK1.x Theme
gtk-engines-qtpixmap - QtPixmap GTK1.x theming engine
gtk-engines-thingeramik - ThinGeramik GTK1.x Theme
gtk2-engines-qtpixmap - QtPixmap GTK2.x theming engine
libgtk1.2-doc - Documentation for the GIMP Toolkit
dora@dora:~$

Install libgtk1.2 and libgtk1.2-dev

You may need some packages like this, too:

libgnomemm-dev - C++ wrapper for GNOME 1 (development files)
libgnomemm1.2-9 - C++ wrapper for GNOME 1 (shared library)

libgtk-canvas1 - port of GNOME Canvas back to gtk+
libgtk-canvas1-dev - port of GNOME Canvas back to gtk+ -- development files

libgdk-pixbuf-gnome-dev - The GNOME1 GdkPixBuf library - development files

---

### Post by chameleon on 2006-03-07
Yes, it worked when I installed gtk1 from Synaptic. But now I've got a different problem - I tried to configure clg, the gtk bindings for CMUCL (Common Lisp), but it couldn't find lisp. I'd put lisp into a directory called CMUCL_DIR. This is what I got at the end of the configure code -

```
root@ubuntu: omlinux-clg-0.54# ./configure --with-lisp
=CMUCL_DIR/bin/lisp --with-lisp-arguments=-nositeinit
(lots of code deleted)
checking for lisp .../bin/lisp
checking whether we can start lisp... TMP_VALUE=
yes
checking whether lisp is CMUCL... no
configure: error: CMUCL is required to compile clg
```

As you can see, there was an option which needed to be passed to /.configure in order to find CMUCL, but for some reason it's not working. I'd put both CMUCL_DIR and omlinux-clg-0.54 into /home. Is this possibly a problem with environment variables?

---

### Post by chameleon on 2006-03-07
I moved CMUCL_DIR to /usr/local/bin, then configured with an extra option ```
root@ubuntu:/omlinux-clg-0.54# ./configure --with-lisp=/usr/local/bin/CMUCL_DIR/bin/lisp --with-lisp-header -- with-lisp-arguments=-nositeinit (lots of code deleted) checking whether we can start lisp... TMP_VALUE= yes checking whether lisp is CMUCL... yes checking for CMUCL library directory... /usr/local/bin/CMUCL_DIR/bin/./. checking for yes... no configure: error: yes: File not found. you can use the --with-lisp-header configure options
``` All that I had done was install autoconf on Synaptic. But something's still not right, obviouisly.

Just tried it all again with -

./configure --with-lisp=/usr/local/bin/CMUCL_DIR/bin/lisp --with-lisp-header=/usr/local/bin/CMUCL_DIR/include/lisp --with-lisp-arguments=-nositeinit

It found everything. But now it says -

checking whether lisp is CMUCL... yes
checking for CMUCL library directory... /usr/local/bin/CMUCL_DIR/bin/./.
checking for /usr/local/bin/CMUCL_DIR/include/lisp.h... yes
checking whether calling lisp code from C works... configure: error: Could not compile file to test dynamic loading

This is so frustrating; I don't understand why I keep getting problems at every turn.

---

### Post by kelcey_s on 2008-06-17
I agree at things not working at every turn, I have given up trying to get this to work. Its a shame because it looked really good.

---

