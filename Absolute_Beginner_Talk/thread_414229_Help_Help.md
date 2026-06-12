---
title: "Help Help"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Stormweaver on 2007-04-19
Ok - I've been trying to enlist help here for a few days now, to which several people have started me down the road to aid, but never finished up... I attempted today to finish this issue myself - OMG what a mistake.


The thread that I was working from is [http://ubuntuforums.org/showthread.php?t=411049&highlight=Need+to+start+over](http://ubuntuforums.org/showthread.php?t=411049&highlight=Need+to+start+over) 


Now.. In frustration and having been given the idea of trying to use Synaptic I found the linux restricted modules listed as the error code from when Automatix attempted to install the Nvidia drivers.... So I installed them and anything else it said it needed to in order to install... Then I went back and installed the Nvidia from Automatix... It all looked good went in without errors and looked like I had finally finished this... now during the requested reboot the server has crashed --- Here is what it is saying, having to type this in as the server is Dead in the water..


"Failed to start the X Server (your grahpical interface)  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?"


PLEASE SOMEONE Please respond to this quickly, I can't afford for it to be down for long... My main box is  offline due to Mobo failure, now this is offline too, I had to borrow the wife's laptop to make this post and to try and wait for an awnser but she will need the LT back soon.... Can someone please tell me what I need to do to undo or fix what has gone wrong????


Help Help!


Stormweaver

---

### Post by Stormweaver on 2007-04-19
Update: I did manage to get it to command line.... But I don't know what to do to undo or fix this... My teamspeak server claims its running but I can't connect to it from another system.. Which means I will have friends calling any time now to find out whats going on... But thats ok.. its not a paid service .. I just feel bad that I tried to fix it and seemed to have cluster screwed it.

Anyone have any ideas on how to fix this?

---

### Post by silverglade00 on 2007-04-19
sudo nano /etc/X11/xorg.conf

Under Section "Device", change driver "nvidia" to "nv"

save and exit nano

reboot and you should be able to get back into X. This is just a fix for your immediate problem. Hopefully someone can help you with the rest of it.

---

### Post by nudnik on 2007-04-19
> **Stormweaver said:**
> Update: I did manage to get it to command line.... But I don't know what to do to undo or fix this... My teamspeak server claims its running but I can't connect to it from another system.. Which means I will have friends calling any time now to find out whats going on... But thats ok.. its not a paid service .. I just feel bad that I tried to fix it and seemed to have cluster screwed it.

Anyone have any ideas on how to fix this?

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure -phigh xserver-xorg

Select your resolution and all should be well. If it isnt, boot into recovery mode from GRUB and try the following

sudo nano /etc/X11/xorg.conf

Change the device driver from nv to vesa. Press Ctrl-X to save, answer yes and then hit enter when asked if the name to save under is correct.

---

### Post by silverglade00 on 2007-04-19
Follow nudnik's directions. They are much better than mine :)

---

### Post by Stormweaver on 2007-04-19
Update: Ok - Followed the temp fix post - Rebooted -- It has come back up - But as it was, I assume the temp fix disabled the changes.... So what do I do next??

---

### Post by Stormweaver on 2007-04-19
Ok - Followed the other instructions - Attempted to select nvidia as thats what the Card, Mobo, chipset all are... chose my screen sizes and saved and rebooted... it crashed at same point, went back in and chose vesa and its up to where it was before the crash.... What do I do now?


Stormweaver

---

### Post by nudnik on 2007-04-19
> **Stormweaver said:**
> Update: Ok - Followed the temp fix post - Rebooted -- It has come back up - But as it was, I assume the temp fix disabled the changes.... So what do I do next??

sudo /etc/init.d/gdm stop

Disable the "nv" driver by typing the following:

gksudo gedit /etc/default/linux-restricted-modules-common

Modify the line DISABLED_MODULES="" to the following:
Code:

DISABLED_MODULES="nv"

sudo apt-get reinstall nvidia-glx   (just in case)

sudo nvidia-glx-config enable

reboot

If it crashes again on reboot the glx driver may not agree with your system. If so, just stick with vesa or nv, whatever works. Remember the mascot.:)

---

### Post by Stormweaver on 2007-04-19
Attepted to do that gksudo gedit... 

gksudo:5533 Gtk-WARNING cannot open display:



I tried it in terminal without shutting down gdm and it gave me a warning but opened the file... I did NOT change while gdm was active.  Whats next?


Stormweaver

---

### Post by nudnik on 2007-04-19
> **Stormweaver said:**
> Attepted to do that gksudo gedit... 

gksudo:5533 Gtk-WARNING cannot open display:



I tried it in terminal without shutting down gdm and it gave me a warning but opened the file... I did NOT change while gdm was active.  Whats next?


Stormweaver

Sorry, lots of brain damage here. You will need to edit the bit with the display error using nano as well. Otherwise, all else should be correct, but we are tinkering with Linux, so you never know. I have to wander off to bed for a while. I shall sacrifice a goat in your honor and perhaps someone at least as wonderful as me will come along in a minute or two:)

---

### Post by igknighted on 2007-04-19
You need to download the kernel-header package for the server, then go to nvidia.com to get the driver installer there as I said in your other thread.  You are using a server kernel, therefor you cannot install nvidia-glx from the repo to work with that kernel.  So install the appropriate linux-header-server package from synaptic, then get the driver from nvidia.  Follow the install instructions on their site, except when they say to type init 3 to kill the Xserver, you need to type "sudo /etc/init.d/gdm stop" as Ubuntu doesn't use standard run-levels.

DO NOT USE SYNAPTIC TO INSTALL THE DRIVERS ON THE SERVER KERNEL... IT WILL FAIL LIKE THAT EVERY TIME.

---

### Post by Stormweaver on 2007-04-19
Ok gdm is up and running, using synaptic I have removed my attempted fix...


So I am back at the beginning - I have nvidia equipment... I have a server that I need to configure for what I have, so that it can be used for what its designed... Any ideas???


Stormweaver

---

### Post by igknighted on 2007-04-19
> **Stormweaver said:**
> Ok gdm is up and running, using synaptic I have removed my attempted fix...


So I am back at the beginning - I have nvidia equipment... I have a server that I need to configure for what I have, so that it can be used for what its designed... Any ideas???


Stormweaver

Run the command "uname -r".  If it mentions server anywhere, follow my directions above and it will work.  Aside from the kernel headers, you need to forget about synaptic... the drivers from synaptic cannot work for you, so uninstall them as they could mess you up later on.

---

### Post by Stormweaver on 2007-04-19
Yeah I've been trying to find the referenced header - Just not had any luck... Searching Synaptic did not reveal a linux-header-server  -- But I figure I am searching wrong for it.

As to the command - 2.6.17-11-386 is what popped up

Sorry if I have freaked out in here, I am trying to stay with the game now..

So I will go back to synaptic to look for linux-header-server package and await a post.


Stormweaver

---

### Post by igknighted on 2007-04-19
> **Stormweaver said:**
> Yeah I've been trying to find the referenced header - Just not had any luck... Searching Synaptic did not reveal a linux-header-server  -- But I figure I am searching wrong for it.

As to the command - 2.6.17-11-386 is what popped up

Sorry if I have freaked out in here, I am trying to stay with the game now..

So I will go back to synaptic to look for linux-header-server package and await a post.


Stormweaver

EDIT: you do not want to run -386.  install generic or boot from your previous -server kernel at boot.

---

### Post by Stormweaver on 2007-04-19
Forgive my noobness at the moment..

How do I get the generic driver back???

Also where do I search for the linux header?? I tried looking at nvidia in hopes of a link which it does mention needing to have it, however, it does not mention where to pull it from.

---

### Post by igknighted on 2007-04-19
> **Stormweaver said:**
> Forgive my noobness at the moment..

How do I get the generic driver back???

Also where do I search for the linux header?? I tried looking at nvidia in hopes of a link which it does mention needing to have it, however, it does not mention where to pull it from.

1st, reboot.  At the grub prompt, choose the kernel labeled server, not i386.  i386 is rather limited, and it sounds like your AMD64 process is rather new, and will be limited by that kernel.

2nd, open a terminal and type "apt-cache search header", no quotes.  Post the result here, but there should be something to do with server kernel headers.

3rd, if you know which one is the one you need (or after we help you here), type "sudo apt-get install <package found above>".  This will install the headers.

4th, go on with Nvidias instructions.

---

