---
title: "How do i install programs?"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by Yautja_Ender on 2006-01-04
How do i install programs that i download for linux...not through synaptic...?for example i dowlnoaded limewire and i cant get it to install.

thank you

---

### Post by sethmahoney on 2006-01-04
Often, when you're downloading programs to install, you will find a .deb package.  This is the one that you want.  To install it, open up a terminal window, go to the folder you downloaded it to, and type

dpkg -i name-of-file

replacing name-of-file with the filename of the .deb file.

You can install other types of files, but it is trickier.

---

### Post by taseal on 2006-01-04
might be not what ure looking for, but to download/install limewire all you have to do is open the terminal and write sudo apt-get install limewire :)

---

### Post by Omnios on 2006-01-04
Most tar-balls (downloaded programs) com with a help file which explaines the install. I useually open the gz with fileroller, the graphical decompression program and read the install help file that is normally there You can also read it after you decompress the tar ball. Most of the time there is a list of dependancies suck as programs or libraries you will need to install to instal the program. 

 This is an example of the install instructions.

 ```
Copyright (C) 1994, 1995, 1996, 1999, 2000, 2001, 2002 Free Software
Foundation, Inc.

   This file is free documentation; the Free Software Foundation gives
unlimited permission to copy, distribute and modify it.

Basic Installation
==================

   These are generic installation instructions.

   The `configure' shell script attempts to guess correct values for
various system-dependent variables used during compilation.  It uses
those values to create a `Makefile' in each directory of the package.
It may also create one or more `.h' files containing system-dependent
definitions.  Finally, it creates a shell script `config.status' that
you can run in the future to recreate the current configuration, and a
file `config.log' containing compiler output (useful mainly for
debugging `configure').

   It can also use an optional file (typically called `config.cache'
and enabled with `--cache-file=config.cache' or simply `-C') that saves
the results of its tests to speed up reconfiguring.  (Caching is
disabled by default to prevent problems with accidental use of stale
cache files.)

   If you need to do unusual things to compile the package, please try
to figure out how `configure' could check whether to do them, and mail
diffs or instructions to the address given in the `README' so they can
be considered for the next release.  If you are using the cache, and at
some point `config.cache' contains results you don't want to keep, you
may remove or edit it.

   The file `configure.ac' (or `configure.in') is used to create
`configure' by a program called `autoconf'.  You only need
`configure.ac' if you want to change it or regenerate `configure' using
a newer version of `autoconf'.

The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.

Compilers and Options
=====================

   Some systems require unusual options for compilation or linking that
the `configure' script does not know about.  Run `./configure --help'
for details on some of the pertinent environment variables.

   You can give `configure' initial values for configuration parameters
by setting variables in the command line or in the environment.  Here
is an example:

     ./configure CC=c89 CFLAGS=-O2 LIBS=-lposix

   *Note Defining Variables::, for more details.

Compiling For Multiple Architectures
====================================

   You can compile the package for more than one kind of computer at the
same time, by placing the object files for each architecture in their
own directory.  To do this, you must use a version of `make' that
supports the `VPATH' variable, such as GNU `make'.  `cd' to the
directory where you want the object files and executables to go and run
the `configure' script.  `configure' automatically checks for the
source code in the directory that `configure' is in and in `..'.

   If you have to use a `make' that does not support the `VPATH'
variable, you have to compile the package for one architecture at a
time in the source code directory.  After you have installed the
package for one architecture, use `make distclean' before reconfiguring
for another architecture.

Installation Names
==================

   By default, `make install' will install the package's files in
`/usr/local/bin', `/usr/local/man', etc.  You can specify an
installation prefix other than `/usr/local' by giving `configure' the
option `--prefix=PATH'.

   You can specify separate installation prefixes for
architecture-specific files and architecture-independent files.  If you
give `configure' the option `--exec-prefix=PATH', the package will use
PATH as the prefix for installing programs and libraries.
Documentation and other data files will still use the regular prefix.

   In addition, if you use an unusual directory layout you can give
