---
title: "Can someone help make this understandable."
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by markusgrey on 2008-01-20
**I want to know what this stuff means**
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

By default, `make install' installs the package's commands under
`/usr/local/bin', include files under `/usr/local/include', etc.  You
can specify an installation prefix other than `/usr/local' by giving
`configure' the option `--prefix=PREFIX'.

   You can specify separate installation prefixes for
architecture-specific files and architecture-independent files.  If you
pass the option `--exec-prefix=PREFIX' to `configure', the package uses
PREFIX as the prefix for installing programs and libraries.
Documentation and other data files still use the regular prefix.

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
use the option `--target=TYPE' to select the type of system they will
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

### Post by Kilz on 2008-01-20
It looks to be compiling instructions, are you trying to install a piece of software?

---

### Post by markusgrey on 2008-01-20
yes

---

### Post by kodak on 2008-01-20
have you checked the repos first before compiling?

---

### Post by frup on 2008-01-20
That's reasonably advanced. Initially all you need to know is three steps plus an initial set up you need on ubuntu.

First before you can compile anything on Ubuntu you need Build Essential which is a set of tools you need.Get it from synaptic or quickly type sudo apt-get install build-essential

You then would get the source you want to compile. Often this comes in a tar.gz file. You extract that to where you want it and then cd to that directory in terminal (eg cd Desktop/source/)

Then when compiling you essentially go

./configure
make 
make install

The command line will spit out any errors there might be such as missing dependencies. This is either that a version of a required library is out of date or missing.

---

### Post by jleaker01z on 2008-01-20
Download and extract the .tar.gz file

Open a terminal, and cd to the folder you extracted  (for example, cd /home/username/Desktop/application-1.09.4

Type "sudo ./configure" then hit enter
Type "sudo make" then hit enter
Type "sudo make install" then hit enter

Your program is now installed.

---

### Post by bwhite82 on 2008-01-20
Compiling isn't the easiest thing to do for a new user. I'd recommend reading up on Compiling in the wiki. [http://help.ubuntu.com/community]("http://help.ubuntu.com/community") What app are you attempting to compile anyways?

---

### Post by markusgrey on 2008-01-20
what are repos?

---

### Post by corney91 on 2008-01-20
> **markusgrey said:**
> 
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


This is the only bit you need to worry about if you're installing something. Basically:
```
./configure
make
sudo make install
```

but you may want to check the repositories to see if what you want to install is there first...


EDIT: Looks like I'm quite late...

---

### Post by Kilz on 2008-01-20
> **markusgrey said:**
> yes

Kodak has the right idea, Ubuntu users should always look in the repositories first. To do that we use Synaptic. [Here is a page that is most helpful in helping to understand Synaptic]("http://www.monkeyblog.org/ubuntu/installing/") and how to install anything in Ubuntu.

---

### Post by kodak on 2008-01-20
> **markusgrey said:**
> what are repos?

repositories, where all the software is for your OS

what operating system have you installed?

---

### Post by erfahren on 2008-01-20
deleted

---

### Post by banewman on 2008-01-20
That's alot of info if you only need to install a program
The way to go about that is to download the program - change to the directory it was downloaded to e.g. if it was downloaded to /usr/bin you type in a terminal
cd /usr/bin/ProgramName
then type ./configure - to configure the prog
then type make
then make install
You may need to put sudo before any/all these lines depending on where the file is and where the install is going
If there are any unusual install routines needed they will be spelt out in a readme file that will be part of the download so always check for one before going any further
Feel free to ask more if needed
:)

---

### Post by mdsmedia on 2008-01-20
from his other thread on upgrading, the OP is using Ubuntu Breezy, and probably looking for Gnomebaker or other burning software. He's also very much a newbie from his first post in that thread, a newbie to either Windows or Linux so step by step instructions would be helpful, I think.

---

### Post by Scarath on 2008-01-20
does anyone else put much stock in 'alien' as an install tool?

I found converting things to .deb helps when i first started on ubuntu but it doesnt always work.

@ the OP 'alien' turns packages into '.deb' files which install things automatically from a GUI

---

### Post by mdsmedia on 2008-01-20
> **banewman said:**
> That's alot of info if you only need to install a program
The way to go about that is to download the program - change to the directory it was downloaded to e.g. if it was downloaded to /usr/bin you type in a terminal
cd /usr/bin/ProgramName
then type ./configure - to configure the prog
then type make
then make install
You may need to put sudo before any/all these lines depending on where the file is and where the install is going
If there are any unusual install routines needed they will be spelt out in a readme file that will be part of the download so always check for one before going any further
Feel free to ask more if needed
:)I'd suggest steering clear of the command line at this stage, if the program is in the repos.

What are you trying to install. If it's not in the repos there might be an alternative that is.

---

### Post by Smelly Avocado on 2008-01-20
wouldn't 'checkinstall' be better than 'make install' because you can remove it with apt-get?

---

### Post by markusgrey on 2008-01-20
i dont get that synaptic thing

---

### Post by oldos2er on 2008-01-20
> **markusgrey said:**
> i dont get that synaptic thing

 Which program are you trying to install?

---

### Post by erfahren on 2008-01-20
> **markusgrey said:**
> i dont get that synaptic thing
lets start from "scratch" here

first - what package are you wanting to install?

second - what version of Ubuntu?

---

### Post by erfahren on 2008-01-20
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by kodak on 2008-01-20
there's a pretty good chance that the poster does not have the compiling software to compile yet

:)
if you have time 
[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by erfahren on 2008-01-20
> **kodak said:**
> there's a pretty good chance that the poster does not have the compiling software to compile yet

:)
if you have time 
[http://ubuntuguide.org/](http://ubuntuguide.org/)
agreed - when a new user posts about compiling software, it's a good idea to first first ensure that the /etc/apt/sources.list is complete and the see if the program is available through Synaptic

note to OP: "apt" is the package management system in Ubuntu - Synaptic is basically a GUI for it - Add/Remove Programs is (in effect) a simplified version of Synaptic

---

### Post by markusgrey on 2008-01-20
jamie@ubuntujamie:~$ `cd tmp/jamie/brasero-0.7.0
> ./configure
> make
> make install
> `cd tmp/jamie/brasero-0.7.0
./configure
make
make install
bash: cd: tmp/jamie/brasero-0.7.0: No such file or directory
bash: ./configure: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
bash: make:: command not found
bash: ./configure: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: Nothing to be done for `install'.
jamie@ubuntujamie:~$