### Post by Stormweaver on 2007-04-19
```
libgcgi-dev - library for CGI programs in C
libgchemutils-dev - GNOME chemistry utils (development version)
libgdal1-1.3.1-dev - Geospatial Data Abstraction Library - Development files
libgdgeda-dev - GNU EDA -- Electronics design software -- gd development files
libgeant321-2-dev - [Physics] Library for Geant 3.21 (development files)
libgeos-dev - Geometry engine for GIS - Development files
libgfortran0-dev - GNU Fortran library development
libgfortran1-dev - GNU Fortran library development
libgfshare-dev - Shamir Secret Sharing in Galois Field library
libggtl2-dev - generic game-tree search library
libggz-dev - GGZ Gaming Zone: common utilities library - development files
libggzcore-dev - GGZ Gaming Zone: core client frontend library - development files
libggzmod-dev - GGZ Gaming Zone: game frontend library - development files
libghemical-dev - Molecular Modelling Library (Development Files)
libghttp-dev - original GNOME HTTP client library - development kit
libgift-dev - helper library for various giFT components [development files]
libgiftproto-dev - interface library for giFT and protocol plugins [development files]
libgig-dev - library for loading Gigasampler files and DLS Level 1/2 files
libginac-dev - The GiNaC symbolic framework (development files)
libgl1-mesa-glide3-dev - A free implementation of the OpenGL API -- glide development support files
libglide2-dev - graphics library for 3Dfx Voodoo based cards - development files
libglide3-dev - graphics library for 3Dfx Voodoo based cards - development files
libglom-dev - Glom library (a database designer and user interface) - header files
libgnokii3-dev - Gnokii library
libgnomesu-dev - a library which allows you to run programs as root or another user
libgnuradio-core0-dev - Software Defined Radio
libgnustep-base-dev - GNUstep Base header files and development libraries
libgnustep-gui-dev - GNUstep GUI header files and static libraries
libgoogle-perftools-dev - libraries for CPU and heap analysis, plus an efficient thread-caching malloc
libgpewidget-dev - Development files for libgpewidget
libgpgme-dev - GPGME - GnuPG Made Easy
libgpib-bin - libgpib support applications and configuration
libgpib-perl - libgpib perl bindings
libgpib0 - C bindings for GPIB (IEEE 488) kernel driver -- headers
libgpib0-dev - C bindings for GPIB (IEEE 488) kernel driver -- headers
libgpiv2-dev - Library for Particle Image Velocimetry (PIV)
libgraflib1-dev - Cernlib graphical library (development files)
libgrafx11-1-dev - Cernlib library interface to X11 and PostScript (development)
libgraphicsmagick++1-dev - format-independent image processing - C++ development files
libgraphicsmagick1-dev - format-independent image processing - C development files
libgraphite-dev - Development files for SILGraphite
libgrapple-dev - a network layer designed for games (development files)
libgrass-dev - GRASS GIS library development files
libgretl1-dev - The GNU Regression, Econometric & Time-Series Library -- development package
libgringotts-dev - Development files for the Gringotts data encapsulation library
libgsmme-dev - Header files and static libraries for gsmlib
libgstreamer0.8-dev - GStreamer development libraries and headers
libgtk-canvas1-dev - port of GNOME Canvas back to gtk+ -- development files
libgtkada2-bin - Development files for libgtkada2
libgtkextra-dev - A useful set of widgets for GTK+ (development files)
libgtkextra17-dev - A useful set of widgets for GTK+ (development files)
libgtkextramm-dev - Static library and header files of GtkExtramm
libgtkhex0-dev - GNOME Hex editor for files (development headers)
libgtksourceviewmm-1.0-dev - C++ binding of GtkSourceView (headers)
libguile-dev - Development headers and static library for libguile
libgwrapguile-dev - Development package for libgwrapguile1
libhd13-dev - Hardware identification system library and headers
libhdate-dev - A library that help use hebrew dates
libherwig59-2-dev - [Physics] Monte Carlo event generator for hadrons (development)
libhighgui-dev - development files for libhighgui
libhk-classes13-dev - development libraries and headers for libhk-classes
libhk-kdeclasses8-dev - development files for libhk-kdeclasses
libhnj-dev - hyphenation and justification library (development files)
libhocr-dev - Developemnt files for hocr library
libhtml-mason-perl - HTML::Mason Perl module
libhtml-mason-perl-doc - HTML::Mason documentation
libhtml-mason-perl-examples - HTML::Mason example setup
libhttp-cache-transparent-perl - Perl module used to transparently cache HTTP requests
libhz-dev - Headers and static libraries for zh-autoconvert
libi18n-acceptlanguage-perl - Matches language preference to available languages
libibtk-dev - Insomnia's Basic ToolKit: Development Libraries and Header Files
libibverbs-dev - Development files for the libibverbs library
libiconv-hook-dev - header files of libiconv-hook
libifstat-dev - Ifstat Development Files
libiiimcf-dev - IIIM Client Framework library development files
libiiimp-dev - IIIM Protocol library development files
libiksemel-dev - iksemel is a C library for the Jabber IM platform
libindex0-dev - KDE indexing library [development]
libisajet758-2-dev - [Physics] Monte Carlo generator for proton/electron reactions
libiso9660-dev - library to work with ISO9660 filesystems (development files)
libiterm-dev - internationalized terminal emulator, development files
libjabberoo-dev - library to interact with Jabber
libjcode-pm-perl - Perl extension interface to convert Japanese text
libjpeg-mmx-dev - Development files for the IJG JPEG library with mmx optimization
libjs0-dev - The NGS JavaScript interpreter - development files
libjsw-dev - Joystick Library header files
libjuman-dev - Header files of JUMAN
libkakasi2-dev - Header files and static libraries for library version of KAKASI
libkdtree++-dev - C++ template container implementation of kd-tree sorting
libkernlib1-dev - core Cernlib library of basic functions (development files)
libkmfl-dev - A Library for providing Keyman(C) services to Linux - development
libkmflcomp-dev - Development files for libkmflcomp
libkst1-dev - Headers for the kst application for displaying scientific data
libktoblzcheck1-dev - development files for libktoblzcheck1
libkwnn-dev - Header files and static library for kWnn (FreeWnn kserver)
libkxl0-dev - development files for libkxl0
libleakbug-dev - Development files for GNUpdate leakbug tracer library
liblineak-dev - LinEAK development files
liblink-grammar4-dev - Carnegie Mellon University's link grammar parser for English
liblivemedia-dev - multimedia RTSP streaming library
liblo0-dev - Lightweight OSC library -- development files
libloki-dev - a C++ library of generic design patterns (development files)
libloudmouth1-dev - Development files for Loudmouth Jabber library
liblrdf0-dev - liblrdf0 development files
liblscp-dev - LinuxSampler Control Protocol wrapper library
liblua40-dev - Main interpreter library for lua40: static library and headers
liblualib40-dev - Extension library for Lua 4.0: static and headers
libluminate-dev - Illuminator Distributed Visualization Library: development files
liblzo2-dev - data compression library (development files)
libm17n-dev - a multilingual text processing library - development
libmalaga-dev - Developer's library for automatic language analysis
libmaloc-dev - Object-oriented Abstraction Layer for C (development files)
libmas-dev - Media Application Server development libraries
libmath++-dev - C++ Math Type Library, development files
libmatheval1-dev - GNU library for evaluating symbolic mathematical expressions (development)
libmathlib2-dev - core Cernlib mathematical library (development files)
libmatroska-dev - extensible open standard audio/video container format
libmcal0-dev - Calendar libraries with icap and mstore support
libmecab-dev - Header files of Mecab
libmemcache-dev - development headers for libmemcache C client API
libmilter-dev - Sendmail Mail Filter API (Milter)
libmilter0 - Sendmail Mail Filter API (Milter)
libmilter0-dbg - Sendmail Mail Filter API (Milter)
libmimetic-dev - C++ MIME library (development)
libminc0-dev - MNI medical image format development environment
libming-dev - Library to generate SWF (Flash) Files (development files)
libmodxslt0-dev - Development header for libmodxslt
libmorph-dev - digital image warping library (development files)
libmpd-dev - High-level client library for accessing Music Player Daemon
libmpeg2-4-dev - libmpeg2 development libraries and headers
libmpeg3-dev - Headers and static libraries for libMPEG3
libmpich-mpd1.0-dev - mpich static libraries and development files
libmpich-shmem1.0-dev - mpich static libraries and development files
libmpich1.0-dev - mpich static libraries and development files
libmudflap0-dev - GCC mudflap support libraries (development files)
libmysqlclient10-dev - LGPL-licensed client development files for MySQL databases
libmysqlclient12-dev - mysql database development files
libmysqlclient14-dev - mysql database development files
libmythes0 - simple thesaurus library (development files)
libncbi6-dev - NCBI libraries for biology applications (development files)
libncp-dev - libncp: development libraries and header files
libneon24-dev - Header and static library files for libneon24
libnet-rawip-perl - Perl interface to lowlevel TCP/IP
libnetgen-dev - Automatic 3d tetrahedral mesh generator development files
libnetpbm9-dev - Development libraries and header files
libnettle-dev - low level cryptographic library (development files)
libnewmat10-dev - matrix manipulations C++ library
libnews-article-perl - Perl modules for manipulating Usenet articles
libnjb1-dev - Creative Labs Nomad Jukebox library development files
libnmz7-dev - libnmz header files and static libraries.
libnoise-dev - a portable, coherent noise-generating library for C++
libnuma-dbg - Debug package for libnuma
libnuma-dev - Development files for libnuma
libnumerix-ocaml-dev - Numerix "big integer" library for OCaml
libnurbs++-dev - C++ NURBS library - development package
libnws-dev - grid monitoring infrastructure (headers and devel documentation)
libobjc-lf2-dev - Header files for the libFoundation fork of the Objective-C library
libodbc++-dev - C++ library for ODBC SQL database access
libode0-dev - Open Dynamics Engine - development files
libofbis-dev - simple Linux framebuffer graphical library - development files
libofx-dev - development package for libofx2c2a
libogg-vorbis-decoder-perl - An object-oriented Ogg Vorbis decoder
libogg-vorbis-header-perl - perl interface to Ogg Vorbis information and comments
libogg-vorbis-header-pureperl-perl - A pure Perl interface to Ogg Vorbis information fields
liboggz1-dev - convenience interface for Ogg stream I/O (development files)
libogre-dev - Object-oriented Graphics Rendering Engine (development files)
liboil0.2-dev - Library of Optimized Inner Loops (development headers)
libomnievents-dev - Implementation of the CORBA Event Service
libooc-x11 - X11 specific modules for the oo2c compiler
libooc-x11-dev - X11 specific modules for the oo2c compiler (devel)
liboop-dev - Event loop management library - development files
libopenafs-dev - AFS distributed filesystem development libraries
libopenal-dev - OpenAL is a portable library for 3D spatialized audio
libopenbabel-dev - Convert and manipulate chemical data files (development version)
libopenct1-dev - headers and development libraries for libopenct1
libopenh323-dev - H.323 aka VoIP library development files
libopenipmi-dev - Intelligent Platform Management Interface - development
libopenspc-dev - library for playing SPC files (development headers)
libopensync0-dev - Headers and static libraries for libopensync
libopenvrml5-dev - developer libraries for openvrml
liborbit-dev - Dev libraries for ORBit - a CORBA ORB
liborsa0-dev - ORSA framework library (development files)
libosip2-dev - development files for the SIP library
libossp-uuid-dev - OSSP uuid ISO-C and C++ - headers and static libraries
libotf-dev - A Library for handling OpenType Font - development
libotr2-dev - Off-the-Record Messaging library development files
libp11-dev - pkcs#11 convenience library - development files
libpacklib1-dev - core Cernlib library (development files)
libpano12-dev - panorama tools library development files
libpcd-dev - Header files and static library for libpcd
libpcl1-dev - Portable Coroutine Library (PCL), development files
libpdflib804-2-dev - [Physics] Comprehensive library of parton density functions
libpeercast0-dev - P2P audio and video streaming server -- development
libpetsc2.3.1-dev - Static libraries, shared links, header files for PETSc
libpfm3-dev - Performance Monitor Unit (PMU) -- development files
libpgeasy-dev - simplified interface library for postgresql - development files
libpgtcl-dev - Tcl client library binding for PostgreSQL - development files
libphysfs-dev - development files for filesystem abstraction library
libpixman1-dev - Cairo pixel manipulation library development libraries and headers
libplot-dev - The GNU plotutils libraries (development files)
libpmount-dev - portable mount library - development files
libpngwriter0-dev - easy to use graphics library (development)
libportmidi-dev - library for real-time MIDI input/output
libpostproc-dev - development files for libpostproc
libppd-dev - postscript PPD file library, development kit
libpqxx-dev - C++ library to connect to PostgreSQL (development files)
libprinterconf-dev - Printer autodetection library
libqcad0-dev - Qcad development headers and static libraries
libqdbm++-dev - QDBM Database Libraries for C++ [development]
libqdbm-dev - QDBM Database Libraries [development]
libqgis0-dev - QGIS Geographic Information System - development files
libqglviewer-dev - A qt/OpenGL-based viewing widget
libqhull-dev - Calculate convex hulls and related structures (development files)
libqt4-debug-dev-kdecopy - Qt 4 debugging development files
libqt4-dev-kdecopy - Qt 4 development files
libqttelepathy-dev - Qt bindings for Telepathy - library headers
libquantlib0-dev - Quantitative Finance Library -- library package
libquantum-dev - library for the simulation of a quantum computer
libradius1-dev - /bin/login replacement with RADIUS. Header file and link lib.
libradiusclient-ng-dev - Enhanced RADIUS client library development files
libreiserfs0.3-dev - ReiserFS access and manipulation library - development files
librep-dev - development libraries and headers for librep
libroxen-expires - Page expiration module for the Roxen Challenger web server
libroxen-meta - Metafiles module for the Roxen Challenger web server
librplay3-dev - Development libraries for the rplay network audio system
librudiments-dev - C++ class library providing base classes
libruli4-dev - Library for easily querying DNS SRV records - development files
librvm-dev - Recoverable Virtual Memory (development files)
librxp1-dev - Development files for librxp
libsablevm1-dev - Free implementation of JVM second edition - JNI development files
libsc-dev - The Scientific Computing Toolkit (development version)
libsctp-dev - user-space access to Linux Kernel SCTP - development files
libsdl-console-dev - development files for libsdl-console
libsdl-gfx1.2-dev - development files for SDL_gfx
libsdl-net1.2-dev - Development files for SDL network library
libsdl-sge-dev - development files for libsdl-sge
libsdl-sound1.2-dev - Development files for SDL_sound
libsdl-stretch-dev - Development files for SDL_stretch library
libseal-dev - development files for libseal, the synthetic audio library
libsemanage1-dev - Header files and libraries for SELinux policy manipulation tools
libserveez-dev - GNU Serveez server framework -- development files
libsexymm-dev - collection of additional gtkmm widgets - header files
libsgutils1-dev - Utilities for working with generic SCSI devices (developer files)
libsident0-dev - Development files to do S/Ident authentication
libsidplay1-dev - SID (MOS 6581) emulation library (development files)
libsigcx-0.6-dev - libSigCX (libSigC++ Extras) - development
libsigcx-gtk-0.6-dev - libSigCX (libSigC++ Extras) GTK+ dispatcher - development
libsimplelist0-dev - memory-efficient generic linked list library
libsmtpguard-dev - Development files for smtpguard
libsnacc-dev - ASN.1 to C or C++ or IDL compiler, development files
libsndfile0 - Library for reading/writing audio files
libsndfile0-dev - Library for reading/writing audio files
libsnmpkit-dev - multithreaded SNMP connection library
libsocksd-dev - Development files for compiling programs with SOCKS support
libsofia-sip-ua-dev - Sofia-SIP library development files
libsofia-sip-ua-glib-dev - Sofia-SIP library glib/gobject interface development files
libsope-core4.4-dev - Development files for the SOPE core libraries
libsope-gdl1-4.4-dev - Development files for the GNUstep database libraries
libspandsp-dev - Telephony signal processing library
libspeechd-dev - Speech Dispatcher: Development libraries and header files
libspf2-dev - Header and development libraries for libspf2
libsphinx2-dev - speech recognition library - development kit
libspread1-dev - Development files for libspread
libsprng2-dev - The SPRNG Scalable Parallel RNG library -- development package
libsqldbc75-dev - Development package for the SQLDBC interface to the MaxDB database system
libsqlod75-dev - Development package for the ODBC interface to the MaxDB database system
libstdc++2.10-dev - The GNU stdc++ library (development files)
libstdc++6-4.0-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6-dev - The GNU Standard C++ Library v3 (development files)
libstroke0-dev - mouse strokes library -- development files
libsvga1-dev - console SVGA display development libraries and headers
libsvncpp-dev - Subversion C++ library (development files)
libsvnqt-dev - Qt wrapper library for subversion (development files)
libsword-dev - Development files for libsword
libsyck0-dev - YAML parser kit -- development files
libsylpheed-claws-dev - Development files to build plugins for Sylpheed-Claws
libsylpheed-claws-gtk2-dev - Development files for Sylpheed-Claws GTK2 plugins
libsynfig-dev - synfig library development files
libsynfigapp-dev - synfig GUI library development files
libtabe-dev - C development library for Chinese lexicons related functions
libtao-dev - Development files for TAO, The ACE ORB
libtao-orbsvcs-dev - The ACE ORB, an open-source implementation of CORBA ORB
libtar-dev - C library for manipulating tar archives
libtasn1-2-dev - Manage ASN.1 structures (development)
libtelepathy-dev - Telepathy framework - GLib library headers
libtext-header-perl - RFC 822/2068 header and unheader functions
libticables3-dev - support library for Texas Instruments link cables [development files]
libticalcs4-dev - provides functions to communicate with TI calculators [development files]
libtifiles0-dev - Texas Instruments calculators file formats library [development files]
libtmail-ruby-doc - Documentation about TMail
libtmail-ruby1.8 - Mail class library for Ruby 1.8
libtolua-dev - Tool to integrate C/C++ code with Lua - development files
libtolua0 - Tool to integrate C/C++ code with Lua - runtime libraries
libtorch3-dev - State of the art machine learning library - development files
libtre-dev - development package for the libtre4 regexp matching library
libtse3-dev - portable MIDI sequencer engine in C++ - development files
libtulip-2.0-dev - Tulip graph library - core development files
libtulip-ogl-2.0-dev - Tulip graph library - OpenGL development files
libtulip-qt4-2.0-dev - Tulip graph library - Qt/OpenGL gui development files
libtwofish-dev - Niels Ferguson's Twofish cryptographic algorithm library
libuclibc-dev - A small implementation of the C library
libuclmmbase1-dev - UCL Common Code (Multimedia) Library - development
libufsparse-dev - collection of libraries for computations for sparse matrices
libuim-dev - Development files for uim
libupnp-dev - Intel Universal Plug And Play SDK for Linux (development files)
libvanessa-adt-dev - Headers and static libraries for vanessa_adt
libvanessa-logger-dev - Headers and static libraries for libvanessa-logger
libvanessa-socket-dev - Headers and static libraries cor libvanessa_socket
libvcdinfo-dev - library to extract information from VideoCD (development files)
libvdk2-dev - header files and static libraries for VDK library version 2
libvdk2-doc - documentation for VDK library version 2
libvdkbuilder2-dev - Header files and static libraries for VDKBuilder plugins
libvigraimpex-dev - A C++ computer vision library
libvncserver-dev - easy API to write one's own VNC server
libvtk5-dev - VTK header files for building C++ code
libwarped0-dev - Development files needed to compile programs that use warped.
libwavpack-dev - an audio codec (lossy and lossless) - development files
libwebauth1-dev - Development files for WebAuth authentication
libwmaker0-dev - Static libraries and headers for Window Maker applications
libwn-dev - Many numerical and memory management functions
libwnn-dev - Header files and static libraries for Wnn (FreeWnn jserver)
libwnn6-dev - Header files and static library for Wnn6 client library
libwraster3-dev - Static libraries and headers of Window Maker rasterizer
libwsound-dev - WSoundServer development files
libxapian-dev - Development files for Xapian search engine library
libxaw6-dev - X11 Athena Widget library (development headers)
libxbae-dev - Xbae Matrix Widget development package
libxbox-dev - Headers for use with libxbox
libxclass0-dev - C++ GUI toolkit for X
libxcrypt-dev - Development files for Crypt library
libxen3.0-dev - headers for Xen, a Virtual Machine Monitor
libxfontcache-dev - X11 font rasterisation library (development headers)
libxiterm-dev - internationalized terminal emulator, X widget development files
libxkbsel-dev - Tool for defining, selecting, and indicating XKB keyboards.
libxml-smart-perl - Convenience features for access to parsed XML trees
libxmlrpc++-dev - C++ library for XML-RPC - Development files
libxnee-dev - X event recorder/replayer - development files
libxosd-dev - X On-Screen Display library - development
libxprintapputil-dev - Xprint job utility client library (development files)
libxprintutil-dev - Xprint printer utility client library (development files)
liby-dev - Y Sound Server Library Header Files
libyaz2-dev - The YAZ Z39.50 toolkit (development files)
libytnef0-dev - improved decoder for application/ms-tnef attachments
libzzip-dev - library providing read access on ZIP-archives - development
licq-dev - Licq development and header files
listadmin - command line mailman moderator queue manipulation
litmus - WebDAV server protocol compliance test suite
llgal - Command-line online gallery generator
lout - Typesetting system, an alternative to (La)TeX
ltp-dev - development files for Linux Test Project
luasocket-dev - TCP/UDP socket library for Lua 5.0
mailagent - An automatic mail-processing tool and filter.
mairix - indexes and searches email in locally stored email
mffm-gtkclasses-dev - GTK header files which make GUI implementation more trivial in C++
mh-e - Emacs interface to the MH mail system
mimedecode - Decodes transfer encoded text type mime messages
minpack-dev - nonlinear equations and nonlinear least squares static library
mlmmj - mail server independent mailing list manager
mn-fit-dev - libraries and header files for creating a custom Mn_Fit
mnogosearch-dev - MnoGoSearch: Development Libraries and Header Files
module-assistant - tool to make module package creation easier
mozilla-dev - The Mozilla Internet application suite - development files
mozilla-livehttpheaders - Adds information about the HTTP headers to Mozilla
mpatrolc2 - A library for debugging memory allocations
mserv-dev - local centralised multiuser music environment
muttprint - Pretty printing of mails
nast - packet sniffer and lan analyzer
netcdfg-dev - Development kit for NetCDF
netdude - NETwork DUmp data Displayer and Editor for tcpdump trace files
nget - auto-resuming command line NNTP file grabber
nozomi-source - source for GlobeTrotter HSDPA kernel driver
ntlmaps - NTLM Authorization Proxy Server
nut-dev - Development files for the nut - Network UPS Tools
nzb - An nzb based Usenet binary grabber
octave2.1-headers - header files for the GNU Octave language (2.1 branch)
octave2.9-headers - header files for the GNU Octave language (2.9 branch)
openexr - viewer and docs for the OpenEXR image format
openggsn-dev - development package for openggsn
p4fftwgel-dev - library for computing Fast Fourier Transforms on Intel P4
p4fftwgel2 - library for computing Fast Fourier Transforms on Intel P4
packit - Network Injection and Capture
pentanet-dev - Libraries and header files for interfacing with Pent@NET driver
perdition-dev - Development libraries and headers for perdition
pfe-dev - Portable Forth Environment, development files
php-fpdf - PHP class to generate PDF files
php4-gpib - libgpib php bindings
pinball-dev - Development files for the Emilia Pinball Emulator
pistachio-kernel-headers - L4 microkernel implementation - kernel headers
playground-dev - development files to build playground plugins
plib1.8.4-dev - Portability Libraries: Development package, stable release
plib1.8.4-pic - Portability Libraries: Dev. package (with PIC code), stable rel.
plplot-tcl-dev - Tcl/Tk development support for PLplot, a plotting library
plptools-dev - plptools (development files)
pmk - utility to configure software sources
pnet-dev - Development package for DotGNU Portable.NET
poe.app - Vorbis comment editor
poedit - cross-platform gettext catalog editor
popfile - email classification tool
post-faq - post periodic FAQs to Usenet newsgroups
postal - SMTP benchmark - the mad postman.
postgresql-server-dev-7.4 - development files for PostgreSQL 7.4 server-side programming
pvm-dev - Parallel Virtual Machine - development files
python-gpib - libgpib python bindings (default package)
python-mutagen - audio metadata editing library
python-pyfits - Python module for reading, writing, and manipulating FITS files
python-pyfits-doc - Documentation for PyFITS
python2.3-sip-dev - Python/C++ bindings generator - Python2.3+Qt3 devel
python2.4-sip-dev - Python/C++ bindings generator - Python2.3+Qt3 devel
rawdog - RSS Aggregator Without Delusions Of Grandeur
regina3-dev - The Regina REXX interpreter, development files
rioutil - Talk to USB based Diamond MM products
robodoc - A source code documentation tool
rsplib-dev - development package for rsplib1
rt2400-source - RT2400 wireless network drivers source
rt2500-source - RT2500 wireless network drivers source
rt2570-source - RT2570 wireless network drivers source
ruby1.9-dev - Header files for compiling extension modules for the Ruby 1.9
sciplot-dev - Development library and header files for SciPlot
sctplib-dev - userland implementation of the SCTP protocol RFC 2960
semi - library to provide MIME feature for emacsen
sendip - A commandline tool to allow sending arbitrary IP packets
sfftw-dev - library for computing Fast Fourier Transforms
sfftw2 - library for computing Fast Fourier Transforms
simgear-dev - Simulator Construction Gear -- development files
slrnpull - pulls a small newsfeed from an NNTP server
snappea-dev - development files for SnapPea hyperbolic 3-manifold tool
socketapi-dev - development package for socketapi1
spamass-milter - sendmail milter for filtering mail through spamassassin
spamassassin-rules-ja - Japanese filter rules for spamassassin
spamoracle - A statistical analysis spam filter based on Bayes' formula
spamoracle-byte - A statistical analysis spam filter based on Bayes' formula
spampd - spamassassin based SMTP/LMTP proxy daemon
spamprobe - Bayesian spam filter
spca5xx-source - source for the spca5xx driver
spellutils - Utilities to spell-check selectively
spikeproxy - Web application security testing proxy
sqcwa - Workaround for Squid not caching some pages
sqlrelay-dev - SQL Relay C and C++ APIs
squashfs-source - Source for the squash filesystem
stegdetect - Detect and extract steganography messages inside JPEG
styx-dev - combined parser/scanner generator development files
sufary-dev - Development files for SUFARY
sweep-dev - Development files for sweep plug-ins
swish-e-dev - Simple Web Indexing System for Humans - Enhanced
sylpheed-claws - Extended version of the Sylpheed mail client
sylpheed-claws-gtk2-fetchinfo-plugin - X-FETCH headers adder for Sylpheed-Claws GTK2 mailer
sylpheed-claws-gtk2-newmail-plugin - New mail logger plugin for Sylpheed-Claws GTK2 mailer
tcl8.0-dev - Tcl (the Tool Command Language) v8.0 - development files
tcpxtract - extracts files from network traffic based on file signatures
teapop - Powerful and flexible RFC-compliant POP3 server
teapop-ldap - Powerful and flexible RFC-compliant POP3 server
teapop-mysql - Powerful and flexible RFC-compliant POP3 server
teapop-pgsql - Powerful and flexible RFC-compliant POP3 server
testdisk - Partition scanner and disk recovery tool
texgd - Program to convert short TeX formulas to PNG graphics
texlive-generic-extra - TeX Live: Miscellaneous extra generic macros
texlive-latex-base - TeX Live: Basic LaTeX packages
texlive-latex-extra - TeX Live: LaTeX supplementary packages
tinycdb - a package for creating and reading constant databases
tinyproxy - A lightweight, non-caching, optionally anonymizing http proxy
tinysnmp-agent-dev - Libraries and header files for developing TinySNMP plugins
tinysnmp-manager-dev - Libraries and header files for developing TinySNMP programs
tk8.0-dev - Tk toolkit for Tcl and X11, v8.0 - development files
tqsllib-dev - QSL signing library development files
translucency-source - Filesystem translucency module - module source
txt2tags - a conversion tool generating HTML/SGML/LaTeX/man/MoinMoin/mgp/PageMaker files
uclibc-toolchain - A compiler wrapper for uClibc
ulog-acctd - Accounting daemon for Linux 2.4+ netfilter
unixcw-dev - Development files for Morse programs
vdr-dev - Video Disk Recorder for DVB cards
vflib3-dev - Development files for VFlib3
wacom-kernel-source - source for the wacom binary modules
wordnet-dev - electronic lexical database of English language
wsola-dev - header files for the embedded WSOLA algorithm
wx2.4-headers - wxWindows Cross-platform C++ GUI toolkit (header files)
xen-headers-2.6.16 - Header files related to Linux kernel, specifically, version 2.6.16
xen-headers-2.6.17-6 - Header files related to Linux kernel, specifically, version 2.6.17
xen-headers-2.6.17-6-bigiron-xen0 - Linux kernel headers 2.6.17 on xen
xen-headers-2.6.17-6-generic-xen0 - Linux kernel headers 2.6.17 on xen
xen-headers-2.6.17-6-server-xen0 - Linux kernel headers 2.6.17 on xen
xen-source-2.6.16 - Linux kernel source for version 2.6.17 with Ubuntu patches
xen-source-2.6.17 - Linux kernel source for version 2.6.17 with Ubuntu patches
xfaces - Displays an image for each piece of mail in your mailbox
xmhtml1 - A Motif widget for display HTML 3.2
xmhtml1-dev - A Motif widget for display HTML 3.2
xviewg-dev - XView development tools
zope-cachefu - suite of Zope products for speeding up Plone
zope-resourceregistries - zope registry for linked stylesheet files and javascripts
zope-securemailhost - secure MailHost reimplementation for zope
autorespond - email autoresponder for qmail
em8300-headers - Kernel headers to access DXR3/Hollywood+ decoder cards
foiltex - a collection of LaTeX files for making foils and slides
ipw2100-source - source for the ipw2100 driver
liblame-dev - LAME Ain't an MP3 Encoder
libmotif-dev - Open Motif - development files
libtrain-dev - The train-routing calculator library - development
manpages-posix-dev - Manual pages about using a POSIX system for development
vmware-player-kernel-source - Source for the vmware-player-kernel drivers.
x-pgp-sig-el - X-PGP-Sig mail and news header utility for Emacs.
stormweaver@Eye-of-the-Storm:~$ 

```

