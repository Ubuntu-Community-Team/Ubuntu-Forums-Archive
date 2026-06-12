---
title: "GnuCash-2.0.1"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by prc320 on 2006-09-07
I was have problem, I type in the following:

root@symsr-laptop:/home/symsr/Desktop# tar xzvf/gnucash/gnucash-2.0.1.tar.gz /etc/gnucash-2.0.1
tar: Old option `g' requires an argument.
Try `tar --help' or `tar --usage' for more information.
root@symsr-laptop:/home/symsr/Desktop#



What does this mean?

---

### Post by whizbaby on 2006-09-07
If you copy-pasted from your shell it means that you left out a space
tar xzvf**PUT_A_SPACE_HERE**/gnucash/gnucash-2.0.1.tar.gz /etc/gnucash-2.0.1

---

### Post by prc320 on 2006-09-07
whizbaby

Thanks but I have the problem:

root@symsr-laptop:/home/symsr/Desktop# tar xzvf /gnucash/gnucash-2.0.1.tar.gz /etc/gnucash-2.0.1
tar: /gnucash/gnucash-2.0.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: /etc/gnucash-2.0.1: Not found in archive
tar: Error exit delayed from previous errors
root@symsr-laptop:/home/symsr/Desktop#

Help? ](*,) 

prc320

---

### Post by whizbaby on 2006-09-07
> **prc320 said:**
> 
tar: /gnucash/gnucash-2.0.1.tar.gz: Cannot open: No such file or directory

This usually means this file isn't there. Can you see it? (Perhaps it's somewhere else? I see you like to become root, so, as root, type **updatedb** and, after a time **locate gnucash-2.0.1.tar.gz**, switch to the directory given and do **tar xzvf gnucash-2.0.1.tar.gz**)

---

### Post by prc320 on 2006-09-08
Thats better, but I still have a problem:

root@symsr-laptop:/etc/gnucash-2.0.1# ./configure
bash: ./configure: No such file or directory
root@symsr-laptop:/etc/gnucash-2.0.1#

Is they an error with sudo?

prc320

](*,)

---

### Post by whizbaby on 2006-09-08
[B]sudo updatedb
locate configure|grep gnucash[/B]
Try executing the script from where it actually *is*.

---

### Post by prc320 on 2006-09-08
Thats better, I understand the process now.

Whats this error?

symsr@symsr-laptop:/etc/gnucash-2.0.1/gnucash-2.0.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
symsr@symsr-laptop:/etc/gnucash-2.0.1/gnucash-2.0.1$


prc320

:-k

---

### Post by whizbaby on 2006-09-08
You'll have to install a C compiler then (*gcc*)!

---

### Post by prc320 on 2006-09-08
mmmmmmmmm

How do I do that?

prc320

---

### Post by whizbaby on 2006-09-08
**sudo apt-get install gcc-4.0**

---

### Post by skymt on 2006-09-08
No, actually, it would be better to do: "sudo aptitude install build-essential". If you just install GCC, you don't get several needed packages.

---

### Post by prc320 on 2006-09-08
ok I will try that then

prc320

---

### Post by whizbaby on 2006-09-08
> **skymt said:**
> No, actually, it would be better to do: "sudo aptitude install build-essential". If you just install GCC, you don't get several needed packages.

Right!
(@prc320: people would have more fun helping you if they get the impression that you are seriously digging, too, beginner or not.;) )

---

### Post by prc320 on 2006-09-08
I did this then:

sudo aptitude install build-essential

then I did this:

symsr@symsr-laptop:/etc/gnucash-2.0.1/gnucash-2.0.1$ ./configure checking for a BSD-compatible install... /usr/bin/install -c
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
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
symsr@symsr-laptop:/etc/gnucash-2.0.1/gnucash-2.0.1$

Now what?

prc320

---

### Post by whizbaby on 2006-09-08
**sudo apt-get install libxml-parser-perl**
(I got this by typing *apt-cache search xml*)

---

### Post by whizbaby on 2006-09-08
Aditionally, I recommend this site for getting to know ubuntu and linux a little better. This doesn't mean that you shouldn't ask anymore, it's only good to have an own lecture to look things up, this makes it easier for all (and you will be able to better understand/verify what the people here say).
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by prc320 on 2006-09-08
Thats good but now I have the problem of:

checking if scanf supports %lld conversions... yes
checking ltdl.h usability... no
checking ltdl.h presence... no
checking for ltdl.h... no
configure: error: Cannot find ltdl.h -- libtool-devel (or libtool-ltdl-devel) not installed?
symsr@symsr-laptop:/etc/gnucash-2.0.1/gnucash-2.0.1$

I looks at "apt-cache search libtool" and installed Libtool but no luck

prc320

---

### Post by whizbaby on 2006-09-08
> **prc320 said:**
> 
configure: error: Cannot find ltdl.h -- **libtool-devel** (or **libtool-ltdl-devel**) 
Perhaps installing the packages suggested in the error message is a good idea?

---

### Post by prc320 on 2006-09-09
I tried that already:

symsr@symsr-laptop:/etc/gnucash-2.0.1/gnucash-2.0.1$ apt-cache search libtool-devel
symsr@symsr-laptop:/etc/gnucash-2.0.1/gnucash-2.0.1$

and

symsr@symsr-laptop:/etc/gnucash-2.0.1/gnucash-2.0.1$ apt-cache search libtool-ltdl-devel
symsr@symsr-laptop:/etc/gnucash-2.0.1/gnucash-2.0.1$


help

---

### Post by whizbaby on 2006-09-09
The ubuntu name of the package is:

**libltdl3-dev**

(o.k. this one was a bit hard)

---

### Post by prc320 on 2006-09-10
Now I had a problem with GLIB