---

### Post by markusgrey on 2008-01-20
> **erfahren said:**
> lets start from "scratch" here

first - what package are you wanting to install?

second - what version of Ubuntu?

1st. Brasero
2nd. Breezy Badger

---

### Post by erfahren on 2008-01-20
> **markusgrey said:**
> jamie@ubuntujamie:~$ `cd tmp/jamie/brasero-0.7.0
> ./configure
> make
> make install
> `cd tmp/jamie/brasero-0.7.0
./configure
make
make install
bash: cd: tmp/jamie/brasero-0.7.0: No such file or directory
bash: ./configure: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
bash: make:: command not found
bash: ./configure: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: Nothing to be done for `install'.
jamie@ubuntujamie:~$
don't enter the commands all at once - enter one at a time

---

### Post by markusgrey on 2008-01-20
Well nothing happened when i did them 1 at a time

---

### Post by corney91 on 2008-01-20
You shouldn't need to compile Brasero. Open Synaptic > Click search > search brasero > check the box 'mark for installation' > click apply.

Or by command line: sudo apt-get install brasero

---

### Post by erfahren on 2008-01-20
I searched on the internet a little - it used to be called "bonfire" - search Synaptic for that as well

the newer package of  Brasero that you have may require newer, updated libraries and the like to compile it.

---

### Post by markusgrey on 2008-01-20
well its not in my synaptic

---

### Post by JoshuaRL on 2008-01-20
What is the output of:

```

sudo gedit /etc/apt/sources.list