It cut off the first part, and after 3 attempts of listing the same command I could not get a capture of the whole thing.

I did get the reboot done, it is running kernal mode now.

Waiting for reply

Stormweaver

---

### Post by igknighted on 2007-04-19
grr, try this, scrollback wasn't enough to hold it all:

apt-cache search header > ~/header.txt

This will make a text file in your home folder, copy and paste the first part of that file, at least up until the other one picks up?

---

### Post by Stormweaver on 2007-04-19
```
apache2-prefork-dev - development headers for apache2
apache2-threaded-dev - development headers for apache2
libapr0-dev - development headers for libapr
libdb4.2++-dev - Berkeley v4.2 Database Libraries for C++ [development]
libdb4.2-dev - Berkeley v4.2 Database Libraries [development]
libdb4.3++-dev - Berkeley v4.3 Database Libraries for C++ [development]
libdb4.3-dev - Berkeley v4.3 Database Libraries [development]
comerr-dev - common error description library - headers and static libraries
libexpat1-dev - XML parsing C library - development kit
libstdc++6-4.1-dev - The GNU Standard C++ Library v3 (development files)
libneon25-dev - Header and static library files for libneon25
libldap2-dev - OpenLDAP development libraries
libssl-dev - SSL development libraries, header files and documentation
libpcre3-dev - Perl 5 Compatible Regular Expression Library - development files
postfix-dev - Postfix loadable modules development environment
libsvn0-dev - development files for Subversion (aka. svn) libraries
atlantik-dev - Development files for Atlantik
autoconf2.13 - automatic configure script builder (obsolete version)
autogen - an automated text file generator
binutils-dev - The GNU binary utilities (BFD development files)
blt-dev - the BLT extension library for Tcl/Tk - development files
brltty - Access software for a blind person using a soft braille terminal
console-tools-dev - Development files for Linux console and font manipulation
cracklib2-dev - pro-active password checker library - development
e2fslibs-dev - ext2 filesystem libraries - headers and static libraries
emacs-goodies-el - Miscellaneous add-ons for Emacs
expect-tcl8.3-dev - Development files for the expect package
festival-dev - development kit for the Festival speech synthesis system
fftw3 - library for computing Fast Fourier Transforms
fftw3-dev - library for computing Fast Fourier Transforms
flite1-dev - A small run-time speech synthesis engine - static libraries
freeglut3-dev - OpenGL Utility Toolkit development files
freetds-dev - MS SQL and Sybase client library (static libs and headers)
gaim-dev - multi-protocol instant messaging client - development files
graphviz-dev - graphviz Libs and Headers aginst which to build applications
iproute-dev - Development package for iproute
iptables-dev - development files for iptable's libipq and libiptc
kate-plugins - plugins for Kate, the KDE Advanced Text Editor
kdemultimedia-dev - development files for the KDE multimedia module
kernel-package - A utility for building Linux kernel related Debian packages.
kolf-dev - Development files for Kolf
kommander-dev - development files for Kommander
lib64ncurses5-dev - Developer's libraries for ncurses (64-bit)
libaa1-dev - ascii art library, development kit
libacl1-dev - Access control list static libraries and headers
libanthy-dev - Anthy static library, headers and documets for developers
libao-dev - Cross Platform Audio Output Library Development
libapache2-mod-perl2-dev - Integration of perl with the Apache2 web server - development files
libapm-dev - Library for interacting with APM driver in kernel
libapt-pkg-dev - Development files for APT's libapt-pkg and libapt-inst
libarts1-dev - development files for the aRts sound system core components
libartsc0-dev - development files for the aRts sound system C support library
libaspell-dev - Development files for applications with GNU Aspell support
libatm1-dev - Development files for compiling ATM programs
libatomic-ops-dev - A library for atomic operations (development files)
libattr1-dev - Extended attribute static libraries and headers
libaudiofile-dev - Open-source version of SGI's audiofile library (header files)
libavc1394-dev - control IEEE 1394 audio/video devices (development files)
libbeecrypt6-dev - header files for beecrypt, a library of cryptographic algorithms
libblkid-dev - block device id library - headers and static libraries
libbonobo2-dev - Bonobo CORBA interfaces library -- development files
libboost-doc - Boost.org libraries documentation
libbrlapi1-dev - Library for communication with BRLTTY - static libs and headers
libcaca-dev - development files for libcaca
libcairo-directfb2-dev - Development files for Cairo graphics library DirectFB build
libcairo2-dev - Development files for the Cairo 2D graphics library
libcairomm-1.0-dev - C++ wrappers for Cairo (development files)
libcap-dev - development libraries and header files for libcap
libcdio-dev - library to read and control CD-ROM (development files)
libchicken-dev - Simple Scheme-to-C compiler - development
libcroco3-dev - a generic Cascading Style Sheet (CSS) parsing and manipulation toolkit
libdaemon-dev - lightweight C library for daemons
libdb3-dev - Berkeley v3 Database Libraries [development]
libdb4.4++-dev - Berkeley v4.4 Database Libraries for C++ [development]
libdb4.4-dev - Berkeley v4.4 Database Libraries [development]
libdevmapper-dev - The Linux Kernel Device Mapper header files
libdiscover1-dev - hardware identification library development files
libdm0-dev - Data Management API static libraries and headers
libdmx-dev - X11 Distributed Multihead extension library (development headers)
libdv4-dev - software library for DV format digital video (devel files)
libesd0-dev - Enlightened Sound Daemon - Development files
libestools1.2-dev - Edinburgh Speech Tools Library - developer's libraries and docs
libevent-dev - Development libraries, header files and docs for libevent
libexo-0.3-dev - Development files for libexo0.3-0
libffi4-dev - Foreign Function Interface library (development files)
libfontconfig1-dev - generic font configuration library - development
libfontenc-dev - X11 font encoding library (development headers)
libfribidi-dev - Development files for FreeBidi library
libfs-dev - X11 Font Services library (development headers)
libg2c0-dev - GNU Fortran 77 library development
libgcj7-dev - Java development headers and static library for use with gcj
libgcompris-1-dev - Core gcompris functionality - development files
libgconf2-dev - GNOME configuration database system (development)
libgcrypt11-dev - LGPL Crypto library - development files
libgda2-dev - Development files for GNOME Data Access library for GNOME2
libgdome2-dev - Development files for libgdome2
libgl1-mesa-dev - A free implementation of the OpenGL API -- GLX development support files
libgl1-mesa-swx11-dev - A free implementation of the OpenGL API -- development support files
libgle3-dev - OpenGL tubing and extrusion library development files
libglew-dev - The OpenGL Extension Wrangler - development environment
libglib1.2-dev - Development files for GLib library
libglib2.0-dev - Development files for the GLib library
libglitz-glx1-dev - Glitz OpenGL library GLX backend development libraries and headers
libglitz1-dev - OpenGL image compositing library development libraries and headers
libglu1-mesa-dev - The OpenGL utility library -- development support files
libglut3-dev - development libraries and headers for GLUT
libgmp3-dev - Multiprecision arithmetic library developers tools
libgnome-mag-dev - screen magnification library for the GNOME desktop (development headers)

```