checking for GLIB - version >= 2.4.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error:
*** GLIB >= 2.4 is required to build Gnucash; please make sure you have the
*** development headers installed. The latest version of GLIB is
*** always available at [ftp://ftp.gnome.org/pub/gnome/sources/glib/](ftp://ftp.gnome.org/pub/gnome/sources/glib/).
symsr@symsr-laptop:/etc/gnucash-2.0.1/gnucash-2.0.1$

So I searched for GLIB and got

symsr@symsr-laptop:/etc/gnucash-2.0.1/gnucash-2.0.1$ apt-cache search GLIB libglib2.0-0 - The GLib library of C routines
libglib2.0-0-dbg - The GLib libraries and debugging symbols
libglib2.0-data - Common files for GLib library
libglib2.0-dev - Development files for the GLib library
libglib2.0-doc - Documentation files for the GLib library
libglibmm-2.4-1c2a - C++ wrapper for the GLib toolkit (shared libraries)
libglibmm-2.4-dev - C++ wrapper for the GLib toolkit (development files)
libgnomecups1.0-1 - GNOME library for CUPS interaction
libgnomecups1.0-dev - GNOME library for CUPS interaction (headers)
libsoup2.2-8 - an HTTP library implementation in C -- Shared library
libsoup2.2-dev - an HTTP library implementation in C -- Development files
abicheck - binary compatibility checking tool
bglibs-dev - BG Libraries Collection
bglibs-doc - BG Libraries Collection (documentation)
classpath-common - architecture independent files
free-java-sdk - Complete Java SDK environment consisting of free Java tools
gftp - X/GTK+ FTP client
gftp-text - colored FTP client using GLib
guile-gnome0-glib - Guile bindings for GLib
ja-trans - Japanese gettext message files
kmtrace - a KDE memory leak tracer
libdb1-compat - The Berkeley database routines [glibc 2.0/2.1 compatibility]
libg++2.8.1.3-glibc2.2 - The GNU C++ extension library - runtime version
libgetopt-java - GNU getopt - Java port
libgfccore-2.0-0-dbg - GTK+ Foundation Classes Core - debug symbols
libgfccore-2.0-0c2a - GTK+ Foundation Classes Core - shared libraries
libgfccore-dev - GTK+ Foundation Classes Core - development files
libgfccore-doc - GTK+ Foundation Classes Core - API reference documentation
libghc6-missingh-dev - Library of utility functions for Haskell, GHC6 package
libglib-cil - CLI binding for the GLib utility library
libglib-java - GLIB bindings for Java
libglib1.2-doc - Documentation files for the GLib library version 1.2
libglib2-ruby - Glib 2 bindings for the Ruby language
libgnetwork1.0-0 - networking wrapper library using Glib/GObject
libgnetwork1.0-dev - networking wrapper library using Glib/GObject (development files)
libhugs-missingh - Library of utility functions for Haskell, Hugs package
libmissinglib-ocaml-dev - Library of utility functions for OCaml
libnm-glib-dev - network management framework (GLib interface)
libnm-glib0 - network management framework (GLib shared library)
libnm-glib0-dbg - network management framework (GLib shared library with debug symbols)
libnss-ldap - NSS module for using LDAP as a naming service
libnss-pgsql1 - name service switch module using PostgreSQL
libroy-dev - Utility and data structure library (development files)
libroy1 - Utility and data structure library (runtime files)
libroy1-dbg - Utility and data structure library (debugging files)
libroy1-prof - Utility and data structure library (profiling files)
libsoup2.2-doc - an HTTP library implementation in C -- API Reference
libstdc++2.10-glibc2.2 - The GNU stdc++ library
libuclibc-dev - A small implementation of the C library
libuclibc0 - A small implementation of the C library
libwww-dev - The W3C WWW library - development files
libwww-ssl-dev - The W3C WWW library - development files (SSL support)
linuxinfo - Displays extended system information
manpages-pl-dev - Polish man pages for developers
missingh-doc - Documentation for Haskell utility library
perdition-dev - Development libraries and headers for perdition
perdition-ldap - Library to allow perdition to access LDAP based popmaps
perdition-mysql - Library to allow perdition to access MySQL based popmaps
perdition-odbc - Library to allow perdition to access ODBC based popmaps
perdition-postgresql - Library to allow perdition to access PostgreSQL based popmaps
pingpong - Free server for Amateur Radio convers
python-utmp - python module for working with utmp
dbus - simple interprocess messaging system
gftp-gtk - X/GTK+ FTP client
glibc-doc - GNU C Library: Documentation
libarts1-mpeglib - mpeglib plugin for aRts, supporting mp3 and mpeg audio/video
libavahi-glib-dev - Development headers for the Avahi glib integration library
libavahi-glib1 - Avahi glib integration library
libc6 - GNU C Library: Shared libraries and Timezone data
libc6-pic - GNU C Library: PIC archive library
libdbus-1-2 - simple interprocess messaging system
libdbus-glib-1-2 - simple interprocess messaging system (GLib-based shared library)
libdbus-glib-1-dev - simple interprocess messaging system (GLib interface)
libglib-perl - Perl interface to the GLib and GObject libraries
libglib1.2 - The GLib library of C routines
libglib1.2-dbg - GLib libraries and debugging symbols
libglib1.2-dev - Development files for GLib library
libglib2.0-cil - CLI binding for the GLib utility library 2.8
libgnet-dev - Developer files for GNet network library
libgnet2.0-0 - GNet network library
libgoffice-1-2 - Document centric objects library - runtime files
libgoffice-1-2-dbg - Document centric objects library - debugging files
libgoffice-1-common - Document centric objects library - common files
libgoffice-1-dev - Document centric objects library - runtime files
libgoffice-gtk-1-2 - Document centric objects library - runtime files
libgoffice-gtk-1-2-dbg - Document centric objects library - debugging files
libnss-mdns - NSS module for Multicast DNS name resolution
libpoppler-glib-dev - PDF rendering library -- development files (GLib interface)
libpoppler1-glib - PDF rendering library (GLib-based shared library)
linux-kernel-headers - Linux Kernel Headers for development
manpages-dev - Manual pages about using GNU/Linux for development
mpeglib - mp3 and mpeg I audio and video library
libtag1-dev - TagLib Audio Meta-Data Library [development]
libtag1c2a - TagLib Audio Meta-Data Library
libtagc0 - TagLib Audio Meta-Data Library (C bindings)
libtagc0-dev - TagLib Audio Meta-Data Library (C bindings) [development]
libtag1-doc - TagLib Audio Meta-Data Library [documentation]
winbind - service to resolve user and group information from Windows NT servers
symsr@symsr-laptop:/etc/gnucash-2.0.1/gnucash-2.0.1$ 

Help................

prc320

---

### Post by whizbaby on 2006-09-10
Try it with the first entries:

libglib2.0-0-dbg - The GLib libraries and debugging symbols
libglib2.0-data - Common files for GLib library
libglib2.0-dev - Development files for the GLib library
libglib2.0-doc - Documentation files for the GLib library

libglibmm-2.4-1c2a - C++ wrapper for the GLib toolkit (shared libraries)
(I'm not so shure that you need the wrapper, but it can't hurt)

---

### Post by prc320 on 2006-09-10
ok I will try that later on.

prc320

---

### Post by rbmorse on 2006-09-10
Does not the GNUcash package have a readme or Install document in the tarball that lists all of the prerequisites and dependencies?  

I know people don't like to RTFM, but sometimes...

---

### Post by whizbaby on 2006-09-10
Unfortionately I didn't look in the repositories if gnucash is listed (never heard of it, thought you downloaded the source because it's not there, I do this often). Now a simple question comes to my mind (and please don't be angry with me):
Did you try to install the package the way it's meant to be? Perhaps you think this (what we were about to do) is the way packages are normally installed in ubuntu, in fact it's not.
If you believe that you don't need a special install (and have *universe* and *multiverse* repositories enabled), open a terminal and type:
**sudo apt-get install gnucash gnucash-common**

to enable *universe* and *multiverse* type
**sudo nano /etc/apt/sources.list**

and remove any # at the start of lines containing *universe* and/or *multiverse* and then
**sudo apt-get update**

(in this case you didn't need the stuff we have done, sorry, but I think you learned one or two useful commands)

If you still want to compile you'll find the dependancies with **apt-cache search gnucash --full**
Again sorry, perhaps I misunderstood what you were trying to do;)

---

### Post by prc320 on 2006-09-11
I tried *apt-cache search gnucash --full* but it given me 1.8.12-6ubuntu3. Not 2.0.1.

This is the sitution so far:


I get the following errors:

checking if unsigned long is at least as big as guint32... yes
checking if guile needs our copy of srfi-1... no
checking if guile needs our copy of srfi-11... no
checking if guile needs our copy of srfi-19... no
checking if guile needs our copy of srfi-2... no
checking if guile needs our copy of srfi-8... no
checking if guile needs our copy of srfi-9... no
checking if guile needs our copy of (guile www)... checking for guile... (cached) /usr/bin/guile
checking for guile-config... /usr/bin/guile-config
checking for guile-tools... /usr/bin/guile-tools
checking if (www main) is available... no
checking for gconf-2.0 >= "2.0"... Package gconf-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gconf-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gconf-2.0' found
configure: error: Library requirements (gconf-2.0 >= "2.0") not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
symsr@symsr-laptop:/etc/gnucash-2.0.1/gnucash-2.0.1$

I have done searches for the follwing
sudo apt-get install libguile-dev
apt-cache search guile-config
apt-cache search gconf-2.0 

to no avail. What next?

prc320

---

### Post by whizbaby on 2006-09-11
So you need the gnucash2 version, eh? You will probably get the package you need by
**sudo apt-get install gconf2 gconf2-common guile-1.6 guile-common**

---

### Post by prc320 on 2006-09-12
That didn't work either.

I am going to check out what depedencies I need. How do I go about check my computer what level I have?

---

### Post by whizbaby on 2006-09-12
Somebody already compiled gnucash2.0 with all dependancies:

[http://ubuntustudio.com/uploads/dapper/gnucash-2.0.0/](http://ubuntustudio.com/uploads/dapper/gnucash-2.0.0/)

install with **sudo dpkg -i gnucash_2.0.0-1_i386.deb** 
Does this run on your machine (if not the readme is quite usefull, it tells what to do to get gnucash compiled)?

---

### Post by prc320 on 2006-09-13
Mmmmm

a. I am going back one level.
b. I am going into deep command line work, will you help me?

prc320

](*,)

---

### Post by whizbaby on 2006-09-13
> **prc320 said:**
> 
I am going into deep command line work, will you help me?

Whatever you're trying to say with this (a little hint would be nice), I'll do my best to help you.

---

### Post by prc320 on 2006-09-15
I tried that and the following came up:

root@symsr-laptop:/etc/gnucash/gnucash-2.0.0# sudo dpkg -i gnucash_2.0.0-1_i386.deb
(Reading database ... 89177 files and directories currently installed.)
Preparing to replace gnucash 1.8.12-6ubuntu3 (using gnucash_2.0.0-1_i386.deb) ...
Unpacking replacement gnucash ...
dpkg: dependency problems prevent configuration of gnucash:
 gnucash depends on gnucash-common (>= 2.0.0-1); however:
  Version of gnucash-common on system is 1.8.12-6ubuntu3.
 gnucash depends on libgsf-gnome-1-113 (>= 1.13.99); however:
  Package libgsf-gnome-1-113 is not installed.
 gnucash depends on guile-g-wrap; however:
  Package guile-g-wrap is not installed.
dpkg: error processing gnucash (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnucash
root@symsr-laptop:/etc/gnucash/gnucash-2.0.0#

I suspect I just load ones that I haven't got? Is that right?

prc320

---

### Post by whizbaby on 2006-09-15
> 
I suspect I just load ones that I haven't got? Is that right?

Yes, this should work.

---

### Post by prc320 on 2006-09-15
Unfortunately this happened,


symsr@symsr-laptop:/etc/gnucash/gnucash-2.0.0$ sudo apt-get -f install gnucash-common libgsf-gnome-1-113 guile-g-wrap
Reading package lists... Done
Building dependency tree... Done
gnucash-common is already the newest version.
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies.
  gnucash: Depends: gnucash-common (>= 2.0.0-1) but 1.8.12-6ubuntu3 is to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).
symsr@symsr-laptop:/etc/gnucash/gnucash-2.0.0$

I am confused!

Help!

prc320

---

### Post by whizbaby on 2006-09-15
First install the last two packages
**sudo apt-get -f install *libgsf-gnome-1-113 guile-g-wrap***
as to the error message with gnucash-common, download
[http://ubuntustudio.com/uploads/dapper/gnucash-2.0.0/gnucash-common_2.0.0-1_all.deb](http://ubuntustudio.com/uploads/dapper/gnucash-2.0.0/gnucash-common_2.0.0-1_all.deb)
and try to install this with
**sudo dpkg -i *gnucash-common_2.0.0-1_all.deb***
(being in the directory where you downloaded to)

---

### Post by prc320 on 2006-09-16
Wow, that's great thank you for getting me there.

Thank you so much.


Robert

prc320

:lol:

---

### Post by whizbaby on 2006-09-16
Does this mean it's up-and-a-workin or wot?

---

### Post by prc320 on 2006-09-17
That's it, I have gnucash 2.0.0.

Thank you

PRC320:-\"

---

### Post by whizbaby on 2006-09-17
:cool:

---

### Post by xhilyn on 2006-09-24
Hi all.
Just a quick question I installed GnuCash 2.0.0 a while back using the compiled pakage and want to update to 2.0.1. I have checked the Synaptic Package Manager but that only has the original version 2.0.0. I am a complete novice when it comes to the command line so any help would be much appreciated. Thanks in advance. xhi.

---

### Post by jacrider on 2006-09-25
I was having real problems with the version of gnucash installed from Synaptic, version 1.8.5 (I think).  It was crashing/hanging.  The only application that was giving me trouble on Dapper.

I found this entry in a blog on how to install version 2.0.1:

[http://ocaoimh.ie/2006/09/14/gnucash-20-on-ubuntu-dapper/](http://ocaoimh.ie/2006/09/14/gnucash-20-on-ubuntu-dapper/)

First, I downloaded both files linked in the blog (gnucash and gnucash-common) to my Desktop.

Next, before installing the newest version, I used Synaptic to uninstall the old version.

Then I used GDebi (invoked by double-clicking on the Desktop icon) to install  gnucash-common first.  

Then, again using GDebi, I installed gnucash.  This time, GDebi identified several dependencies, which were also installed.

That's it.  Gnucash showed up in my Applications menu and it works.

It is a much nicer UI and far more intuitive on the import of transactions.  A real improvement.

---

