---
title: "Compiling rtorrent - What am I doing wrong?"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by 449 on 2008-01-05
I'm running Ubuntu 7.10. Here's my terminal: 

```
erik@erik-desktop:~$ cd Desktop
erik@erik-desktop:~/Desktop$ tar -xvzf rtorrent-0.7.9.tar.gz 
rtorrent-0.7.9/
rtorrent-0.7.9/aclocal.m4
rtorrent-0.7.9/AUTHORS
rtorrent-0.7.9/autogen.sh
rtorrent-0.7.9/ChangeLog
rtorrent-0.7.9/config.guess
rtorrent-0.7.9/config.h.in
rtorrent-0.7.9/config.sub
rtorrent-0.7.9/configure
rtorrent-0.7.9/configure.ac
rtorrent-0.7.9/COPYING
rtorrent-0.7.9/depcomp
rtorrent-0.7.9/doc/
rtorrent-0.7.9/doc/faq.xml
rtorrent-0.7.9/doc/Makefile.am
rtorrent-0.7.9/doc/Makefile.in
rtorrent-0.7.9/doc/rtorrent.1
rtorrent-0.7.9/doc/rtorrent.1.xml
rtorrent-0.7.9/doc/rtorrent.rc
rtorrent-0.7.9/INSTALL
rtorrent-0.7.9/install-sh
rtorrent-0.7.9/ltmain.sh
rtorrent-0.7.9/Makefile.am
rtorrent-0.7.9/Makefile.in
rtorrent-0.7.9/missing
rtorrent-0.7.9/mkinstalldirs
rtorrent-0.7.9/NEWS
rtorrent-0.7.9/rak/
rtorrent-0.7.9/rak/address_info.h
rtorrent-0.7.9/rak/algorithm.h
rtorrent-0.7.9/rak/error_number.h
rtorrent-0.7.9/rak/file_stat.h
rtorrent-0.7.9/rak/fs_stat.h
rtorrent-0.7.9/rak/functional.h
rtorrent-0.7.9/rak/functional_fun.h
rtorrent-0.7.9/rak/partial_queue.h
rtorrent-0.7.9/rak/path.h
rtorrent-0.7.9/rak/priority_queue.h
rtorrent-0.7.9/rak/priority_queue_default.h
rtorrent-0.7.9/rak/ranges.h
rtorrent-0.7.9/rak/regex.h
rtorrent-0.7.9/rak/socket_address.h
rtorrent-0.7.9/rak/string_manip.h
rtorrent-0.7.9/rak/timer.h
rtorrent-0.7.9/rak/unordered_vector.h
rtorrent-0.7.9/README
rtorrent-0.7.9/scripts/
rtorrent-0.7.9/scripts/attributes.m4
rtorrent-0.7.9/scripts/checks.m4
rtorrent-0.7.9/scripts/common.m4
rtorrent-0.7.9/src/
rtorrent-0.7.9/src/command_download.cc
rtorrent-0.7.9/src/command_events.cc
rtorrent-0.7.9/src/command_file.cc
rtorrent-0.7.9/src/command_helpers.cc
rtorrent-0.7.9/src/command_helpers.h
rtorrent-0.7.9/src/command_local.cc
rtorrent-0.7.9/src/command_network.cc
rtorrent-0.7.9/src/command_peer.cc
rtorrent-0.7.9/src/command_tracker.cc
rtorrent-0.7.9/src/command_ui.cc
rtorrent-0.7.9/src/control.cc
rtorrent-0.7.9/src/control.h
rtorrent-0.7.9/src/core/
rtorrent-0.7.9/src/core/curl_get.cc
rtorrent-0.7.9/src/core/curl_get.h
rtorrent-0.7.9/src/core/curl_stack.cc
rtorrent-0.7.9/src/core/curl_stack.h
rtorrent-0.7.9/src/core/download.cc
rtorrent-0.7.9/src/core/download.h
rtorrent-0.7.9/src/core/download_factory.cc
rtorrent-0.7.9/src/core/download_factory.h
rtorrent-0.7.9/src/core/download_list.cc
rtorrent-0.7.9/src/core/download_list.h
rtorrent-0.7.9/src/core/download_slot_map.h
rtorrent-0.7.9/src/core/download_store.cc
rtorrent-0.7.9/src/core/download_store.h
rtorrent-0.7.9/src/core/http_queue.cc
rtorrent-0.7.9/src/core/http_queue.h
rtorrent-0.7.9/src/core/log.cc
rtorrent-0.7.9/src/core/log.h
rtorrent-0.7.9/src/core/Makefile.am
rtorrent-0.7.9/src/core/Makefile.in
rtorrent-0.7.9/src/core/manager.cc
rtorrent-0.7.9/src/core/manager.h
rtorrent-0.7.9/src/core/poll_manager.cc
rtorrent-0.7.9/src/core/poll_manager.h
rtorrent-0.7.9/src/core/poll_manager_epoll.cc
rtorrent-0.7.9/src/core/poll_manager_epoll.h
rtorrent-0.7.9/src/core/poll_manager_kqueue.cc
rtorrent-0.7.9/src/core/poll_manager_kqueue.h
rtorrent-0.7.9/src/core/poll_manager_select.cc
rtorrent-0.7.9/src/core/poll_manager_select.h
rtorrent-0.7.9/src/core/scheduler.cc
rtorrent-0.7.9/src/core/scheduler.h
rtorrent-0.7.9/src/core/view.cc
rtorrent-0.7.9/src/core/view.h
rtorrent-0.7.9/src/core/view_manager.cc
rtorrent-0.7.9/src/core/view_manager.h
rtorrent-0.7.9/src/display/
rtorrent-0.7.9/src/display/attributes.h
rtorrent-0.7.9/src/display/canvas.cc
rtorrent-0.7.9/src/display/canvas.h
rtorrent-0.7.9/src/display/frame.cc
rtorrent-0.7.9/src/display/frame.h
rtorrent-0.7.9/src/display/Makefile.am
rtorrent-0.7.9/src/display/Makefile.in
rtorrent-0.7.9/src/display/manager.cc
rtorrent-0.7.9/src/display/manager.h
rtorrent-0.7.9/src/display/text_element.h
rtorrent-0.7.9/src/display/text_element_list.cc
rtorrent-0.7.9/src/display/text_element_list.h
rtorrent-0.7.9/src/display/text_element_string.cc
rtorrent-0.7.9/src/display/text_element_string.h
rtorrent-0.7.9/src/display/text_element_value.cc
rtorrent-0.7.9/src/display/text_element_value.h
rtorrent-0.7.9/src/display/utils.cc
rtorrent-0.7.9/src/display/utils.h
rtorrent-0.7.9/src/display/window.cc
rtorrent-0.7.9/src/display/window.h
rtorrent-0.7.9/src/display/window_download_chunks_seen.cc
rtorrent-0.7.9/src/display/window_download_chunks_seen.h
rtorrent-0.7.9/src/display/window_download_list.cc
rtorrent-0.7.9/src/display/window_download_list.h
rtorrent-0.7.9/src/display/window_download_statusbar.cc
rtorrent-0.7.9/src/display/window_download_statusbar.h
rtorrent-0.7.9/src/display/window_download_transfer_list.cc
rtorrent-0.7.9/src/display/window_download_transfer_list.h
rtorrent-0.7.9/src/display/window_file_list.cc
rtorrent-0.7.9/src/display/window_file_list.h
rtorrent-0.7.9/src/display/window_http_queue.cc
rtorrent-0.7.9/src/display/window_http_queue.h
rtorrent-0.7.9/src/display/window_input.cc
rtorrent-0.7.9/src/display/window_input.h
rtorrent-0.7.9/src/display/window_log.cc
rtorrent-0.7.9/src/display/window_log.h
rtorrent-0.7.9/src/display/window_log_complete.cc
rtorrent-0.7.9/src/display/window_log_complete.h
rtorrent-0.7.9/src/display/window_peer_list.cc
rtorrent-0.7.9/src/display/window_peer_list.h
rtorrent-0.7.9/src/display/window_statusbar.cc
rtorrent-0.7.9/src/display/window_statusbar.h
rtorrent-0.7.9/src/display/window_string_list.cc
rtorrent-0.7.9/src/display/window_string_list.h
rtorrent-0.7.9/src/display/window_text.cc
rtorrent-0.7.9/src/display/window_text.h
rtorrent-0.7.9/src/display/window_title.cc
rtorrent-0.7.9/src/display/window_title.h
rtorrent-0.7.9/src/display/window_tracker_list.cc
rtorrent-0.7.9/src/display/window_tracker_list.h
rtorrent-0.7.9/src/globals.cc
rtorrent-0.7.9/src/globals.h
rtorrent-0.7.9/src/input/
rtorrent-0.7.9/src/input/bindings.cc
rtorrent-0.7.9/src/input/bindings.h
rtorrent-0.7.9/src/input/input_event.cc
rtorrent-0.7.9/src/input/input_event.h
rtorrent-0.7.9/src/input/Makefile.am
rtorrent-0.7.9/src/input/Makefile.in
rtorrent-0.7.9/src/input/manager.cc
rtorrent-0.7.9/src/input/manager.h
rtorrent-0.7.9/src/input/path_input.cc
rtorrent-0.7.9/src/input/path_input.h
rtorrent-0.7.9/src/input/text_input.cc
rtorrent-0.7.9/src/input/text_input.h
rtorrent-0.7.9/src/main.cc
rtorrent-0.7.9/src/Makefile.am
rtorrent-0.7.9/src/Makefile.in
rtorrent-0.7.9/src/option_parser.cc
rtorrent-0.7.9/src/option_parser.h
rtorrent-0.7.9/src/rpc/
rtorrent-0.7.9/src/rpc/command.h
rtorrent-0.7.9/src/rpc/command_map.cc
rtorrent-0.7.9/src/rpc/command_map.h
rtorrent-0.7.9/src/rpc/command_scheduler.cc
rtorrent-0.7.9/src/rpc/command_scheduler.h
rtorrent-0.7.9/src/rpc/command_scheduler_item.cc
rtorrent-0.7.9/src/rpc/command_scheduler_item.h
rtorrent-0.7.9/src/rpc/command_slot.cc
rtorrent-0.7.9/src/rpc/command_slot.h
rtorrent-0.7.9/src/rpc/command_variable.cc
rtorrent-0.7.9/src/rpc/command_variable.h
rtorrent-0.7.9/src/rpc/exec_file.cc
rtorrent-0.7.9/src/rpc/exec_file.h
rtorrent-0.7.9/src/rpc/Makefile.am
rtorrent-0.7.9/src/rpc/Makefile.in
rtorrent-0.7.9/src/rpc/parse.cc
rtorrent-0.7.9/src/rpc/parse.h
rtorrent-0.7.9/src/rpc/parse_commands.cc
rtorrent-0.7.9/src/rpc/parse_commands.h
rtorrent-0.7.9/src/rpc/scgi.cc
rtorrent-0.7.9/src/rpc/scgi.h
rtorrent-0.7.9/src/rpc/scgi_task.cc
rtorrent-0.7.9/src/rpc/scgi_task.h
rtorrent-0.7.9/src/rpc/xmlrpc.cc
rtorrent-0.7.9/src/rpc/xmlrpc.h
rtorrent-0.7.9/src/signal_handler.cc
rtorrent-0.7.9/src/signal_handler.h
rtorrent-0.7.9/src/ui/
rtorrent-0.7.9/src/ui/download.cc
rtorrent-0.7.9/src/ui/download.h
rtorrent-0.7.9/src/ui/download_list.cc
rtorrent-0.7.9/src/ui/download_list.h
rtorrent-0.7.9/src/ui/element_base.h
rtorrent-0.7.9/src/ui/element_chunks_seen.cc
rtorrent-0.7.9/src/ui/element_chunks_seen.h
rtorrent-0.7.9/src/ui/element_download_list.cc
rtorrent-0.7.9/src/ui/element_download_list.h
rtorrent-0.7.9/src/ui/element_file_list.cc
rtorrent-0.7.9/src/ui/element_file_list.h
rtorrent-0.7.9/src/ui/element_log_complete.cc
rtorrent-0.7.9/src/ui/element_log_complete.h
rtorrent-0.7.9/src/ui/element_menu.cc
rtorrent-0.7.9/src/ui/element_menu.h
rtorrent-0.7.9/src/ui/element_peer_list.cc
rtorrent-0.7.9/src/ui/element_peer_list.h
rtorrent-0.7.9/src/ui/element_string_list.cc
rtorrent-0.7.9/src/ui/element_string_list.h
rtorrent-0.7.9/src/ui/element_text.cc
rtorrent-0.7.9/src/ui/element_text.h
rtorrent-0.7.9/src/ui/element_tracker_list.cc
rtorrent-0.7.9/src/ui/element_tracker_list.h
rtorrent-0.7.9/src/ui/element_transfer_list.cc
rtorrent-0.7.9/src/ui/element_transfer_list.h
rtorrent-0.7.9/src/ui/Makefile.am
rtorrent-0.7.9/src/ui/Makefile.in
rtorrent-0.7.9/src/ui/root.cc
rtorrent-0.7.9/src/ui/root.h
rtorrent-0.7.9/src/utils/
rtorrent-0.7.9/src/utils/directory.cc
rtorrent-0.7.9/src/utils/directory.h
rtorrent-0.7.9/src/utils/list_focus.h
rtorrent-0.7.9/src/utils/lockfile.cc
rtorrent-0.7.9/src/utils/lockfile.h
rtorrent-0.7.9/src/utils/Makefile.am
rtorrent-0.7.9/src/utils/Makefile.in
rtorrent-0.7.9/src/utils/socket_fd.cc
rtorrent-0.7.9/src/utils/socket_fd.h
rtorrent-0.7.9/TODO
erik@erik-desktop:~/Desktop$ cd rtorrent-0.7.9/
erik@erik-desktop:~/Desktop/rtorrent-0.7.9$ ls
aclocal.m4    config.h.in   depcomp     Makefile.am    rak
AUTHORS       config.sub    doc         Makefile.in    README
autogen.sh    configure     INSTALL     missing        scripts
ChangeLog     configure.ac  install-sh  mkinstalldirs  src
config.guess  COPYING       ltmain.sh   NEWS           TODO
erik@erik-desktop:~/Desktop/rtorrent-0.7.9$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for user-defined CXXFLAGS... default "-O2 -Wall"
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
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
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
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
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking for execinfo.h... no
checking for proper overloaded template function disambiguation... yes
checking for library containing add_wch... no
checking for library containing wbkgdset... no
*** The ncurses library is required!
erik@erik-desktop:~/Desktop/rtorrent-0.7.9$ make
make: *** No targets specified and no makefile found.  Stop.
erik@erik-desktop:~/Desktop/rtorrent-0.7.9$ make install
make: *** No rule to make target `install'.  Stop.
erik@erik-desktop:~/Desktop/rtorrent-0.7.9$ 