I'm having to break it up due to max text cap.

Next post to have rest.

Stormweaver

---

### Post by Stormweaver on 2007-04-19
```

libgnome-media-dev - development libraries for the GNOME media utilities
libgnome-menu-dev - an implementation of the freedesktop menu specification for GNOME
libgnome-pilot2-dev - Development libraries for gnome-pilot
libgnome-speech3-dev - GNOME text-to-speech library (development headers)
libgnomecups1.0-dev - GNOME library for CUPS interaction (headers)
libgnomecupsui1.0-dev - UI extensions to libgnomecups (headers)
libgnomedb2-dev - Database UI widget library for GNOME2 -- development files
libgpg-error-dev - library for common error values and messages in GnuPG components
libgsl0-dev - GNU Scientific Library (GSL) -- development package
libgsm1-dev - Development libraries for a GSM speech compressor
libgssapi-dev - header files and docs for libgssapi
libgtk1.2-dev - Development files for the GIMP Toolkit
libgtksourceview-dev - development files for the GTK+ syntax highlighting widget
libgtkspell-dev - Development files for GtkSpell
libgucharmap5-dev - Unicode browser widget library (development headers)
libgutenprint-dev - development files for the Gutenprint printer driver library
libgutenprintui2-dev - development files for the Gutenprint printer driver user interface library
libhfsp-dev - library to access HFS+ formatted volumes
libice-dev - X11 Inter-Client Exchange library (development headers)
libid3-3.8.3-dev - ID3 Tag Library: Development Libraries and Header Files.
libidl-dev - development files for programs that use libIDL
libijs-dev - IJS raster image transport protocol: development files
libiw-dev - Wireless tools - development files
libjasper-1.701-dev - Development files for the JasPer JPEG-2000 library
libjpeg62-dev - Development files for the IJG JPEG library
libkcal2-dev - KDE calendaring library [development]
libkdegames-dev - KDE games library headers
libkdepim1-dev - KDE PIM library [development]
libkgantt0-dev - KDE gantt charting library [development]
libkjsembed-dev - Embedded JavaScript library (Development files)
libkleopatra1-dev - KDE GnuPG interface libraries [development]
libklibc-dev - kernel headers used during the build of klibc
libkpathsea-dev - path search library for teTeX (devel part)
libkpimexchange1-dev - KDE PIM Exchange library [development]
libksieve0-dev - KDE mail/news message filtering library [development]
libktnef1-dev - KTNEF handler library [development]
liblaunchpad-integration-dev - library for launchpad integration
liblcms1-dev - Color management library (Development headers)
liblockdev1-dev - Development library for locking devices
liblockfile-dev - Development library for liblockfile.
liblpint-bonobo-dev - library for launchpad integration
libltdl3-dev - A system independent dlopen wrapper for GNU libtool
liblua50-dev - Main interpreter library for Lua 5.0: static library and headers
liblualib50-dev - Extension library for Lua 5.0: static and headers
liblzo-dev - data compression library (old version) (development files)
libmhash-dev - Library for cryptographic hashing and message authentication
libmikmod2-dev - A portable sound library - development files
libmimelib1-dev - KDE mime library [development]
libmng-dev - M-N-G library (Development headers)
libmodplug-dev - development files for mod music based on ModPlug
libmpfr-dev - multiple precision floating-point computation developers tools
libmusicbrainz4-dev - Second generation incarnation of the CD Index - development
libmyspell-dev - MySpell spellchecking library development files
libnasl-dev - Nessus Attack Scripting Language, static library and headers
libnautilus-burn-dev - Nautilus Burn Library - development version
libncurses5-dev - Developer's libraries and docs for ncurses
libncursesw5-dev - Developer's libraries for ncursesw
libnessus-dev - Nessus static libraries and headers
libnetpbm10-dev - Development libraries and header files
libnewt-dev - Developer's toolkit for newt windowing library
libnfsidmap-dev - header files and docs for libnfsidmap
libnjb-dev - Creative Labs Nomad Jukebox library development files
libnl-dev - Development library and headers for libnl
libnm-util-dev - network management framework (development files)
libogg-dev - Ogg Bitstream Library Development
liboil0.3-dev - Library of Optimized Inner Loops (development headers)
liboobs-1-dev - wrapping library to the System Tools Backends - header files
libopal-dev - OPAL library header files
libopenais-dev - standards-based cluster framework (developer files)
libopencdk8-dev - Open Crypto Development Kit (OpenCDK) (development files)
libopenexr-dev - development files for the OpenEXR image library
libopenexr2c2a - runtime files for the OpenEXR image library
libopts25 - automated option processing library based on autogen - runtime
libopts25-dev - automated option processing library based on autogen - development
liborbit2-dev - development files for ORBit2 - a CORBA ORB
libpam0g-dev - Development files for PAM
libpango1.0-dev - Development files for the Pango
libparted1.7-dev - The GNU Parted disk partitioning library development files
libpcap0.7-dev - Development library and header files for libpcap 0.7
libpcap0.8-dev - Development library and header files for libpcap 0.8
libpisock-dev - development files for communicating with a PalmOS PDA
libpopt-dev - lib for parsing cmdline parameters - development files
libproc-dev - library for accessing process information from /proc
libpspell-dev - Development files for applications with pspell support
libpt-dev - Portable Windows Library development files
libqscintilla-dev - Qt source code editing component - development files
libqt4-dev - Qt 4 development files
libquicktime-dev - header files for developing applications with quicktime
libraptor1-dev - Raptor RDF parser and serializer development libraries and headers
librasqal0-dev - Rasqal RDF query library development libraries and headers
librdf0-dev - Redland RDF library development libraries and headers
librecode-dev - Development package for librecode0
librpcsecgss-dev - header files and docs for librpcsecgss
libsamplerate0-dev - development files for audio rate conversion (libsamplerate)
libscim-dev - development library for SCIM platform
libselinux1-dev - SELinux development headers
libsensors-dev - lm-sensors development kit
libsepol1-dev - Security Enhanced Linux policy library and development files
libsexy-dev - collection of additional GTK+ widgets - header files
libshout3-dev - MP3/Ogg Vorbis broadcast streaming library (development)
libskim-dev - skim development library
libslp-dev - OpenSLP development libraries
libsm-dev - X11 Inter-Client Exchange library (development headers)
libsmpeg-dev - SDL MPEG Player Library - development files
libsndfile1 - Library for reading/writing audio files
libsnmp9-dev - NET SNMP (Simple Network Management Protocol) Development Files
libsqlite0-dev - SQLite development files
libsqlite3-dev - SQLite 3 development files
libstartup-notification0-dev - library for program launch feedback (development headers)
libstdc++5-3.3-dev - The GNU Standard C++ Library v3 (development files)
libstonith-dev - Interface for remotely powering down a node in the cluster
libsysfs-dev - interface library to sysfs - development files
libt1-dev - Type 1 font rasterizer library - development
libtag1-dev - TagLib Audio Meta-Data Library [development]
libtagc0-dev - TagLib Audio Meta-Data Library (C bindings) [development]
libtasn1-3-dev - Manage ASN.1 structures (development)
libthai-dev - Development files for Thai language support library
libtheora-dev - The Theora Video Compression Codec (development files)
libtheora0 - The Theora Video Compression Codec
libthunar-vfs-1-dev - Development files for libthunar-vfs
libtiff4-dev - Tag Image File Format library (TIFF), development files
libttf-dev - FreeType 1 development files (static library and headers)
libtunepimp3-dev - MusicBrainz tagging library -- development files
libtut-dev - elegant C++ unit test framework
libungif4-dev - shared library for GIF images (development files)
libvisual-0.4-dev - Audio visualization framework (development package)
libvncauth-dev - Virtual network computing authentication headers and static lib
libvorbis-dev - The Vorbis General Audio Compression Codec (development files)
libwmf-dev - Windows metafile conversion development
libwnck-dev - Window Navigator Construction Kit - development files
libwvstreams-dev - Development libraries and header files for libwvstreams4.2
libxau-dev - X11 authorisation library (development headers)
libxaw-headers - X11 Athena Widget library (development headers)
libxaw7-dev - X11 Athena Widget library (development headers)
libxcomposite-dev - X11 Composite extension library (development headers)
libxcursor-dev - X cursor management library (development files)
libxdamage-dev - X11 damaged region extension library (development headers)
libxdmcp-dev - X11 authorisation library (development headers)
libxevie-dev - X11 EvIE extension library (development headers)
libxext-dev - X11 miscellaneous extensions library (development headers)
libxfce4util-dev - Development files for libxfce4util
libxfcegui4-dev - Development files for libxfcegui4-4
libxfixes-dev - X11 miscellaneous 'fixes' extension library (development headers)
libxft-dev - FreeType-based font drawing library for X (development files)
libxi-dev - X11 Input extension library (development headers)
libxinerama-dev - X11 Xinerama extension library (development headers)
libxkbfile-dev - X11 keyboard file manipulation library (development headers)
libxkbui-dev - X11 keyboard UI presentation library (development headers)
libxklavier-dev - Development files for libxklavier
libxmlsec1-dev - Development files for the XML security library
libxmu-dev - X11 miscellaneous utility library (development headers)
libxmu-headers - X11 miscellaneous utility library headers
libxmuu-dev - X11 miscellaneous micro-utility library (development headers)
libxp-dev - X Printing Extension (Xprint) client library (development files)
libxplc0.3.13-dev - Light weight component system (Development libraries and headers)
libxpm-dev - X11 pixmap library (development headers)
libxrandr-dev - X11 RandR extension library (development headers)
libxrender-dev - X Rendering Extension client library (development files)
libxres-dev - X11 Resource extension library (development headers)
libxss-dev - X11 Screen Saver extension library (development headers)
libxt-dev - X11 toolkit intrinsics library (development headers)
libxtrap-dev - X11 event trapping extension library (development headers)
libxtst-dev - X11 Record extension library (development headers)
libxv-dev - X11 Video extension library (development headers)
libxvmc-dev - X11 Video extension library (development headers)
libxxf86dga-dev - X11 Direct Graphics Access extension library (development headers)
libxxf86misc-dev - X11 XFree86 miscellaneous extension library (development headers)
libxxf86vm-dev - X11 XFree86 video mode extension library (development headers)
mesa-common-dev - Developer documentation for Mesa
nessus-dev - Nessus development header files
network-manager-dev - network management framework (development files)
pciutils-dev - Linux PCI Utilities (development files)
ppp-dev - Selected headers from the ppp package
python-dev - Header files and a static library for Python (default)
python-egenix-mx-base-dev - development files for the egenix-mx-base distribution
python2.4-dev - Header files and a static library for Python (v2.4)
python2.5-dev - Header files and a static library for Python (v2.5)
qobex-dev - Swiss army knife for obex testing/development
ss-dev - command-line interface parsing library - headers and static libraries
tcl8.3-dev - Tcl (the Tool Command Language) v8.3 - development files
tcl8.4-dev - Tcl (the Tool Command Language) v8.4 - development files
tk8.3-dev - Tk toolkit for Tcl and X11, v8.3 - development files
tk8.4-dev - Tk toolkit for Tcl and X11, v8.4 - development files
unixodbc-dev - ODBC libraries for UNIX (development files)
uuid-dev - universally unique id library - headers and static libraries
x11proto-core-dev - X11 core wire protocol and auxiliary headers
x11proto-fonts-dev - X11 font extension wire protocol
xfce4-mcs-manager-dev - Development files and static plugins
xfslibs-dev - XFS filesystem-specific static libraries and headers
zsh-dev - A shell with lots of features (development files)
evolution-data-server-dev - Development files for evolution-data-server (meta package)
kdebase-dev - development files for the KDE base module
kopete-dev - development files for the KDE instant messenger, Kopete
libc6-dev - GNU C Library: Development Libraries and Header Files
libcamel1.2-dev - Development files for libcamel
libebook1.2-dev - Client library for evolution address books (development files)
libecal1.2-dev - Client library for evolution calendars (development files)
libedata-book1.2-dev - Backend library for evolution address books (development files)
libedata-cal1.2-dev - Backend library for evolution calendars (development files)
libedataserver1.2-dev - Utility library for evolution data servers (development files)
libedataserverui1.2-dev - GUI utility library for evolution data servers (development files)
libegroupwise1.2-dev - Development files for libegroupwise
libexchange-storage1.2-dev - Backend library for evolution calendars (development files)
libgimp2.0-dev - Headers and other files for compiling plugins for The GIMP
libgnome-window-settings-dev - Utility library for getting window manager settings (headers)
libgnomeprintui2.2-dev - GNOME 2.2 print architecture User Interface - devel files
libkonq4-dev - development files for Konqueror's core libraries
libmysqlclient15-dev - mysql database development files
libtotem-plparser-dev - Totem Playlist Parser library - development version
libvolumeid-dev - volume identification library (development files)
xorg-dev - the X.Org X Window System development libraries
evolution-dev - Development library files for Evolution
firefox-dev - Development files for Mozilla Firefox
kdelibs4-dev - development files for the KDE core libraries
libaudio-dev - The Network Audio System (NAS). (development files)
libavahi-client-dev - Development files for the Avahi client library
libavahi-common-dev - Development files for the Avahi common library
libavahi-compat-libdnssd-dev - Development headers for the Avahi Apple Bonjour compatibility library
libavahi-glib-dev - Development headers for the Avahi glib integration library
libavahi-qt3-dev - Development headers for the Avahi QT3 integration library
libavahi-qt4-dev - Development headers for the Avahi QT4 integration library
libbind-dev - Static Libraries and Headers used by BIND
libdbus-1-dev - simple interprocess messaging system (development headers)
libfreetype6-dev - FreeType 2 font engine, development files
libgpgme11-dev - GPGME - GnuPG Made Easy
libgtk2.0-dev - Development files for the GTK+ library
libgtop2-dev - gtop system monitoring library
libimlib2-dev - Imlib2 development files
libkrb5-dev - Headers and development libraries for MIT Kerberos
libmagick9-dev - Image manipulation library -- development
libmono-dev - libraries for the Mono JIT - Development files
libmythes-dev - simple thesaurus library (development files)
libpng12-dev - PNG library - development
libpoppler-dev - PDF rendering library -- development files
libqt3-compat-headers - Qt 1.x and 2.x compatibility includes
libqt3-headers - Qt3 header files
libqt3-mt-dev - Qt development files (Threaded)
librpm-dev - RPM shared library, development kit
libsmbclient-dev - libsmbclient static libraries and headers
libwv-dev - Development files for the wvWare library
libx11-dev - X11 client-side library (development headers)
libxfont-dev - X11 font rasterisation library (development headers)
libxine-dev - the xine video player library, development packages
linux-headers-2.6.17-10 - Header files related to Linux kernel version 2.6.17
linux-headers-2.6.17-10-386 - Linux kernel headers for version 2.6.17 on i386
linux-headers-2.6.17-10-generic - Linux kernel headers for version 2.6.17 on x86/x86_64
linux-headers-2.6.17-10-server - Linux kernel headers for version 2.6.17 on x86/x86_64
linux-headers-2.6.17-10-server-bigiron - Linux kernel headers for version 2.6.17 on BigIron Server Equipment
linux-headers-2.6.17-11 - Header files related to Linux kernel version 2.6.17
linux-headers-2.6.17-11-386 - Linux kernel headers for version 2.6.17 on i386
linux-headers-2.6.17-11-generic - Linux kernel headers for version 2.6.17 on x86/x86_64
linux-headers-2.6.17-11-server - Linux kernel headers for version 2.6.17 on x86/x86_64
linux-headers-2.6.17-11-server-bigiron - Linux kernel headers for version 2.6.17 on BigIron Server Equipment
linux-headers-386 - Linux kernel headers on 386
linux-headers-686 - Obsoleted by: linux-headers-generic
linux-headers-generic - Generic Linux kernel headers
linux-headers-k7 - Obsoleted by: linux-headers-generic
linux-headers-server - Linux kernel headers on Server Equipment.
linux-headers-server-bigiron - Linux kernel headers on BigIron Server Equipment.
linux-libc-dev - Linux Kernel Headers for development
linux-source-2.6.17 - Linux kernel source for version 2.6.17 with Ubuntu patches
postgresql-server-dev-8.1 - development files for PostgreSQL 8.1 server-side programming
ruby1.8-dev - Header files for compiling extension modules for the Ruby 1.8
tcpdump - A powerful tool for network monitoring and data acquisition
xmms-dev - XMMS development static library and header files
xserver-xorg-dev - X.Org X server -- development files
liblircclient-dev - development files for LIRC client library
libpq-dev - header files for libpq5 (PostgreSQL library)
mutt - text-based mailreader supporting MIME, GPG, PGP and threading
postgresql-server-dev-8.2 - development files for PostgreSQL 8.2 server-side programming
libexiv2-dev - EXIF/IPTC metadata manipulation library - development files
libvlc0-dev - development files for VLC
spamassassin - Perl-based spam filter using text analysis
wx2.6-headers - wxWidgets Cross-platform C++ GUI toolkit (header files)
asterisk-dev - development files for asterisk
kdenetwork-dev - development files for the KDE network module
libavahi-compat-howl-dev - Development headers for the Avahi Howl compatibility library
libclamav-dev - clam Antivirus library development files
a2ps - GNU a2ps - 'Anything to PostScript' converter and pretty-printer
acpidump - utilities to dump system's ACPI tables to an ASCII file
affix-headers - Header files of the Affix Bluetooth protocol stack for Linux
afio - archive file manipulation program
alsa-source - ALSA driver sources
altermime - utility used to alter mime-encoded mailpacks
aolserver4-dev - AOL Web Server 4 (Development Tools)
apache-dev - development kit for the Apache webserver
apcalc-dev - Library for arbitrary precision arithmetic
araneida - A programmable web server written and extended in Lisp
archmbox - a simple email archiver written in perl
atlas3-headers - Automatically Tuned Linear Algebra Software,C header files
aub - Assembles binary files from USENET
avr-libc - Standard C library for Atmel AVR development
bake - yet another Make replacement (python)
bash-builtins - Bash loadable builtins - headers & examples
beep-media-player-dev - Beep Media Player development static library and header files
biosquid-dev - headers and static library for biological sequence analysis
bitchx-dev - Header files for BitchX
blitz++ - C++ template class library for scientific computing
boinc-dev - development files to build applications for BOINC projects
c2hs - C->Haskell Interface Generator
c2hs-doc - C->Haskell Interface Generator -- Documentation package
c2n - Tape transfer utility for CBM/Oric-1 machines
cernlib-core-dev - Cernlib development headers, tools, and static libraries
cfortran - Header file permitting Fortran routines to be called in C/C++
checkmp3 - identify MP3s that do not follow the MP3 format
chktex - Finds typographic errors in LaTeX
cimg-dev - powerful image processing library
cjet - Software PCL emulation for Canon CaPSL laser printers
cl-rfc2388 - an implementation of RFC 2388 in Common Lisp
clearsilver-dev - headers and static library for clearsilver
comedi-source - Comedi kernel module source
compface - Compress/decompress images for mailheaders, user tools
courier-filter-perl - purely Perl-based mail filter framework for the Courier MTA
cpad-kernel-dev - kernel header for the Synaptics cPad driver
cpad-kernel-source - source for the Synaptics cPad driver
cscope - Interactively examine a C program source
ctn-dev - Development files for Central Test Node, a DICOM implementation
cxref - Generates latex and HTML documentation for C programs
cyrus-dev-2.2 - Cyrus mail system (developer files)
cyrus21-dev - Cyrus mail system (developer files)
dazuko-source - source for the Dazuko driver
distcc - Simple distributed compiler client and server
distccmon-gnome - GTK monitor for distcc a distributed client and server
doc++ - A documentation system for C/C++, IDL and Java
dpkg-cross - tools for cross compiling Debian packages
drac-dev - Dynamic Relay Authorization Control (development files)
dssi-dev - Header file for compiling DSSI plugins and hosts
dvhtool - Manipulate the volume header on sgi partition layouts
easytag - viewing, editing and writing ID3 tags
elks-libc - 16-bit C library and include files
elvis-tools - text editing tools for programmers (elvfmt, elvtags, ref)
fblogo - Converts images to framebuffer-logo header file
fftw-dev - library for computing Fast Fourier Transforms
fftw2 - library for computing Fast Fourier Transforms
firebird2-dev - Development files for Firebird - an RDBMS based on InterBase 6.0 code
firefox-webdeveloper - web developer extension for the Firefox web browser
fixincludes - Fix non-ANSI header files
flow-tools-dev - development files for flow-tools
foremost - Forensics application to recover data
freecell-solver-bin - Library for solving Freecell games
freetable - Facilitates production of HTML tables
ftjam - FreeType version of Jam, a replacement for make
gap-dev - GAP computer algebra system, compiler and development files
gbuffy - A GTK+-based, XBuffy-like multiple mailbox "biff" program
gcx - astronomical image processing and photometry gtk+ application
gdk-imlib11-dev - Header files needed for Gdk-Imlib development
genisovh - Make CD-ROMs bootable for SGI MIPS machines
giblib-dev - headers for giblib
giflib3g-dev - shared library for GIF images (development files)
gmpc-dev - Gnome Music Player Client (plugin development files)
gnubiff - A mail notification program for GNOME (and others)
gnus-bonus-el - Miscellaneous add-ons for Gnus
gpib-modules-source - kernel modules for various GPIB boards
gpsim-dev - Libraries needed only for building gpsim components
grepmail - search mailboxes for mail matching an expression
gromacs-dev - GROMACS molecular dynamics sim, development kit
happycoders-libdbg-dev - C++ utilities to facilitate modern debugging idioms
happycoders-libsocket-dev - Generic C++ library that implement Udp/Tcp socket interface
hbf-cns40-1 - Chinese Fanti Song 40x40 bitmap font (CNS plane 1) for CJK
hbf-cns40-2 - Chinese Fanti Song 40x40 bitmap font (CNS plane 2) for CJK
hbf-cns40-3 - Chinese Fanti Song 40x40 bitmap font (CNS plane 3) for CJK
hbf-cns40-4 - Chinese Fanti Song 40x40 bitmap font (CNS plane 4) for CJK
hbf-cns40-5 - Chinese Fanti Song 40x40 bitmap font (CNS plane 5) for CJK
hbf-cns40-6 - Chinese Fanti Song 40x40 bitmap font (CNS plane 6) for CJK
hbf-cns40-7 - Chinese Fanti Song 40x40 bitmap font (CNS plane 7) for CJK
hbf-cns40-b5 - Chinese Fanti Song 40x40 bitmap font (Big5) for CJK
hbf-jfs56 - Chinese Jianti Fangsong 56x56 bitmap font (GB2312) for CJK
hbf-kanji48 - Japanese Kanji 48x48 bitmap font (JIS X-0208) for CJK
headache - Tool to manage license notes of source files
httping - ping-like program for http-requests
hybrid-dev - development files for ircd-hybrid
ieee80211-source - Source for the 802.11 (wireless) network stack for Linux
imageindex - generate static HTML galleries from images
imapsync - IMAP synchronization, copy and migration tool
imlib11-dev - Imlib is an imaging library for X and X11
inn2-dev - The libinn.a library, headers and man pages
insserv - Reorder boot sequence based on LSB init.d script dependencies
ipgrab - Tcpdump-like utility that prints detailed header information
itcl3-dev - [incr Tcl] OOP extension for Tcl - development files
itk3-dev - [incr Tk] OOP extension for Tk - development files
jabber-dev - Daemon for the jabber.org Open Source Instant Messenger
jam - Software-build tool, replacement for make
jhead - manipulate the non-image part of Exif compliant JPEG files
k3d-dev - 3D modeling and animation system - Development files
k6fftwgel-dev - library for computing Fast Fourier Transforms on AMD K6-2
k6fftwgel2 - library for computing Fast Fourier Transforms on AMD K6-2
k7fftwgel-dev - library for computing Fast Fourier Transforms on AMD K7
k7fftwgel2 - library for computing Fast Fourier Transforms on AMD K7
kaffe-dev - Header files and other resources for building against Kaffe
kannel-dev - WAP and SMS gateway headers and development files
kboincspy-dev - development files for KBoincSpy plugins
kde-devel - the K Desktop Environment development files and modules
kde4base-dev - development files for the KDE 4 testing applications
kdegraphics-dev - development files for the KDE graphics module
kdelibs5-dev - development files for the KDE 4 testing core libraries
kdepimlibs4-dev - development files for the KDE PIM 4 testing core libraries
kdesdk-misc - various goodies from the KDE Software Development Kit
kernel-build-2.4.27-2 - Headers for building modules for Linux 2.4.27
kernel-headers-2.4.27-2 - Header files related to Linux kernel version 2.4.27
kernel-headers-2.4.27-2-386 - Linux 2.4.27 kernel headers for 386
kernel-headers-2.4.27-2-586tsc - Linux 2.4.27 kernel headers for Pentium-Classic
kernel-headers-2.4.27-2-686 - Linux 2.4.27 kernel headers for PPro/Celeron/PII/PIII/P4
kernel-headers-2.4.27-2-686-smp - Linux 2.4.27 kernel headers for PPro/Celeron/PII/PIII/P4 SMP
kernel-headers-2.4.27-2-k6 - Linux 2.4.27 kernel headers for AMD K6/K6-II/K6-III
kernel-headers-2.4.27-2-k7 - Linux 2.4.27 kernel headers for AMD K7
kernel-headers-2.4.27-2-k7-smp - Linux 2.4.27 kernel headers for AMD K7 SMP
kernel-source-2.4.27 - Linux kernel source for version 2.4.27 with Debian patches
klibido - usenet binary grabber for KDE
ksimus-dev - KSimus development header files
kvirc2-dev - Development files for KVIrc
lam4-dev - Development of parallel programs using LAM
lcrash-dev - development files required to analyze LKCD kernel crash dumps
lesstif-dev - development library and header files for LessTif 1.2
lesstif2-dev - development library and header files for LessTif 2.1
libace-dev - An Object-Oriented Network Programming Toolkit in C++
libacexml-dev - ACE XML PARSER Framework (development files)
libadasockets0-dev - bindings for socket services in Ada
libadolc-dev - ADOLC development libs and headers
libaldmb1-dev - development files for libaldmb1
libalps-heap1-dev - ALPS Physics Simulation Algorithms (heap development files)
libalps-light1-dev - ALPS Physics Simulation Algorithms (light library development files)
libalps-mpi1-dev - ALPS Physics Simulation Algorithms (MPI development files)
libalps-pvm1-dev - ALPS Physics Simulation Algorithms (PVM development files)
libalps-sgl1-dev - ALPS Physics Simulation Algorithms (SGL development files)
libaltlinuxhyph-dev - ALTLinux hyphenation library development files
libalut-dev - OpenAL Utility Toolkit development files
libannodex0-dev - annotated and indexed media library (develoment files)
libanydata-perl - simple tied hash interface for files and data structures
libapache-mod-auth-useragent - blocks parts of service for certain user agents
libapache-mod-cgi-debug - Easier debugging of CGI scripts
libapache-mod-choke - concurrent connections per IP and data transfer rate limiter for Apache
libapache-mod-encoding - Apache module for non-ascii filename interoperability
libapache-mod-layout - Apache web page content wrapper
libapache-mod-rpaf - module for Apache which takes the last IP from the 'X-Forwarded-For' header
libapache-modxslt - XSLT processing module for Apache based on libxml2
libapache2-mod-encoding - Apache2 module for non-ascii filename interoperability
libapache2-mod-layout - Apache2 web page content wrapper
libapache2-mod-proxy-html - Apache2 filter module for HTML links rewriting
libapache2-mod-rpaf - module for Apache2 which takes the last IP from the 'X-Forwarded-For' header
libapache2-modxslt - XSLT processing module for Apache 2.0.x based on libxml2
libapr1-dbg - The Apache Portable Runtime Library - Development Headers
libapr1-dev - The Apache Portable Runtime Library - Development Headers
libapr1.0-dbg - The Apache Portable Runtime Library - Development Headers
libapr1.0-dev - The Apache Portable Runtime Library - Development Headers
libapreq2-dev - generic Apache request library - development files
libaprutil1-dbg - The Apache Portable Runtime Utility Library - Development Headers
libaprutil1-dev - The Apache Portable Runtime Utility Library - Development Headers
libaprutil1.0-dbg - The Apache Portable Runtime Utility Library - Development Headers
libaprutil1.0-dev - The Apache Portable Runtime Utility Library - Development Headers
libarkrpg-dev - development headers for Arkrpg
libasis-dev - Ada Semantic Interface Specification (ASIS) headers and libraries
libassa3.4-0-dev - object-oriented C++ networking library
libast2-dev - libast2 development files
libastro-fits-header-perl - Perl tools for reading, modifying and writing FITS headers
libatlas-cpp-0.6-dev - The protocol library of the World Forge project - header files
libaudiere-dev - a portable, high-level audio library (development files)
libaudio-flac-header-perl - Perl interface to FLAC file header metadata
libautotrace-dev - bitmap to vector graphics converter, development files
libavcodec-dev - development files for libavcodec
libavformat-dev - development files for libavformat
libavifile-0.7-dev - development header files for libavifile
libavl-dev - AVL tree manipulation library - development
libbitcollider-dev - bitcollider library headers
libbtparse-dev - A C library to parse BibTeX files - development files
libbuffy-dev - Base functions for building mailbox summary applications
libc-client-dev - UW c-client library for mail protocols
libcanlock2-dev - development files for Usenet cancel lock library
libcanna1g-dev - Canna Static Library and Headers
libcapsinetwork-dev - C++ network server library, development files
libccaudio2-dev - header files and static link library for GNU ccAudio
libcddb2-dev - library to access CDDB data - development files
libcdio-cdda-dev - library to read and control digital audio CDs (development files)
libcdio-paranoia-dev - library to read digital audio CDs with error correction (development files)
libcdk-dev - C-based curses widget library (development files)
libcdk5-dev - C-based curses widget library (development files)
libcgi-dev - library for CGI programs in C
libcgi-simple-perl - A Simple totally OO CGI interface that is CGI.pm compliant
libcgicg1-dev - C library for developing CGI applications
libchasen-dev - a Japanese Morphological Analysis System (libraries and headers)
libcherokee-base0-dev - extremely fast and flexible web server - development files
libcherokee-client0-dev - extremely fast and flexible web server - development files
libcherokee-server0-dev - extremely fast and flexible web server - development files
libchm-dev - library for dealing with Microsoft CHM format files
libciao-dev - CIAO, TAO's implementation of CORBA Component Model (CCM)
libclips-dev - CLIPS shared libraries
libcln-dev - Development library for Class Library for Numbers (c++)
libclucene-dev - library for full-featured text search engine (development)
libclutils0-dev - Development files needed to compile programs that use clutils.
libcm7 - Support code for compositing managers - development files
libcmml1-dev - Continuous Media Markup Language document handler (development files)
libcojets2-dev - [Physics] COJETS p-p and pbar-p interaction Monte Carlo
libcomedi-dev - Development library for Comedi
libcommoncpp2-dev - Header files and static libraries for Common C++ "2"
libcompfaceg1 - Compress/decompress images for mailheaders, libc6 runtime
libcompfaceg1-dev - Compress/decompress images for mailheaders, libc6 devel
libconfuse-dev - Development files for libConfuse
libcppopt-dev - C++ option parsing library header files
libcriawips-dev - libraries necessary to run criawips, headers
libcriawipshelper-dev - helper libraries necessary to run criawips, headers
libcrypto++-dev - General purpose cryptographic C++ library - development
libctl-dev - Library for flexible control files, development version
libcv-dev - development files for libcv
libcvaux-dev - development files for libcvaux
libcwnn-dev - Header files and static library for cWnn (FreeWnn cserver)
libdb2-dev - The Berkeley database routines (development files)
libdbaudiolib0-dev - Communicate to the DBMix audio system (development files)
libdbi0-dev - Database Independent Abstraction Layer for C (dev files)
libdcmtk1-dev - The OFFIS DICOM toolkit development libraries and headers
libdianewcanvas2-dev - a gtk+2 vectorial canvas with extra features
libdiscover-dev - hardware identification library development files
libdjbdns1-dev - DNS client library designed to replace the BIND res_*/dn_* library
libdnet-dev - DECnet development libraries & Headers
libdockapp-dev - Window Maker Dock App support (development files)
libdspam7-dev - DSPAM is a scalable and statistical anti-spam filter
libdts-dev - development files for libdts
libdumb1-dev - development files for libdumb1
libdumbnet-dev - Development libraries, header files and docs for libdumbnet
libdvb-dev - library to tune and command Digital Video Broadcasting cards
libdvbpsi3-dev - development files for libdvbpsi3
libdvbpsi4-dev - development files for libdvbpsi4
libdvdnav-dev - The DVD navigation library, development package
libdvdplay0-dev - development files for libdvdplay0
libdx4-dev - OpenDX (IBM Visualization Data Explorer) - development files
libebml-dev - access library for the EBML format
libeditline-dev - development files for libeditline
libelfsh0-dev - The ELF shell library
libelk0-dev - development files for libelk0
libemail-date-perl - Perl module for correct formatting of dates in emails
libemail-messageid-perl - Generate world unique message-ids.
libemail-mime-contenttype-perl - Parse a MIME Content-Type Header
libemail-mime-encodings-perl - A unified interface to MIME encoding and decoding
libemail-mime-perl - Easy MIME message parsing module for Perl
libemail-simple-perl - Simple parsing of RFC2822 message format and headers
libenca-dev - Extremely Naive Charset Analyser - development files
libendeavour2-dev - file and disk management suite - library headers
libepplet-dev - Development files for Epplets
libeurodec1-dev - [Physics] Monte Carlo library for quark / heavy lepton decays
libexscalibar1-dev - Development files for the Exscalibar libraries
libextutils-xsbuilder-perl - Automatic XS glue code generation
libezv24-dev - ez24V Library: Development library and header files
libf2c2-dev - Development libraries for use with f2c
libfactory++-dev - C++ template factory framework
libfam-dev - Client library to control the FAM daemon - development files
libfann1-dev - Fast Artificial Neural Network Library, Development files
libfcgi-dev - Header files of FastCGI
libfishsound1-dev - simple programming interface that wraps Xiph.Org audio codecs (development files)
libflash-dev - GPL Flash (SWF) Library - development files
libfluidsynth-dev - Real-time MIDI software synthesizer (development files)
libfnlib-dev - header files needed for Fnlib development
libforms-dev - Header files and static libraries for the XForms widget library
libformsgl-dev - Header files and static libraries for the OpenGL XForms library
libfortune-perl - Perl module to read fortune (strfile) databases
libfox1.2-dev - Development files for the FOX C++ GUI Toolkit
libfox1.4-dev - Development files for the FOX C++ GUI Toolkit
libfreecell-solver-dev - Library for solving Freecell games (Development files)
libfreecell-solver0 - Library for solving Freecell games
libfreefem-dev - Development library, header files and manpages
libftdi-dev - Development files for libftdi
libfwbuilder-dev - Firewall Builder API library development files
libfwbuilder6c2a - Firewall Builder API library
libg2-dev - g2 2D graphics library (development files)
libgalago-dev - Libraries and header files for developing against libgalago
libgalago-doc - Libraries and header files for developing against libgalago
libgalago-gtk-dev - libraries and header files for developing against libgalago-gtk
libgammu-dev - Header files for Gammu
libgatos-dev - The General ATI TV and Overlay Software(GATOS): Dev Lib and Headers
libgavl-dev - Gmerlin Audio Video Library
libgcgi-dev - library for CGI programs in C
libgchemutils-dev - GNOME chemistry utils (development version)
libgdal1-1.3.1-dev - Geospatial Data Abstraction Library - Development files

```

