---
title: "PKG_CONFIG_PATH error"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by matteospqr on 2007-06-09
I am trying to install Compiz-settigns on my computer and the only way is from source because the .deb file online is only for i386 users.  When I download the source file and make it run I get this message:


checking for PACKAGE... configure: error: Package requirements (dbus-1 compiz >= 0.3.3 dbus-glib-1 gconf-2.0 gtk+-2.0 >= 2.0.0) were not met:

No package 'dbus-1' found
No package 'compiz' found
No package 'dbus-glib-1' found
No package 'gconf-2.0' found
No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


I checked with synaptic and I have those packages installed.  I don't know how to go around this problem by doing what they say at the bottom of the error message.

Any suggestions??

thanks

---

### Post by tbroderick on 2007-06-09
You need the corresponding -dev packages.

libdbus-1-dev
libdbus-glib-1-dev
compiz-dev
libgconf2-dev
libgtk2.0-dev

---

### Post by matteospqr on 2007-06-09
I have them installed thats the thing. I checked on synaptic.  I think its something to do with this:

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I am clueless!

:(

---

### Post by tbroderick on 2007-06-09
You have pkg-config installed? And can you post more of your ./configure output.

---

### Post by matteospqr on 2007-06-09
Ok here is the whole output message I get.
By the way instead of doing ./configure I do ./autogen.sh --prefix=/usr which is what they tell you to do on the compiz-settings install page.  I tried anyways doing ./configure and I still am getting the same message:



matteo@matteo:~/Desktop/compizsettings-trunk$ ./autogen.sh --prefix=/usr
processing .
Creating ./aclocal.m4 ...
Running glib-gettextize...  Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/local/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

Making ./aclocal.m4 writable ...
Running aclocal  ...
Running autoheader...
Running automake --gnu  ...
Running autoconf ...
Running ./configure --enable-maintainer-mode --prefix=/usr ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/local/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... configure: error: Package requirements (dbus-1 compiz >= 0.3.3 dbus-glib-1 gconf-2.0 gtk+-2.0 >= 2.0.0) were not met:

No package 'dbus-1' found
No package 'compiz' found
No package 'dbus-glib-1' found
No package 'gconf-2.0' found
No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

matteo@matteo:~/Desktop/compizsettings-trunk$ 



Thank you so much for your help!

---

### Post by Bachstelze on 2007-06-09
```
sudp apt-get install pkg-config libdbus-1-dev compiz-dev libdbus-glib-1-dev libgconf2-dev libgtk2.0-dev
```

---

### Post by matteospqr on 2007-06-09
I did that even though I had the files already installed.  I am thinking that this could help:


Please add the files
codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
progtest.m4
from the /usr/local/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).


Its at the top of the error message.  The problem is that I dont know where the autoconf macro directory is!!

---

### Post by Patrick Biggs on 2007-07-19
I had the same problem in Anjuta trying to program a libglade setup.

Why does autoconfugure complain that no package 'gtk2.0' found when what it really wants is
libgtk2.0-dev.  I've just wasted 2 hours installing gtk, pango, cairo and atk to no avail
when all I needed to do was ...

sudo apt-get install libgtk2.0-dev

My fault, I should have looked in this forum first.

Anyway I am now working.

Love Ubuntu, rapidly going off Microsoft.

---

