---
title: "Help compiling Gazebo from source"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2007-06-24
Hi,
Gazebo is a 3d robot simulation software that I require for my research. The installation instructions and general information about it can be found here:
[http://playerstage.sourceforge.net/doc/Gazebo-manual-0.5-html/install.html](http://playerstage.sourceforge.net/doc/Gazebo-manual-0.5-html/install.html)

I am trying to install it. I did a ./configure after downloading the tarball and here is what  I got:
sudarshan@Lucky-Linux:~/gazebo-0.7.0$ auto-apt run ./configure
Entering auto-apt mode: ./configure
Exit the command to leave auto-apt mode.
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C preprocessor... gcc -E
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for correct ltmain.sh version... yes
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for a BSD-compatible install... /usr/bin/install -c
checking for stdint.h... (cached) yes
checking for scandir... yes
checking for poll... yes
checking for dirname... yes
checking for alphasort... yes
checking for strndup... yes
checking for dlopen in -ldl... yes
checking checking for union semun... no
checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
checking GL/glu.h usability... yes
checking GL/glu.h presence... yes
checking for GL/glu.h... yes
checking GL/glut.h usability... no
checking GL/glut.h presence... no
checking for GL/glut.h... no
configure: error: Could not find (one of) gl.h glu.h glut.h; OpenGL is required to build Gazebo.

I see that it needs a bunch of header files but dont know how to get them. I need help installing this thing on my machine.

Thanks

---

### Post by Kubunteando on 2007-06-24
You will need to install some new packages.
The MESA packages contain the libraries for OpenGL.

Start by installing:
- mesa-common-dev
- libglu1-mesa-dev

They are in the normal repositories, so you can use just Adept Manager, as for any other software.

---

### Post by linuxnovice on 2007-06-24
Hi,
I checked and found that both are already installed.
sudarshan@Lucky-Linux:~$ sudo apt-get install mesa-common-dev
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
mesa-common-dev is already the newest version.
mesa-common-dev set to manual installed.
The following packages were automatically installed and are no longer required:
  liblaunchpad-integration0 libchewing3-data libgail18 libglitz-glx1 libdc1394-13 python-notify libwmf0.2-7 feisty-wallpapers
  libgnomeui-common libgail-common cdrecord anthy libots0 libwxgtk2.6-0 libgfortran1 human-cursors-theme ttf-dustin libtagc0
  libaiksaurusgtk-1.2-0c2a libbonoboui2-common libbonoboui2-0 metacity-common libpostproc0d libxml-twig-perl kdeedu-data gdebi-core
  libgnome-menu2 libdvbpsi4 gcc-3.4-base libavformat0d system-tools-backends libcdio6 libxosd2 libpanel-applet2-0 libpoppler1-glib
  python-gtkhtml2 libchewing3 libgutenprintui2-1 libvlc0 human-theme libnet-dbus-perl libwpd-stream8c2a libavc1394-0 libgdome2-0
  libwxbase2.6-0 libnm-glib0 python-vte libvte9 libgnomeui-0 libcroco3 libglitz1 human-icon-theme libhdf5-serial-1.6.5-0 libgtkhtml2-0
  libgsm1 libdvdnav4 libiso9660-4 libgnome-window-settings1 libmetacity0 python-launchpad-integration atlas3-base feisty-session-splashes
  libgimp2.0 libgdome2-cpp-smart0c2a python-gdbm libanthy0 librsvg2-2 libxklavier11 libavcodec0d liboobs-1-3 libkdeedu3 xaw3dg
  libgtkmathview0c2a libtar libgtkspell0 libg2c0 mkisofs binfmt-support libberyldecoration0 gnome-mount libvcdinfo0 libvte-common
  libgnome-desktop-2 librsvg2-common libgnomeprintui2.2-0 x-dev libgnomeprintui2.2-common libmpeg2-4 app-install-data-commercial
  liba52-0.7.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sudarshan@Lucky-Linux:~$ sudo apt-get install libglu1-mesa-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
libglu1-mesa-dev is already the newest version.
libglu1-mesa-dev set to manual installed.
The following packages were automatically installed and are no longer required:
  liblaunchpad-integration0 libchewing3-data libgail18 libglitz-glx1 libdc1394-13 python-notify libwmf0.2-7 feisty-wallpapers
  libgnomeui-common libgail-common cdrecord anthy libots0 libwxgtk2.6-0 libgfortran1 human-cursors-theme ttf-dustin libtagc0
  libaiksaurusgtk-1.2-0c2a libbonoboui2-common libbonoboui2-0 metacity-common libpostproc0d libxml-twig-perl kdeedu-data gdebi-core
  libgnome-menu2 libdvbpsi4 gcc-3.4-base libavformat0d system-tools-backends libcdio6 libxosd2 libpanel-applet2-0 libpoppler1-glib
  python-gtkhtml2 libchewing3 libgutenprintui2-1 libvlc0 human-theme libnet-dbus-perl libwpd-stream8c2a libavc1394-0 libgdome2-0
  libwxbase2.6-0 libnm-glib0 python-vte libvte9 libgnomeui-0 libcroco3 libglitz1 human-icon-theme libhdf5-serial-1.6.5-0 libgtkhtml2-0
  libgsm1 libdvdnav4 libiso9660-4 libgnome-window-settings1 libmetacity0 python-launchpad-integration atlas3-base feisty-session-splashes
  libgimp2.0 libgdome2-cpp-smart0c2a python-gdbm libanthy0 librsvg2-2 libxklavier11 libavcodec0d liboobs-1-3 libkdeedu3 xaw3dg
  libgtkmathview0c2a libtar libgtkspell0 libg2c0 mkisofs binfmt-support libberyldecoration0 gnome-mount libvcdinfo0 libvte-common
  libgnome-desktop-2 librsvg2-common libgnomeprintui2.2-0 x-dev libgnomeprintui2.2-common libmpeg2-4 app-install-data-commercial
  liba52-0.7.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Suggestions?

---

### Post by Kubunteando on 2007-06-24
Then I think glut.h is still missing.
Try installing the package freeglut3-dev

---

### Post by shifty_powers on 2007-06-24
You might find using synaptic and searching through the repositories easier than using apt-get for this. Certainly what i do when I'm trying to resolve dependencies...

---

### Post by linuxnovice on 2007-06-24
Hi,
You were right. I installed that and everything else went smothly. Now the default installation directory was /usr/local. But I installed it in /usr. Then as per instructions given in this website [http://playerstage.sourceforge.net/doc/Gazebo-manual-0.5-html/install.html](http://playerstage.sourceforge.net/doc/Gazebo-manual-0.5-html/install.html) I tried to start gazebo on Konsole using the command:
gazebo /usr/local/share/gazebo/worlds/example1.world 
I just erased /local from the command since I didnt install it there.

Anyway when I tried to start it I got the follwoing error:
gazebo: error while loading shared libraries: libode.so: cannot open shared object file: No such file or directory

Any idea why it didnt start?

Thanks.

---

### Post by linuxnovice on 2007-06-24
Help please?

---