```

---

### Post by ~LoKe on 2008-01-05
```
sudo apt-get install libncurses5-dev
```
Try that, then run ./configure again.

---

### Post by 449 on 2008-01-05
```
erik@erik-desktop:~/Desktop/rtorrent-0.7.9$ sudo apt-get install libncurses5-dev
[sudo] password for erik:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libncurses5-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1456kB of archives.
After unpacking 6283kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com gutsy/main libncurses5-dev 5.6+20070716-1ubuntu3 [1456kB]
Fetched 1456kB in 3s (414kB/s)            
Selecting previously deselected package libncurses5-dev.
(Reading database ... 108282 files and directories currently installed.)
Unpacking libncurses5-dev (from .../libncurses5-dev_5.6+20070716-1ubuntu3_i386.deb) ...
Setting up libncurses5-dev (5.6+20070716-1ubuntu3) ...
erik@erik-desktop:~/Desktop/rtorrent-0.7.9$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for user-defined CXXFLAGS... default "-O2 -Wall"
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
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
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
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
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking for execinfo.h... no
checking for proper overloaded template function disambiguation... yes
checking for library containing add_wch... no
checking for library containing wbkgdset... -lncurses
checking sys/vfs.h usability... yes
checking sys/vfs.h presence... yes
checking for sys/vfs.h... yes
checking sys/statvfs.h usability... yes
checking sys/statvfs.h presence... yes
checking for sys/statvfs.h... yes
checking sys/statfs.h usability... yes
checking sys/statfs.h presence... yes
checking for sys/statfs.h... yes
checking for statvfs... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for STUFF... configure: error: Package requirements (sigc++-2.0 libcurl >= 7.12.0 libtorrent >= 0.11.8) were not met:

No package 'sigc++-2.0' found
No package 'libcurl' found
No package 'libtorrent' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables STUFF_CFLAGS
and STUFF_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by Deadmode on 2008-01-05
wow that's weird I just downloaded it to see if I could install it and nearly the same thing happened.  All my problems occured at the end of the ./configure check.  "*** The ncurses library is required!"  Is it dependencey problems?  

I use Ktorrent and I like it.

---

### Post by 449 on 2008-01-05
> **Deadmode said:**
> wow that's weird I just downloaded it to see if I could install it and nearly the same thing happened.  All my problems occured at the end of the ./configure check.  "*** The ncurses library is required!"  Is it dependencey problems?  

I use Ktorrent and I like it.

At least it's not just me. This is my first time trying to compile. :)

Although it does seem a whole lot easier than I expected.

---

### Post by ~LoKe on 2008-01-05
See this?  It tells you what you're missing:
> No package 'sigc++-2.0' found
No package 'libcurl' found
No package 'libtorrent' found
So...
> sudo apt-cache search sigc|grep dev
libsigc++-2.0-dev - type-safe Signal Framework for C++ - development files
libsigc++-1.2-dev - type-safe Signal Framework for C++ - development files
libsigc++-dev - Type-safe Signal Framework for C++ - development files
libsigcperl-dev - Helper library for the libsigc++ Perl bindings - development files
libsigcx-0.6-dev - libSigCX (libSigC++ Extras) - development
libsigcx-gtk-0.6-dev - libSigCX (libSigC++ Extras) GTK+ dispatcher - development
>  sudo apt-cache search libcurl|grep dev
libcurl4-gnutls-dev - Development files and documentation for libcurl (GnuTLS)
libcurl4-openssl-dev - Development files and documentation for libcurl (OpenSSL)
libcurl-ocaml-dev - ocaml libcurl bindings
libghttp-dev - original GNOME HTTP client library - development kit
liblua5.1-curl-dev - libcURL development files for the lua language version 5.1
libwww-dev - The W3C WWW library - development files
libwww-ssl-dev - The W3C WWW library - development files (SSL support)
> sudo apt-cache search libtorrent|grep dev
libtorrent-dev - a C++ BitTorrent library (development files)