That should be the rest.

Thank you for all your help with this, I only hope I can help someone else as much or more in time.

Stormweaver

---

### Post by igknighted on 2007-04-19
linux-headers-server is the one you want.
```
sudo apt-get install linux-headers-server
```

then continue on from the nvidia installer (remember though, not "init 3" , rather "/etc/init.d/gdm stop")

---

### Post by Stormweaver on 2007-04-19
Update:  Success on getting the driver in!

Ok - Graphics are still running choppy, I assume cause I need to edit this file it spoke of, can you guide me through this????


Stormweaver

---

### Post by igknighted on 2007-04-19
> **Stormweaver said:**
> Update:  Success on getting the driver in!

Ok - Graphics are still running choppy, I assume cause I need to edit this file it spoke of, can you guide me through this????


Stormweaver

"sudo nvidia-xconfig" should do it.  then restart X (ctrl-alt-backspc) and you should get an nvidia splash before you get to the login

If you need to enable anything else, like composite for beryl or something, check these are all the commands to change the way your graphics work:
```
nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:38:46 PST
2007
  The NVIDIA X Configuration Tool.

  This program is used to manipulate X configuration files, specifically to
  enable NVIDIA X driver functionality.

  Copyright (C) 2005 NVIDIA Corporation.


  In its normal operation, nvidia-xconfig finds the system X configuration file
  (or generates a new X configuration if it cannot find the system file), makes
  sure the configuration is usable by the NVIDIA X driver, applies any updates
  requested on the commandline, and writes the new configuration to file.

  Please see the NVIDIA README for a description of NVIDIA X configuration file
  options.


nvidia-xconfig [options]

  -c XCONFIG, --xconfig=XCONFIG
      Use XCONFIG as the input X config file; if this option is not specified,
      then the same search path used by the X server will be used to find the X
      configuration file.

  -o OUTPUT-XCONFIG, --output-xconfig=OUTPUT-XCONFIG
      Use OUTPUT-XCONFIG as the output X configuration file; if this option is
      not specified, then the input X configuration filename will also be used
      as the output X configuration filename.

  -s, --silent
      Run silently; no messages will be printed to stdout, except for warning
      and error messages to stderr.

  -t, --tree
      Read the X configuration file, print to stdout the X configuration data
      in a tree format, and exit.

  -v, --version
      Print the nvidia-xconfig version and exit.

  -h, --help
      Print usage information for the common commandline options and exit.

  -A, --advanced-help
      Print usage information for the common commandline options as well as the
      advanced options, and then exit.

  --add-argb-glx-visuals, --no-add-argb-glx-visuals
      Enables or disables support for OpenGL rendering into 32-bit ARGB windows
      and pixmaps.

  --allow-ddcci, --no-allow-ddcci
      Enables or disables DDC/CI support in the NV-CONTROL X extension.

  --allow-dfp-stereo, --no-allow-dfp-stereo
      Enable or disable the "AllowDFPStereo" X configuration option.

  --allow-glx-with-composite, --no-allow-glx-with-composite
      Enable or disable the "AllowGLXWithComposite" X configuration option.

  --bandwidth-test, --no-bandwidth-test
      Disable or enable the "NoBandWidthTest" X configuration option.

  --composite, --no-composite
      Enable or disable the "Composite" X extension.

  --constant-dpi, --no-constant-dpi
      Enable or disable the "ConstantDPI" X configuration option, which
      controls whether the NVIDIA X driver maintains a constant dots per inch
      (DPI) value by recomputing the reported size in millimeters of the X
      screen when XRandR changes the size in pixels of the X screen.

  --custom-edid=CUSTOM-EDID, --no-custom-edid
      Enable or disable the  "CustomEDID" X configuration option; setting this
      option forces the X driver to use the EDID specified in a file rather
      than the display's EDID.

  --dac-8bit, --no-dac-8bit
      Most Quadro parts by default use a 10 bit color look up table (LUT) by
      default; setting this option to TRUE forces these graphics chips to use
      an 8 bit (LUT).

  -d DEPTH, --depth=DEPTH
      Set the default depth to DEPTH; valid values for DEPTH are 8, 15, 16 and
      24.

  --disable-glx-root-clipping, --no-disable-glx-root-clipping
      Disable or enable clipping OpenGL rendering to the root window via the
      "DisableGLXRootClipping" X configuration option.

  --damage-events, --no-damage-events
      Use OS-level events to notify the X server when a direct-rendering client
      has performed rendering that needs to be composited to the screen. 
      Improves performance when using GLX with the composite extension.

  --dynamic-twinview, --no-dynamic-twinview
      Enable or disable support for dynamically configuring TwinView.

  -a, --enable-all-gpus
      Configure an X screen on every GPU in the system.

  --exact-mode-timings-dvi, --no-exact-mode-timings-dvi
      Forces the initialization of the X server with the exact timings
      specified in the ModeLine.

  -E FILE, --extract-edids-from-file=FILE
      Extract any raw EDID byte blocks contained in the specified X log file
      LOG; raw EDID bytes are printed by the NVIDIA X driver to the X log as
      hexidecimal when verbose logging is enabled with the "-logverbose 6" X
      server commandline option.  Any extracted EDIDs are then written as
      binary data to individual files.  These files can later be used by the
      NVIDIA X driver through the "CustomEDID" X configuration option.

  --extract-edids-output-file=FILENAME
      When the '--extract-edids-from-log' option is used, nvidia-xconfig writes
      any extracted EDID to a file, typically "edid.bin" in the current
      directory.  Use this option to specify an alternate filename.  Note that
      nvidia-xconfig, if necessary, will append a unique number to the EDID
      filename, to avoid overwriting existing files (e.g., "edid.bin.1" if
      "edid.bin" already exists).

  --flip, --no-flip
      Enable or disable OpenGL flipping

  --force-generate
      Force generation of a new X config file, ignoring any existing system X
      config file.  This is not typically recommended, as things like the mouse
      protocol, keyboard layout, font paths, etc, are setup by your Unix
      distribution.  While nvidia-xconfig can attempt to infer these values, it
      is best to use your Unix distribution's X config file for the basis of
      anything that nvidia-xconfig creates.

  --force-stereo-flipping, --no-force-stereo-flipping
      Normally, stereo flipping is only performed when a stereo drawable is
      visible. This option forces stereo flipping even when no stereo drawables
      are visible.

  --include-implicit-metamodes, --no-include-implicit-metamodes
      Enable or disable the "IncludeImplicitMetaModes" X configuration option.

  --keyboard=KEYBOARD
      When generating a new X configuration file (which happens when no system
      X configuration file can be found, or the '--force-generate' option is
      specified), use KEYBOARD as the keyboard type, rather than attempting to
      probe the system for the keyboard type.  For a list of possible keyboard
      types, see the '--keyboard-list' option.

  --keyboard-driver=DRIVER
      In most cases nvidia-xconfig can automatically determine the correct
      keyboard driver to use (either 'kbd' or 'keyboard'). Use this option to
      override what nvidia-xconfig detects. Typically, if you are using an
      X.Org X server, use 'kdb'; if you are using an XFree86 X server, use
      'keyboard'.

  --keyboard-list
      Print to stdout the available keyboard types recognized by the
      '--keyboard' option, and then exit.

  --layout=LAYOUT
      The nvidia-xconfig utility operates on a Server Layout within the X
      configuration file.  If this option is specified, the layout named LAYOUT
      in the X configuration file will be used.  If this option is not
      specified, the first Server Layout in the X configuration file is used.

  --load-kernel-module, --no-load-kernel-module
      Allow or disallow NVIDIA Linux X driver module to load the NVIDIA Linux
      kernel module automatically.

  --logo, --no-logo
      Disable or enable the "NoLogo" X configuration option.

  --logo-path=PATH, --no-logo-path
      Set the path to the PNG file to be used as the logo splash screen at X
      server startup.

  --mode=MODE
      Add the specified mode to the mode list.

  --remove-mode=MODE
      Remove the specified mode from the mode list.

  --mouse=MOUSE
      When generating a new X configuration file (which happens when no system
      X configuration file can be found, or the '--force-generate' option is
      specified), use MOUSE as the mouse type, rather than attempting to probe
      the system for the mouse type.  For a list of possible mouse types, see
      the '--mouse-list' option.

  --mouse-list
      Print to stdout the available mouse types recognized by the '--mouse'
      option, and then exit.

  --multigpu=MULTIGPU, --no-multigpu
      Enable or disable MultiGPU.  Valid values for MULTIGPU are 'Off', 
      'Auto', 'AFR', 'SFR', 'AA'.

  --multisample-compatibility, --no-multisample-compatibility
      Enable or disable the use of separate front and back multisample
      buffers.

  --nvagp=NVAGP, --no-nvagp
      Set the NvAGP X config option value.  Possible values are 0 (no AGP), 1
      (NVIDIA's AGP), 2 (AGPGART), 3 (try AGPGART, then try NVIDIA's AGP);
      these values can also be specified as 'none', 'nvagp', 'agpgart', or
      'any'.

  --nvidia-cfg-path=PATH
      The nvidia-cfg library is used to communicate with the NVIDIA kernel
      module to query basic properties of every GPU in the system.  This
      library is typically only used by nvidia-xconfig when configuring
      multiple X screens.  This option tells nvidia-xconfig where to look for
      this library (in case it cannot find it on its own).  This option should
      normally not be needed.

  --only-one-x-screen

  --overlay, --no-overlay
      Enable or disable the "Overlay" X configuration option.

  --cioverlay, --no-cioverlay
      Enable or disable the color index overlay.

  --overlay-default-visual, --no-overlay-default-visual
      Enable or disable the "OverlayDefaultVisual" X configuration option.

  --transparent-index=INDEX, --no-transparent-index
      Pixel to use as transparent when using color index overlays.  Valid
      values for TRANSPARENT-INDEX are 0-255.

  -T, --post-tree
      Like the '--tree' option, but goes through the full process of applying
      any user requested updates to the X configuration, before printing the
      final configuration to stdout in a tree format.  Effectively, this option
      just causes the configuration to be printed to stdout as a tree instead
      of writing the results to file.

  --power-connector-check, --no-power-connector-check
      Disable or enable the "NoPowerConnectorCheck" X configuration option.

  --probe-all-gpus, --no-probe-all-gpus
      Disable or enable the "ProbeAllGpus" X configuration option.

  --query-gpu-info
      Print information about all recognized NVIDIA GPUs in the system.

  --randr-rotation, --no-randr-rotation
      Enable or disable the "RandRRotation" X configuration option.

  --render-accel, --no-render-accel
      Enable or disable the "RenderAccel" X configuration option.

  --render-extension, --no-render-extension
      Disable or enable the "NoRenderExtension" X configuration option.

  --rotate=ROTATE, --no-rotate
      Enable or disable the "Rotate" X configuration option.  Valid values for
      ROTATE are 'normal', 'left', 'CCW', 'inverted', 'right', and 'CW'. 
      Rotation can be disabled 

  --screen=SCREEN
      The nvidia-xconfig utility operates on one or more screens within a
      Server Layout in the X configuration file.  If this option is specified,
      the screen named SCREEN in the X configuration file will be used.  If
      this option is not specified, all screens within the selected Server
      Layout in the X configuration file will be used used.

  --separate-x-screens, --no-separate-x-screens
      A GPU that supports multiple simultaneous display devices can either
      drive these display devices in TwinView, or as separate X screens.  When
      the '--separate-x-screens' option is specified, each GPU on which an X
      screen is currently configured will be updated to have two X screens
      configured.  The '--no-separate-x-screens' option will remove the second
      configured X screen on each GPU.  Please see the NVIDIA README
      description of "Separate X Screens on One GPU" for further details.

  --sli=SLI, --no-sli
      Enable or disable SLI.  Valid values for SLI are 'Off', 'Auto', 'AFR',
      'SFR', 'AA', 'AFRofAA'.

  --stereo=STEREO, --no-stereo
      Enable or disable the stereo mode.  Valid values for STEREO are: 1 (DCC
      glasses), 2 (Blueline glasses), 3 (Onboard stereo), 4 (TwinView clone
      mode stereo), 5 (SeeReal digital flat panel), 6 (Sharp3D digital flat
      panel).

  --twinview, --no-twinview
      Enable or disable TwinView.

  --twinview-orientation=ORIENTATION, --no-twinview-orientation
      Specify the TwinViewOrientation.  Valid values for ORIENTATION are:
      "RightOf" (the default), "LeftOf", "Above", "Below", or "Clone".

  --twinview-xinerama-info, --no-twinview-xinerama-info
      Prohibits providing Xinerama information when in TwinView.

  --twinview-xinerama-info-order=TWINVIEW-XINERAMA-INFO-ORDER,
  --no-twinview-xinerama-info-order
      Enable or disable the "TwinViewXineramaInfoOrder" X configuration option.
      TWINVIEW-XINERAMA-INFO-ORDER is a comma-separated list of display device
      names that describe the order in which TwinViewXineramaInfo should be
      reported.  E.g., "CRT, DFP, TV".

  --ubb, --no-ubb
      Enable or disable the "UBB" X configuration option.

  --use-edid, --no-use-edid
      Enable or disable use of the EDID (Extended Display Identification Data)
      from your display device(s).  The EDID will be used for driver operations
      such as building lists of available modes, determining valid frequency
      ranges, and computing the DPI (Dots Per Inch).  This option defaults to
      TRUE (the NVIDIA X driver will use the EDID, when available).  It is NOT
      recommended that you use this option to globally disable use of the EDID;
      instead, use '--no-use-edid-freqs' or '--no-use-edid-dpi' to disable
      specific uses of the EDID.

  --use-edid-dpi, --no-use-edid-dpi
      Enable or disable use of the physical size information in the display
      device's EDID, if any, to compute the DPI (Dots Per Inch) of the X
      screen.  This option defaults to TRUE (the NVIDIA X driver uses the
      EDID's physical size, when available, to compute the DPI).

  --use-edid-freqs, --no-use-edid-freqs
      Enable or disable use of the HorizSync and VertRefresh ranges given in a
      display device's EDID, if any.  EDID provided range information will
      override the HorizSync and VertRefresh ranges specified in the Monitor
      section.  This option defaults to TRUE (the NVIDIA X driver will use
      frequency information from the EDID, when available).

  --use-int10-module, --no-use-int10-module
      Enable use of the X Int10 module to soft-boot all secondary cards, rather
      than POSTing the cards through the NVIDIA kernel module.

  --use-display-device=DISPLAY-DEVICE, --no-use-display-device
      Force the X driver to use the display device specified.

  --virtual=WIDTHxHEIGHT, --no-virtual
      Specify the virtual screen resolution.

  --x-prefix=X-PREFIX
      The X installation prefix; the default is /usr/X11R6/.  Only under rare
      circumstances should this option be needed.

  --xinerama, --no-xinerama
      Enable or disable Xinerama.

  --xvmc-uses-textures, --no-xvmc-uses-textures
      Forces XvMC to use the 3D engine for XvMCPutSurface requests rather than
      the video overlay.
```

