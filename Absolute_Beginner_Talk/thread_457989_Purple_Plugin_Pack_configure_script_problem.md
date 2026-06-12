---
title: "Purple Plugin Pack configure script problem"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-05-29
This is the output of running the configure script
```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
./configure: eval: line 2376: syntax error near unexpected token `('
./configure: eval: line 2376: `${SHELL} /home/allan/Desktop/purple-plugin_pack-1.0 (2)/missing --run true'
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
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
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... no
checking whether no accepts -g... no
checking dependency style of no... none
checking whether we are using the GNU Fortran 77 compiler... no
checking whether no accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  en_AU es_ES
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PURPLE... yes
checking for PIDGIN... no
checking for FINCH... no
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.0.0... yes (version 2.12.11)
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error:
*** GTK+ 2.0 is required to build purple-plugin_pack; please make sure you have the
*** GTK+ development headers installed. The latest version of GTK+ is always
*** available at http://www.gtk.org/.

```

What do I install now?

---

### Post by nylecoj813 on 2007-05-29
I was compiling Pidgin from source yesterday and had similar problems. I think libgtk2.0-dev is the package you need. Maybe double check you have lib-gtk2.0 too? They're both in synaptic. Be warned I'm still new to this stuff and could be wrong...but those errors you're getting look familiar.

Let me know if that helps!

---

### Post by wersdaluv on 2007-05-29
Thanks. I already had libgtk2.0 and I just installed the libgtk2.0-dev and it surely helped but...

Here is the output of the configure script
```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
./configure: eval: line 2376: syntax error near unexpected token `('
./configure: eval: line 2376: `${SHELL} /home/allan/Desktop/purple-plugin_pack-1.0 (3)/missing --run true'
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
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
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... no
checking whether no accepts -g... no
checking dependency style of no... none
checking whether we are using the GNU Fortran 77 compiler... no
checking whether no accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  en_AU es_ES
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PURPLE... yes
checking for PIDGIN... yes
checking for FINCH... no
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.0.0... yes (version 2.12.11)
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... yes (version 2.10.11)
checking talkfilters.h usability... no
checking talkfilters.h presence... no
checking for talkfilters.h... no
configure: WARNING:
*** GNU Talk Filters is required to build the talkfilters plugin;
*** please make sure you have the GNU Talk Filters development headers installed.
*** The latest version of GNU Talk Filters is available at
*** http://www.hyperrealm.com/talkfilters/talkfilters.html.
checking for GTKSPELL... no
checking for xmms-config... no
checking regex.h usability... yes
checking regex.h presence... yes
checking for regex.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating common/Makefile
config.status: creating doc/Makefile
config.status: creating m4/Makefile
config.status: creating po/Makefile.in
config.status: creating VERSION
config.status: creating plugin_pack.spec
config.status: creating album/Makefile
config.status: creating autorejoin/Makefile
config.status: creating autoreply/Makefile
config.status: creating awaynotify/Makefile
config.status: creating bash/Makefile
config.status: creating bit/Makefile
config.status: creating blistops/Makefile
config.status: creating broadcast/Makefile
config.status: creating buddytime/Makefile
config.status: creating chronic/Makefile
config.status: creating dice/Makefile
config.status: creating difftopic/Makefile
config.status: creating eight_ball/Makefile
config.status: creating flip/Makefile
config.status: creating groupmsg/Makefile
config.status: creating gRIM/Makefile
config.status: creating hideconv/Makefile
config.status: creating ignorance/Makefile
config.status: creating irchelper/Makefile
config.status: creating irssi/Makefile
config.status: creating lastseen/Makefile
config.status: creating listhandler/Makefile
config.status: creating mystatusbox/Makefile
config.status: creating napster/Makefile
config.status: creating nicksaid/Makefile
config.status: creating oldlogger/Makefile
config.status: creating plonkers/Makefile
config.status: creating schedule/Makefile
config.status: creating sepandtab/Makefile
config.status: creating showoffline/Makefile
config.status: creating simfix/Makefile
config.status: creating slashexec/Makefile
config.status: creating sslinfo/Makefile
config.status: creating stocker/Makefile
config.status: creating switchspell/Makefile
config.status: creating talkfilters/Makefile
config.status: creating xchat-chats/Makefile
config.status: creating xmmsremote/Makefile
config.status: creating xmmsremote/pixmaps/Makefile
config.status: creating pre_config.h
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

purple-plugin_pack 1.0 Configuration complete

Debugging enabled................: no

Build purple plugins.............: yes
Installing purple plugins to.....: /usr/lib/purple-2
Installing purple plugin data to.: /usr/share
Purple plugins to be built.......:
         autoreply bash dice eight_ball
         flip irchelper listhandler oldlogger
         showoffline simfix slashexec sslinfo

Build pidgin plugins.............: yes
Installing pidgin plugins to.....: /usr/lib/pidgin
Installing pidgin plugin data to.: /usr/share
Pidgin plugins to be built.......:
         album blistops difftopic gRIM
         hideconv irssi lastseen mystatusbox
         nicksaid plonkers schedule sepandtab
         talkfilters xchat-chats xmmsremote

Build finch plugins..............: no

Type make to compile

```
It looks good but...

Here is last part of the result of make
```
make[2]: Leaving directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)/xchat-chats'
Making all in xmmsremote
make[2]: Entering directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)/xmmsremote'
Making all in pixmaps
make[3]: Entering directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)/xmmsremote/pixmaps'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)/xmmsremote/pixmaps'
make[3]: Entering directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)/xmmsremote'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)/xmmsremote'
make[2]: Leaving directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)/xmmsremote'
make[2]: Entering directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)'
make[1]: Leaving directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)'

```

Here is the result of sudo make install
```
make  install-recursive
make[1]: Entering directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)'
Making install in common
make[2]: Entering directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)/common'
make[3]: Entering directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)/common'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)/common'
make[2]: Leaving directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)/common'
Making install in doc
make[2]: Entering directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)/doc'
make[3]: Entering directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)/doc'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)/doc'
make[2]: Leaving directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)/doc'
Making install in m4
make[2]: Entering directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)/m4'
make[3]: Entering directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)/m4'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)/m4'
make[2]: Leaving directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)/m4'
Making install in po
make[2]: Entering directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)/po'
/home/allan/Desktop/purple-plugin_pack-1.0 (3)/install-sh -d /usr/share/locale
/bin/sh: Syntax error: word unexpected (expecting ")")
make[2]: *** [install-data-yes] Error 2
make[2]: Leaving directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)/po'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/user/Desktop/purple-plugin_pack-1.0 (3)'
make: *** [install] Error 2

```

What do I do now?

---

### Post by wersdaluv on 2007-05-29
I managed to install it by installing the deb from getdeb.net!

You know what I have learned? Every time we are to install something, we should look first in Synaptic or Add/Remove, then in getdeb.net, then Google for debs. If all else fail, that is the only time we try compiling tarballs. LOL

---

### Post by foresth on 2007-06-13
> **wersdaluv said:**
> I managed to install it by installing the deb from getdeb.net!

You know what I have learned? Every time we are to install something, we should look first in Synaptic or Add/Remove, then in getdeb.net, then Google for debs. If all else fail, that is the only time we try compiling tarballs. LOL

Hi,
could you be more specific? Which deb?

Thanks..

---

### Post by nylecoj813 on 2007-06-13
It doesn't seem to be on getdeb.net. Try here: [http://download.ubuntu.pl/_Feisty_Fawn/pidgin/2.0.0/](http://download.ubuntu.pl/_Feisty_Fawn/pidgin/2.0.0/) 

It's under 2.0.0 but I don't see why it wouldn't work with 2.0.1

---

### Post by daynah on 2007-06-15
daynah@wubuntu:~$ sudo dpkg -i purple-plugin-pack_1.0-1_i386.deb
Selecting previously deselected package purple-plugin-pack.
(Reading database ... 187982 files and directories currently installed.)
Unpacking purple-plugin-pack (from purple-plugin-pack_1.0-1_i386.deb) ...
dpkg: dependency problems prevent configuration of purple-plugin-pack:
 purple-plugin-pack depends on pidgin (>= 2.0.0); however:
  Package pidgin is not installed.
dpkg: error processing purple-plugin-pack (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 purple-plugin-pack


I have pidgin 2.0.1 installed though. HMMM... suggestions? It's a bit late to think about this, I'll come back and work on it tomorrow.

---