So...
```
sudo apt-get install libsigc++-2.0-dev libtorrent-dev
```
Libcurl I'm not sure about, but try this:
```
sudo apt-get install libcurl4-openssl-dev
```

---

### Post by 449 on 2008-01-05
```
Requested 'libtorrent >= 0.11.8' but version of libtorrent is 0.11.4

```

How do I update?

---

### Post by mali2297 on 2008-01-05
> **449 said:**
> ```
Requested 'libtorrent >= 0.11.8' but version of libtorrent is 0.11.4

```

How do I update?

Compile the latest version from [here]("http://libtorrent.rakshasa.no/").

---

### Post by ~LoKe on 2008-01-05
How about just trying...
```
sudo apt-get install libtorrent10
```

But I'm curious...why are you trying to compile rTorrent?  It's in the repos.
```
sudo apt-get install rtorrent
```

---

### Post by 449 on 2008-01-05
> **~LoKe said:**
> How about just trying...
```
sudo apt-get install libtorrent10
```

But I'm curious...why are you trying to compile rTorrent?  It's in the repos.
```
sudo apt-get install rtorrent
```

Haha, well if I knew that...

But it's still good practice. :KS

---

### Post by 449 on 2008-01-05
Ok, I tried both of those and still no luck. When I try typing "rtorrent" in terminal I get this:

```
  *** rTorrent 0.7.4 - libTorrent 0.11.4 ***
[View: main]



















(15:32:41) Using 'epoll' based polling.
(15:32:41) Could not read resource file: ~/.rtorrent.rc
[Throttle off/off KB] [Rate   0.0/  0.0 KB] [Port: 6980] [U 0/0] [D 0/0] [H 0/3


```

---

### Post by ~LoKe on 2008-01-05
rTorrent is a CLI torrent application.  That's exactly what it's supposed to look like.

Press **Enter** to find your torrent.  

It'll say...
**Load>**
Write the entire path to your torrent, like so:
**Load>/home/username/Torrents/movie.torrent**

[This should help you](http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide).

---

