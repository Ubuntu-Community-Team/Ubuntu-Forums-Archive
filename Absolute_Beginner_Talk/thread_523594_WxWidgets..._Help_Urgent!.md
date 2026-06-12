---
title: "WxWidgets... Help Urgent!"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Dark Star on 2007-08-12
I was install Simdock :) but while configuring I got this error 

```
shashwat@shashwat-desktop:~$ cd /home/shashwat/simdock/
shashwat@shashwat-desktop:~/simdock$ ./configure
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... yes
checking for ranlib... ranlib
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking dependency style of g++... gcc3
checking for wx-config... no
configure: error:
                wxWidgets must be installed on your system.

                Please check that wx-config is in path, the directory
                where wxWidgets libraries are installed (returned by
                'wx-config --libs' or 'wx-config --static --libs' command)
                is in LD_LIBRARY_PATH or equivalent variable and
                wxWidgets version is 2.8.0 or above.

shashwat@shashwat-desktop:~/simdock$ 
```

Plz tell me how to install wxwidgets :( :confused:

---

### Post by Warren Watts on 2007-08-12
Install it from the repositories using apt-get
```
sudo apt-get install libwxgtk2.8-dev
```

---

### Post by Dark Star on 2007-08-12
```
shashwat@shashwat-desktop:~$ cd /home/shashwat/simdock
shashwat@shashwat-desktop:~/simdock$ ./configure
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... yes
checking for ranlib... ranlib
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking dependency style of g++... gcc3
checking for wx-config... /usr/bin/wx-config
checking for wxWindows version >= 2.8.0... 
  Warning: No config found to match: /usr/bin/wx-config --static --libs
           in /usr/lib/wx/config
  If you require this configuration, please install the desired
  library build.  If this is part of an automated configuration
  test and no other errors occur, you may safely ignore it.
  You may use wx-config --list to see all configs available in
  the default prefix.

yes (version 2.8.1)
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for pid_t... yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for dup2... yes
checking for sqrt... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
shashwat@shashwat-desktop:~/simdock$ make
cd . && /bin/bash /home/shashwat/simdock/missing --run aclocal-1.9 
/home/shashwat/simdock/missing: line 52: aclocal-1.9: command not found
WARNING: `aclocal-1.9' is missing on your system.  You should only need it if
         you modified `acinclude.m4' or `configure.in'.  You might want
         to install the `Automake' and `Perl' packages.  Grab them from
         any GNU archive site.
 cd . && /bin/bash /home/shashwat/simdock/missing --run automake-1.9 --gnu 
/home/shashwat/simdock/missing: line 52: automake-1.9: command not found
WARNING: `automake-1.9' is missing on your system.  You should only need it if
         you modified `Makefile.am', `acinclude.m4' or `configure.in'.
         You might want to install the `Automake' and `Perl' packages.
         Grab them from any GNU archive site.
cd . && /bin/bash /home/shashwat/simdock/missing --run autoconf
/home/shashwat/simdock/missing: line 52: autoconf: command not found
WARNING: `autoconf' is missing on your system.  You should only need it if
         you modified `configure.in'.  You might want to install the
         `Autoconf' and `GNU m4' packages.  Grab them from any GNU
         archive site.
/bin/bash ./config.status --recheck
running CONFIG_SHELL=/bin/bash /bin/bash ./configure   --no-create --no-recursion
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... yes
checking for ranlib... ranlib
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking dependency style of g++... gcc3
checking for wx-config... /usr/bin/wx-config
checking for wxWindows version >= 2.8.0... 
  Warning: No config found to match: /usr/bin/wx-config --static --libs
           in /usr/lib/wx/config
  If you require this configuration, please install the desired
  library build.  If this is part of an automated configuration
  test and no other errors occur, you may safely ignore it.
  You may use wx-config --list to see all configs available in
  the default prefix.

yes (version 2.8.1)
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for pid_t... yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for dup2... yes
checking for sqrt... yes
configure: creating ./config.status
 /bin/bash ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
cd . && /bin/bash /home/shashwat/simdock/missing --run autoheader
/home/shashwat/simdock/missing: line 52: autoheader: command not found
WARNING: `autoheader' is missing on your system.  You should only need it if
         you modified `acconfig.h' or `configure.in'.  You might want
         to install the `Autoconf' and `GNU m4' packages.  Grab them
         from any GNU archive site.
rm -f stamp-h1
touch config.h.in
make  all-am
make[1]: Entering directory `/home/shashwat/simdock'
if g++ -DHAVE_CONFIG_H -I. -I. -I.   -I/usr/lib/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__  -g -O2  -MT getBg.o -MD -MP -MF ".deps/getBg.Tpo" -c -o getBg.o `test -f 'src/getBg.cc' || echo './'`src/getBg.cc; \
        then mv -f ".deps/getBg.Tpo" ".deps/getBg.Po"; else rm -f ".deps/getBg.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I.   -I/usr/lib/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__  -g -O2  -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o `test -f 'src/main.cc' || echo './'`src/main.cc; \
        then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
src/main.cc: In member function ‘void MyFrame::OnPaint(wxPaintEvent&)’:
src/main.cc:894: warning: taking address of temporary
src/main.cc:917: warning: taking address of temporary
if g++ -DHAVE_CONFIG_H -I. -I. -I.   -I/usr/lib/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__  -g -O2  -MT simImage.o -MD -MP -MF ".deps/simImage.Tpo" -c -o simImage.o `test -f 'src/simImage.cc' || echo './'`src/simImage.cc; \
        then mv -f ".deps/simImage.Tpo" ".deps/simImage.Po"; else rm -f ".deps/simImage.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I.   -I/usr/lib/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__  -g -O2  -MT main_arguments.o -MD -MP -MF ".deps/main_arguments.Tpo" -c -o main_arguments.o `test -f 'src/main_arguments.cc' || echo './'`src/main_arguments.cc; \
        then mv -f ".deps/main_arguments.Tpo" ".deps/main_arguments.Po"; else rm -f ".deps/main_arguments.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I.   -I/usr/lib/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__  -g -O2  -MT main_settings.o -MD -MP -MF ".deps/main_settings.Tpo" -c -o main_settings.o `test -f 'src/main_settings.cc' || echo './'`src/main_settings.cc; \
        then mv -f ".deps/main_settings.Tpo" ".deps/main_settings.Po"; else rm -f ".deps/main_settings.Tpo"; exit 1; fi
g++  -g -O2    -o simbar  getBg.o main.o simImage.o main_arguments.o main_settings.o  -pthread   -lwx_gtk2u_aui-2.8 -lwx_gtk2u_xrc-2.8 -lwx_gtk2u_qa-2.8 -lwx_gtk2u_html-2.8 -lwx_gtk2u_adv-2.8 -lwx_gtk2u_core-2.8 -lwx_baseu_xml-2.8 -lwx_baseu_net-2.8 -lwx_baseu-2.8 
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make[1]: Leaving directory `/home/shashwat/simdock'
shashwat@shashwat-desktop:~/simdock$ sudo make install
Password:
make[1]: Entering directory `/home/shashwat/simdock'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'simbar' '/usr/local/bin/simbar'
test -z "/usr/share/SimBar" || mkdir -p -- "/usr/share/SimBar"
 /usr/bin/install -c -m 644 'src/bg.png' '/usr/share/SimBar/bg.png'
 /usr/bin/install -c -m 644 'src/bg2.png' '/usr/share/SimBar/bg2.png'
make[1]: Leaving directory `/home/shashwat/simdock'
shashwat@shashwat-desktop:~/simdock$ 
```

Hey now I think Install is done .. I can't see its icon anywhere how to open it ;):guitar:

---

### Post by Dark Star on 2007-08-12
Plz help me .. I know install docks but due to low system I can't run Berly :( therefore this 1 runs without berly ;)

---

### Post by DarthPooky on 2007-12-01
press alt + f1 than type simdock and press enter

---

