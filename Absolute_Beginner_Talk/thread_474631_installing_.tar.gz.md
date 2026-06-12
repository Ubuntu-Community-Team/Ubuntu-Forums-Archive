---
title: "installing .tar.gz"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by JLoomis95 on 2007-06-15
Hey im trying to install a linux games. its a tar.gz, i have done a little bit but now im confused. 
   1. tar xzvf WFUT-1.1.0.tar.gz 
   2. sudo apt-get install build-essential
now i have no clue what to do. Any help would be great, thanks.

---

### Post by Outrunner on 2007-06-15
Well, it depends, is this game precompiled, or do you have to compile it yourself? To find out
```

cd <extracted_directory>
```

```
ls
```

And post the output here so we can see what you need to do.

Anyway, here's a tip, when you want to type a directory or file name in the terminal, simply type the first few letters and press TAB to autocomplete, or TAB twice to see what autocomplete options there are.

EDIT: By the way I searched for WFUT on google and I found this 	"Software updater tool for WorldForge applications", are you sure you got the right program?

---

### Post by drs305 on 2007-06-15
Edited: bowing out to let the pros answer ;-)

Edited 31 posts later: Now I'm really glad ;-) ;-)

---

### Post by kevdog on 2007-06-15
OK just generally,

I think the proper command is

tar -zxvf WFUT-1.1.0.tar.gz 

Once the archive is extacted, you will probably have to change into that directory from current one:
cd WFUT-1.1.0

Look for a INSTALL or README file -- it should contain instructions.
If it does not, most programs are compiled and installed like this:
make clean
./config (if you do not have a config file in the directory then you might get an error - no big deal)
make 
sudo make install

That should be about it -- Again the INSTALL or README file should inform you

---

### Post by JLoomis95 on 2007-06-15
i cant do ./configure or make or make install i have tried but cant, so im confused.

---

### Post by kevdog on 2007-06-15
Lists the contents of the current directory for me:

ls

It sounds like you might not be in the correct directory

---

### Post by Outrunner on 2007-06-15
OK, then maybe the game is precompiled and you don't need to do it, Post the output of

```
ls
``` while in the game's directory so we can see what you need to run.

---

### Post by JLoomis95 on 2007-06-15
i think im in the right one
      is wont work

---

### Post by Outrunner on 2007-06-15
> **JLoomis95 said:**
> i think im in the right one
      is wont work

OK, but if you want our help, post the output of 

```
ls
```

---

### Post by JLoomis95 on 2007-06-15
sry ls works
but know what?

---

### Post by meborc on 2007-06-15
<never mind - you guys are too fast for me>

---

### Post by Outrunner on 2007-06-15
> **JLoomis95 said:**
> sry ls works
but know what?

OK, let me be more specific. Type

```
ls
```

and select the text that appears... Hover your mouse over it and right-click and then click 'Copy' then come here and 'Paste' it into a reply, got that?

---

### Post by JLoomis95 on 2007-06-15
ok here they are

aclocal.m4  config.log    INSTALL      Makefile.in  project.properties  TODO
AUTHORS     configure     install-sh   missing      project.xml
build.xml   configure.ac  m4           NEWS         README
ChangeLog   COPYING       Makefile.am  pom.xml      src

---

### Post by JLoomis95 on 2007-06-15
how do you put it in the code box?

---

### Post by meborc on 2007-06-15
ahh... just open nautilus (file manager) and see what files are there in your home folder, and if there is a folder called WFUT (or similar) then see what files are there inside... and READ the install or readme files :D

edit: again too late :D

you need to do 

```
./configure
```

then

```
make
```

and then 

```
sudo make install
```

---

### Post by kevdog on 2007-06-15
Open and read the INSTALL file:

gedit INSTALL


What does it say??

---

### Post by Outrunner on 2007-06-15
> **JLoomis95 said:**
> how do you put it in the code box?

Highligh your text and click the '#' icon at the top of the reply box.

Are you sure you installed the build-essential package properly?
```

sudo aptitude install build-essential
```
```

./configure
make
sudo make install
```
If this doesn't work you should try reading the INSTALL file

```
gedit INSTALL
```

---

### Post by JLoomis95 on 2007-06-15
nstallation Instructions
*************************

Copyright (C) 1994, 1995, 1996, 1999, 2000, 2001, 2002, 2004, 2005 Free
Software Foundation, Inc.

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

Some systems require unusual options for compilation or linking that the
`configure' script does not know about.  Run `./configure --help' for
details on some of the pertinent environment variables.

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
option `--prefix=PREFIX'.

   You can specify separate installation prefixes for
architecture-specific files and architecture-independent files.  If you
give `configure' the option `--exec-prefix=PREFIX', the package will
use PREFIX as the prefix for installing programs and libraries.
Documentation and other data files will still use the regular prefix.

   In addition, if you use an unusual directory layout you can give
options like `--bindir=DIR' to specify different values for particular
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

There may be some features `configure' cannot figure out automatically,
but needs to determine by the type of machine the package will run on.
Usually, assuming the package is built to be run on the _same_
architectures, `configure' can figure that out, but if it prints a
message saying it cannot guess the machine type, give it the
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

If you want to set default values for `configure' scripts to share, you
can create a site shell script called `config.site' that gives default
values for variables like `CC', `cache_file', and `prefix'.
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

causes the specified `gcc' to be used as the C compiler (unless it is
overridden in the site shell script).  Here is a another example:

     /bin/bash ./configure CONFIG_SHELL=/bin/bash

Here the `CONFIG_SHELL=/bin/bash' operand causes subsequent
configuration-related scripts to be executed by `/bin/bash'.

`configure' Invocation
======================

`configure' recognizes the following options to control how it operates.

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

---

### Post by JLoomis95 on 2007-06-15
if i type 
```
./configure
```
than i get this
```
configure: error: no acceptable java compiler found in $PATH
```

---

### Post by Malibu Illusion on 2007-06-15
```

sudo apt-get install gcj-4.1
./configure
make
sudo make install

```

---

### Post by kevdog on 2007-06-15
Are java compilers contained in the build-essential package???

I need to check

---

### Post by JLoomis95 on 2007-06-15
i see that but the problem is still not fixed, still same error

---

### Post by JLoomis95 on 2007-06-15
no there not

---

### Post by kevdog on 2007-06-15
I think you need more than what is in the build-essential package -- from what I see a java compiler is not in the build-essential package.

I dont compile programs on a regular basis, but I did install a java compiler once, I just need to find the right package for you to download and install. 

Please do not post the whole file here, but does the README file give you any indication what java package you need to compile the program.  Sometime reading the file or the INSTALL file helps, even though I didnt see anything in the INSTALL file that seemed helpful for me.

---

### Post by JLoomis95 on 2007-06-15
WFUT has been built on Java 1.4.1 but may run on earlier versions. WFUT will mostly run under gcj 4.1 with a few minor GUI issues.

---

### Post by Malibu Illusion on 2007-06-15
Plz see my post on the bottom of page two.

---

### Post by JLoomis95 on 2007-06-15
thx you that worked

---

### Post by JLoomis95 on 2007-06-15
did that finsh installing it and if so how do i start the program?

---

### Post by Bablefish on 2007-06-15
I know this is a little off topic but if you want good games check no further than Add Remove I found some really great games there.

---

### Post by JLoomis95 on 2007-06-15
such as...

---

### Post by kevdog on 2007-06-15
Mr. Illusion -- thanks for helping out!!

---