```

---

### Post by markusgrey on 2008-01-20
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by JoshuaRL on 2008-01-20
Okay, that would be your problem.  You can either go to Preferences -> Administration -> Software Sources and add everything you see there, or in the file you just opened remove every # you see in front of a line that starts with "deb".  That will open all the sources for updates.  Then go into Update Manager and you should have over 100 updates.  After you're done with that, you can do the other steps detailed here.

---

### Post by markusgrey on 2008-01-20
when i open the update manager it closes in half a second

---

### Post by markusgrey on 2008-01-20
Here are my accounts for Gaim if anyone wants to im session me
yahoo    jamie_ruston2
aim        ahot1pocket
msn       markusgrey

---

### Post by JoshuaRL on 2008-01-20
Okay.  Try:

```

sudo apt-get update

```

and then when that's done:

```

sudo apt-get upgrade

```

That should work.  And if it doesn't, it should show an error message.

---

### Post by JoshuaRL on 2008-01-20
> **markusgrey said:**
> Here are my accounts for Gaim if anyone wants to im session me
yahoo    jamie_ruston2
aim        ahot1pocket
msn       markusgrey

For one-on-one help chat works pretty well, but I prefer the forums.  That way if someone else has the same problem they can find the issue from your solved thread.

---

### Post by markusgrey on 2008-01-20
jamie@ubuntujamie:~$ sudo apt-get update
Password:
E: Type 'Uncomment' is not known on line 4 in source list /etc/apt/sources.list
jamie@ubuntujamie:~$ Uncomment
bash: Uncomment: command not found
jamie@ubuntujamie:~$ sudo apt-get upgrade
E: Type 'Uncomment' is not known on line 4 in source list /etc/apt/sources.list
E: The list of sources could not be read.
jamie@ubuntujamie:~$
jamie@ubuntujamie:~$

---

### Post by markusgrey on 2008-01-20
thats what happened

---

### Post by CupofDice on 2008-01-20
You weren't supposed to uncomment everything, just the urls starting with deb. Open up /etc/apt/sources.list again, and add the TWO comments back to where they were. Where there was only one comment, keep it the same.

---

### Post by JoshuaRL on 2008-01-20
Alright, I think you took out too many #s.  I looked at your old /etc/apt/sources.list and if you uncommented the right parts it should look like:

```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

If not you can either fix is so it does, or just copy over this one.  Then save the file and try those terminal commands again.

---

### Post by markusgrey on 2008-01-20
where do i comment

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


 Uncomment the following two lines to fetch updated software from the network
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

 Uncomment the following two lines to fetch major bug fix updates produced
 after the final release of the distribution.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

 Uncomment the following two lines to add software from the 'universe'
 repository.
 N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
 team, and may not be under a free licence. Please satisfy yourself as to
 your rights to use the software. Also, please note that software in
 universe WILL NOT receive any review or updates from the Ubuntu security
 team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

 Uncomment the following two lines to add software from the 'backports'
 repository.
 N.B. software from this repository may not have been tested as
 extensively as that contained in the main release, although it includes
 newer versions of some applications which may provide useful features.
 Also, please note that software in backports WILL NOT receive any review
 or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by markusgrey on 2008-01-20
This is what happened