---

### Post by Stormweaver on 2007-04-19
Ok I know I did something wrong... Just don't know what.


stormweaver@Eye-of-the-Storm:~$ sudo nvidia-xconfig
Password:
sudo: nvidia-xconfig: command not found
stormweaver@Eye-of-the-Storm:~$ 




So.. Any ideas of what I goofed up now?? LOL wow.. I'm thinking I did not have a strong basis in computers after all. :)

Stormweaver

---

### Post by igknighted on 2007-04-19
hmm, try open xorg.conf with this command:
```
gksudo gedit /etc/X11/xorg.conf
```
find the section "Device".  There will be a line saying what driver it is using, likely "nv".  Change it to "nvidia".  Then save and quit, and restart X

---

### Post by Stormweaver on 2007-04-19
SUCCESS!!!!!!!!!!

WOOT!!!!

I'm sure it will need fine tweaking over time, but I have access to everything again!

So that knocks out the Graphics issue.

In between the posts here I knocked out the Teamspeak issue.

Does that leave me ready to look at possibly installing WoW now?


Stormweaver

---

### Post by igknighted on 2007-04-19
> **Stormweaver said:**
> SUCCESS!!!!!!!!!!

WOOT!!!!

I'm sure it will need fine tweaking over time, but I have access to everything again!

