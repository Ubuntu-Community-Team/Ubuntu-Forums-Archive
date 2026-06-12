---
title: "install prob w/ scratchpad 3.0: no glib-2?"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by takayuki on 2006-10-08
Hi,

I'm trying to install a text editor called Scratchpad.  There isn't a deb that I'm aware of so I d/l'd the tarball, unpacked it and did a ./configure, and I got the usual packages not found message. 

It needs glib-2.0, but I can't find it in the repository.  I've got libglib2.0...  

Any thoughts greatly appreciated!






bubox@bubox:~/Desktop/scratchpad-0.3.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking for valac... valac
checking for gconftool-2... /usr/bin/gconftool-2
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for SCRATCHPAD... configure: error: Package requirements (
        glib-2.0 >= 2.12.0
        gtk+-2.0 >= 2.10.0
        gtksourceview-1.0 >= 1.8.0
        gconf-2.0 >= 2.14.0
        gnome-vfs-2.0 >= 2.16.0
) were not met:

No package 'glib-2.0' found
No package 'gtk+-2.0' found
No package 'gtksourceview-1.0' found
No package 'gconf-2.0' found
No package 'gnome-vfs-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables SCRATCHPAD_CFLAGS
and SCRATCHPAD_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