options like `--bindir=PATH' to specify different values for particular
kinds of files.  Run `configure --help' for a list of the directories
you can set and what kinds of files go in them.

   If the package supports it, you can cause programs to be installed
with an extra prefix or suffix on their names by giving `configure' the
option `--program-prefix=PREFIX' or `--program-suffix=SUFFIX'.

Optional Features
=================

   Some packages pay attention to `--enable-FEATURE' options to
`configure', where FEATURE indicates an optional part of the package.
They may also pay attention to `--with-PACKAGE' options, where PACKAGE
is something like `gnu-as' or `x' (for the X Window System).  The
`README' should mention any `--enable-' and `--with-' options that the
package recognizes.

   For packages that use the X Window System, `configure' can usually
find the X include and library files automatically, but if it doesn't,
you can use the `configure' options `--x-includes=DIR' and
`--x-libraries=DIR' to specify their locations.

Specifying the System Type
==========================

   There may be some features `configure' cannot figure out
automatically, but needs to determine by the type of machine the package
will run on.  Usually, assuming the package is built to be run on the
_same_ architectures, `configure' can figure that out, but if it prints
a message saying it cannot guess the machine type, give it the
`--build=TYPE' option.  TYPE can either be a short name for the system
type, such as `sun4', or a canonical name which has the form:

     CPU-COMPANY-SYSTEM

where SYSTEM can have one of these forms:

     OS KERNEL-OS

   See the file `config.sub' for the possible values of each field.  If
`config.sub' isn't included in this package, then this package doesn't
need to know the machine type.

   If you are _building_ compiler tools for cross-compiling, you should
use the `--target=TYPE' option to select the type of system they will
produce code for.

   If you want to _use_ a cross compiler, that generates code for a
platform different from the build platform, you should specify the
"host" platform (i.e., that on which the generated programs will
eventually be run) with `--host=TYPE'.

Sharing Defaults
================

   If you want to set default values for `configure' scripts to share,
you can create a site shell script called `config.site' that gives
default values for variables like `CC', `cache_file', and `prefix'.
`configure' looks for `PREFIX/share/config.site' if it exists, then
`PREFIX/etc/config.site' if it exists.  Or, you can set the
`CONFIG_SITE' environment variable to the location of the site script.
A warning: not all `configure' scripts look for a site script.

Defining Variables
==================

   Variables not defined in a site shell script can be set in the
environment passed to `configure'.  However, some packages may run
configure again during the build, and the customized values of these
variables may be lost.  In order to avoid this problem, you should set
them in the `configure' command line, using `VAR=value'.  For example:

     ./configure CC=/usr/local2/bin/gcc

will cause the specified gcc to be used as the C compiler (unless it is
overridden in the site shell script).

`configure' Invocation
======================

   `configure' recognizes the following options to control how it
operates.

`--help'
`-h'
     Print a summary of the options to `configure', and exit.

`--version'
`-V'
     Print the version of Autoconf used to generate the `configure'
     script, and exit.

`--cache-file=FILE'
     Enable the cache: use and save the results of the tests in FILE,
     traditionally `config.cache'.  FILE defaults to `/dev/null' to
     disable caching.

`--config-cache'
`-C'
     Alias for `--cache-file=config.cache'.

`--quiet'
`--silent'
`-q'
     Do not print messages saying which checks are being made.  To
     suppress all normal output, redirect it to `/dev/null' (any error
     messages will still be shown).

`--srcdir=DIR'
     Look for the package's source code in directory DIR.  Usually
     `configure' can determine that directory automatically.

`configure' also accepts some other, not widely useful, options.  Run
`configure --help' for more details.


```

 ALso you wil probably need build-essencial from synaptic which is a bunch of install tools to compile the tarball.

---

### Post by DoorGunner on 2006-01-04
some programs will require compiling. So be sure that you have the following. 

have a look in the tips and tricks section of the ubuntu guide.
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

some packages will require gcc and other compilers that dont automatically come with ubuntu....ensure you have them installed....the how too's are in here as well...