So that knocks out the Graphics issue.

In between the posts here I knocked out the Teamspeak issue.

Does that leave me ready to look at possibly installing WoW now?


Stormweaver

Sounds about right.  I don't use WoW, so I can't help there, but if you search the forum I know there is a how to for it somewhere.

Oh, one other thing.  Remove the 386 kernel so you don't accidentally boot from it, because if you do your graphics won't work.  As an alternative, you could use this command to go into the boot menu file and delete the lines pertaining to the 386 kernel:
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Stormweaver on 2007-04-19
Also - How hard would it be to create some sort of icon that when clicked would tell me if the Teamspeak server is running or not, and or one that could be clicked to run the process for it, rather then opening terminal, going to the directory and starting it there?


Or can I set it up to fire up on start up of the system?


Anywho, thats side line biz... God this rocks, I have a comp running again!


Thank you again so much, I'm hoping I've not been too much a nut case to work with.


Stormweaver

---

### Post by igknighted on 2007-04-19
> **Stormweaver said:**
> Also - How hard would it be to create some sort of icon that when clicked would tell me if the Teamspeak server is running or not, and or one that could be clicked to run the process for it, rather then opening terminal, going to the directory and starting it there?


Or can I set it up to fire up on start up of the system?


Anywho, thats side line biz... God this rocks, I have a comp running again!


