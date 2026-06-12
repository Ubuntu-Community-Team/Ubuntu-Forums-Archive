---
title: "Error compiling gnomebaker-0.6.2"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by chips.4.u on 2007-10-12
1st things, ubuntu/linux total newbie. converting from ms.

From the Install text inside the archive I typed this into the terminal:
[indent]xxxxxx@xxxxxx:~/Desktop/gnomebaker-0.6.2$ ./configure; make; make install[/indent]
and this was my output:
[indent]checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.[/indent]

If you need to see the 'config.log' will post. or any other details. thanks

c

---

### Post by chips.4.u on 2007-10-12
ok after reading this thread:
[http://ubuntuforums.org/showthread.php?t=323939](http://ubuntuforums.org/showthread.php?t=323939)
I Installed the 'build-essential' package and everything attached to it.
then did this again:
[indent]./configure; make; make install[/indent]
here is the output:
[indent]
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for GNOMEBAKER... configure: error: Package requirements (
        libgnomeui-2.0 >= 2.8.1
        gtk+-2.0 >= 2.6.0
        glib-2.0 >= 2.4.0
        libglade-2.0 >= 2.4.2
        libxml-2.0 >= 2.4.0
) were not met:

No package 'libgnomeui-2.0' found
No package 'gtk+-2.0' found
No package 'glib-2.0' found
No package 'libglade-2.0' found
No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOMEBAKER_CFLAGS
and GNOMEBAKER_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
[/indent]

anyone inform me how to proceed?

c

---

### Post by annda on 2007-10-12
welcome!

before you install the missing dependencies (libgnomeui, libglade etc. listed in the error message), is there any important reason why the easy install method is not working? i mean Applications>Add/remove or Synaptic (system>administration>synaptic)? you may not need to compile from source...

in case you need them, here are two guides to installing software in ubuntu:
[forum sticky]("http://ubuntuforums.org/showthread.php?t=500020")
[monkeyblog]("http://monkeyblog.org/ubuntu/installing/")

---