---

### Post by Yautja_Ender on 2006-01-04
what if its a .rpm file?

---

### Post by piedamaro on 2006-01-04
It' s an app already compiled and packaged for the rpm package manger, wich is used by sone distributions notably redhat/fedora, suse, mandrake.
You can use a program called alien to convert from rpm to deb and vv. but I discourage that.
Try to find the app with synaptic, if it isn't there try to find someone on the net who packaged it in a deb format, if not compile it manually and create a package with checkinstall. 
At least this is what I do :)

---

### Post by Sandlst on 2006-01-04
rpm files are very easy.....all you have to do is make sure you have alien installed ```
sudo apt-get install alien
``` then run the command (ignoring parenthesis) ```
sudo alien (/path/to/.rpmfile)
``` This will in effect change the .rpm file to a .deb file, and after that just install the deb file normally (ignoring parenthesis) ```
sudo dpkg -i (/path/to/.debfile)
```

---

### Post by Omnios on 2006-01-04
For .rpm 's I think you need to install " alien " from synaptic. I dont have a lot of experience with alian but you might want to do a search on how to use it.

 Got this from another post

CD to the files directory

 ```
sudo apt-get install alien
sudo alien package-name.rpm
sudo dpkg -i package_name.deb
```

 there is also a note of
 
```
sudo alien -i [file name]
```
that I did when trying to intall realplayer from a rpm where -i =install.

 EDIT: as above was checking posts so you beat me to it lol

 Note it is best to try to get a deb first as not all .rpm packages will work with Ubuntu

---

### Post by R3linquish3r on 2006-01-04
i have the same problem except my file is a .sh

---

### Post by Omnios on 2006-01-04
If I remeber correctly for a .sh file you cd to the directory the .sh is in and type sudo .file_mame. Is the program you downloaded just a .sh file?

---

### Post by R3linquish3r on 2006-01-04
no. for reference it is teamspeak. the sh file, when launched in GUI launches the install program. i read this in the readme. there are a bunch of other files for manual install but i dont understand enough yet for that :P

---

### Post by R3linquish3r on 2006-01-04
also it says sudo setup.sh is a command not found

---

### Post by Jukey on 2006-01-04
is it in the right directory??

---

### Post by Omnios on 2006-01-04
In terminal cd to the directory cd /home/your_name/..... 

 do a " ls " command to see if you are in the right directory and the .sh is there. 

 then type "  Sudo ./filename or .filename find most of the time . works but sometimes needs ./

---

### Post by R3linquish3r on 2006-01-04
Alrighty thanks. also, i have an XFire plugin for GAIM i downlaoded. it is an exe file. what do i do to install that?

---

### Post by Omnios on 2006-01-04
[QUOTE=Omnios]In terminal cd to the directory cd /home/your_name/..... 

 do a " ls " command to see if you are in the right directory and the .sh is there. 

 then type "  Sudo ./filename or .filename find most of the time . works but sometimes needs ./[/QUOTE]

 Oh just remembered you have to make the .sh executable

---

### Post by R3linquish3r on 2006-01-04
yeah it worked fine. now i jsut gatta do the GAIM pluggin. any ideas?

---

### Post by Omnios on 2006-01-04
[QUOTE=R3linquish3r]Alrighty thanks. also, i have an XFire plugin for GAIM i downlaoded. it is an exe file. what do i do to install that?[/QUOTE]

 Have not heard of an a exe for a while, they used to run them in the run command thing. Basicly if it is an executable you should be able run it with .filename or ./file_name Also again make shure it is exacutable. Also use the sudo command as most installs isntall things in the file system and you need root to write to most of those directories.

---

### Post by R3linquish3r on 2006-01-04
my bad. its labbeled as a windows executable. sry :(

---

### Post by DoorGunner on 2006-01-04
im not sure if i saw the answer about the sh

if you have an sh file all you need to do is

$ sudo sh filename.sh   (same thing as ./filename.sh)
and it will install automatically

---