jamie@ubuntujamie:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
  404 Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  404 Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
  404 Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
  404 Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Sources
  404 Not Found [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Sources
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/bin](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/bin) ary-i386/Packages.gz  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restrict](http://security.ubuntu.com/ubuntu/dists/breezy-security/restrict) ed/binary-i386/Packages.gz  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/sou](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/sou) rce/Sources.gz  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restrict](http://security.ubuntu.com/ubuntu/dists/breezy-security/restrict) ed/source/Sources.gz  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe) /binary-i386/Packages.gz  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe) /source/Sources.gz  404 Not Found
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i38](http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i38) 6/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/bina](http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/bina) ry-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sou](http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sou) rces.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/sour](http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/sour) ce/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary](http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary) -i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/source](http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/source) /Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/bi](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/bi) nary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restric](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restric) ted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/so](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/so) urce/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restric](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restric) ted/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/) binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restr](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restr) icted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/unive](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/unive) rse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multi](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multi) verse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/) source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restr](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restr) icted/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/unive](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/unive) rse/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multi](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multi) verse/source/Sources.gz  404 Not Found [IP: 91.189.88.46 80]
Reading package lists... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Pa ckages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary -i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restric ted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restr icted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/univers e Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_univers e_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates /main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-upd ates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates /restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_bree zy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backpor ts/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-b ackports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backpor ts/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_br eezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or direct ory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backpor ts/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_bree zy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backpor ts/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_br eezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or direct ory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-securi ty_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy- security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-se curity_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead.
jamie@ubuntujamie:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Pa ckages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary -i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restric ted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restr icted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/univers e Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_univers e_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates /main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-upd ates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates /restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_bree zy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backpor ts/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-b ackports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backpor ts/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_br eezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or direct ory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backpor ts/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_bree zy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backpor ts/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_br eezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or direct ory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-securi ty_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy- security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-se curity_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
jamie@ubuntujamie:~$  apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied )
E: Unable to lock the list directory
jamie@ubuntujamie:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Pa ckages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary -i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restric ted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restr icted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/univers e Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_univers e_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates /main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-upd ates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates /restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_bree zy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backpor ts/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-b ackports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backpor ts/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_br eezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or direct ory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backpor ts/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_bree zy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backpor ts/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_br eezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or direct ory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-securi ty_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy- security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-se curity_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
jamie@ubuntujamie:~$ sudo apt-get upgrade

---

### Post by JoshuaRL on 2008-01-20
Just copy the one I provided over.  If you want to see the difference, every line that begins with "deb" needs to NOT have a # in front of it.  Anywhere with two #s is instruction or documentation directly to you the user, and is not of use to the operating system.  When you take out the solitary #s it allows APT to search those places for updates.

---

### Post by Kilz on 2008-01-20
[shipit may be a good solution]("https://shipit.ubuntu.com/") to the problem, are we sure the breezy repos still exist?

---

### Post by markusgrey on 2008-01-20
well i do have your sources list that you gave me put as mine

---

### Post by oldos2er on 2008-01-20
> **markusgrey said:**
>  Breezy Badger

 I think the Breezy repos don't exist anymore.

---

### Post by markusgrey on 2008-01-20
> **oldos2er said:**
> I think the Breezy repos don't exist anymore.

So does that mean i am screwed?

---

### Post by JoshuaRL on 2008-01-20
> **oldos2er said:**
> I think the Breezy repos don't exist anymore.

Dude, you're right.  I forgot that.

Well, no it doesn't mean you're screwed.  You'll need to upgrade to the newest version.  Fortunately there's a sticky at the top of the Absolute Beginners Forum that explains how to upgrade to Gutsy Gibbon.  Then all the things you need will be there.  Honestly, you should be running the newest version unless there's some legitimate reason not to.  I mean, why not upgrade if it's free!  Plus, your version is two years out of date.  How did you get that CD?

---

### Post by CupofDice on 2008-01-20
I checked you post history (well, just read a bit of it), and I think I understand your problem. I think the alternative install discs are smaller than 700 mb (I have not the slightest clue), and you could try searching google for a version of any burner for breezy. Also does Breezy have a default burner, or did that not come till later?

This may help. Or maybe not.

[https://launchpad.net/ubuntu/breezy/+source/nautilus-cd-burner/](https://launchpad.net/ubuntu/breezy/+source/nautilus-cd-burner/)

Also you can order the cd for free from canonical.

---

### Post by markusgrey on 2008-01-20
my dad downloaded it 2 years ago when he was trying to mess around with linux

---

### Post by kodak on 2008-01-20
:lolflag:

---

### Post by JoshuaRL on 2008-01-20
> **markusgrey said:**
> my dad downloaded it 2 years ago when he was trying to mess around with linux

Sweet.  Is there any way you can get him to burn you off a newer version?  We'll help you if you have any problems.

If not, then Cup of Dice is right.  You'll need to download and install one of those cd burners and use that to burn off Gutsy.  But I'm sure it will make everything much easier.

---