Thank you again so much, I'm hoping I've not been too much a nut case to work with.


Stormweaver

hit alt+F2 to open a run dialog and start there, or make a launcher on your desktop (right click and its in that menu) and make the command the command you use to start the teamspeak.  You might need to select run in terminal though (its on option when making the launcher)

---

### Post by Stormweaver on 2007-04-20
Aight seems I have hit some walls again:


1. During start up I need to make the Grub screen not show the 386 version of the OS, this is on Server OS and it crashes by auto booting to the 386, I would just assume not have to stop GRUB each time to select what to boot.


2. The Nvidia seems to be holding its own, but I have no 3D enviroment, which I need for WoW and other things.... I know Ubuntu 386 Server doesn't accept GLX from Nvidia, but does that put an end to my 3D enviroment as a result?


3.  I understand the running commands thing, but is it possible to set up a icon that simply opens Terminal already set in a directory other then /home ??

4.  I got caught by the Bug that mutes sound during updates, went into the alsa mixer and turned it back on, now is that saved as is, or do I need to run a command before shut down or reboot to save that setting as is now???

5.  Is Cedega really worth it??  I mean using it vs wine for installs?



Stormweaver

---

### Post by Stormweaver on 2007-04-20
Giving the thread a lil bump in hopes of an update.

Stormweaver

---

### Post by dhtseany on 2007-07-06
Cedega is much better and easier to configure vs. wine. i hate wine personally, but then again its all a matter of opinion.

Sean

ps- in case you didn't know, you have to pay for cedega.

---

### Post by brundlelinux on 2008-03-25
Just curious where this thread lies in the grand scheme of things.  It's been coming up a year since the last post.

---

