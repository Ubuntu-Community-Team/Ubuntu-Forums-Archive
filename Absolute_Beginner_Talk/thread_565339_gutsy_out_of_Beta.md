---
title: "gutsy out of Beta?"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by metalpancake on 2007-10-02
Does anyone know when Gutsy will come out of Beta? I am quite anxios to try it but I don't really want to try the beta because of the instability.

---

### Post by nowshining on 2007-10-02
so far gutsy has been really stable :) at least for me - however I did remove junk programs i didn't need or use, however to answer ur question October 18th is the official release date of Gutsy. :)

---

### Post by overdrank on 2007-10-02
> **metalpancake said:**
> Does anyone know when Gutsy will come out of Beta? I am quite anxios to try it but I don't really want to try the beta because of the instability.

Estimated Oct.18 I believe. :)

---

### Post by metalpancake on 2007-10-02
thank you. I can't wait!:)

---

### Post by nowshining on 2007-10-02
ur welcome. Also ur Avatar makes me hungry for some pancakes. :D :p

---

### Post by metalpancake on 2007-10-02
lol. I wanted to use something that related to my username, which is just a random word I picked up one time!

---

### Post by metalpancake on 2007-10-02
i like your one too, it's something different

---

### Post by nowshining on 2007-10-02
thanks, If I remember correctly I found it off another forum from another user and have liked it since. :) I also use it as my logo picture on the computer. :P

---

### Post by metalpancake on 2007-10-02
I just found mine on google images and scaled it down to fit the avatar parameters!

---

### Post by nowshining on 2007-10-02
ah google yes I am trying to switch over to [www.clusty.com](www.clusty.com) :) and get away from google plus they also have clusters on the side to make finding the relevant article or articles easier, etc.. :)

---

### Post by hyper_ch on 2007-10-02
Well, a linux beta is about equal to a windoze stable version ;)

---

### Post by nowshining on 2007-10-02
> **hyper_ch said:**
> Well, a linux beta is about equal to a windoze stable version ;)

Your absolutely wrong - It's More Stable and A million times better than a stable version of windows. :p

---

### Post by metalpancake on 2007-10-02
yeah, I dual boot winxp and ubuntu feisty and I spent most of my time on Ubuntu, including my forum time!

---

### Post by nowshining on 2007-10-02
yes u'll become one of us in no time :P echoes: one of us, one of us, one of us......."

---

### Post by metalpancake on 2007-10-02
lol. I sure hope so!:)

---

### Post by metalpancake on 2007-10-02
One other thing I was wondering is how to install programs that give you a tar.gz file when you download them. I have quite a few programs like this!

---

### Post by nowshining on 2007-10-02
u'll have to compile them thru the terminal

if all is well
however since ur a newbie It's higly suggestable to only download and use .deb files yes Ubuntu is based of the Debian unstable branch. :) and Debian of course.

edit: of course until you get used to using ubuntu and linux and have read up more on it. Oh and is one of them the mozilla build firefox? if so use ubuntuzilla to auto download/compile, etc.. it for u - yes it backs up the ubuntu version of firefox first. ubuntuzilla has their own forum here.

---

### Post by metalpancake on 2007-10-02
no, it's actually a video editing program called kdenlive. Yes, I have up untill now been using programs downloaded through synaptic package manager, add/remove programs or from .deb files.:)

---

### Post by metalpancake on 2007-10-02
I might also try ubuntuzilla. it sounds good. can you just google it to find it?

---

### Post by nowshining on 2007-10-02
ubuntuzilla installs the Main build again build of firefox and gets rid of the ubuntu version breaking the reliance on updates and waiting thru ubuntu is gone, also the benefit is that once installed you can easily update from one version of firefox to another by just going to a terminal (updates require root privelages) but first exiting out firefox and typing sudo firefox then going to the help - check for updates and then restarting when asked to. :)

[http://ubuntuforums.org/forumdisplay.php?f=46](http://ubuntuforums.org/forumdisplay.php?f=46)

```

Ubuntuzilla:
Scripts automating the installation of the latest versions of Mozilla software with minimal disturbance to the system.

```

---

### Post by nowshining on 2007-10-02
answer for compiling

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by metalpancake on 2007-10-02
yeah, thanks. I will read that page. :)

---

### Post by nowshining on 2007-10-02
ur welcome. Also note that many programs have an install readme file that should also tell u and some need more commands to complete then the basic ones such as the patch, etc..

---

### Post by metalpancake on 2007-10-02
ok, so for this bit of software I found instructions on how to install it. It told me ```
Installing from tarball :

Download the tarball into a directory, and unpack it :

tar -xzf kdenlive-x.x.x-src.tar.gz

where x.x.x is the version number.
(your reading this so you've already done this, right?)

Once extracted, you can enter the directory and configure and build kdenlive.

cd kdenlive
./configure --prefix=`kde-config --prefix`
make

To install, become root:

su
(enter root password at prompt)
make install

./configure takes a number of options, type ./configure --help to
discover what these are. The most important one is --prefix, which
specifies where your KDE installation is when installing. For Mandrake,
use :

./configure --prefix=/usr

Once installed, you can start Kdenlive by typing "kdenlive".

Note that you should also install Piave to do anything useful with Kdenlive. See
the README file for details.

Have Fun!


Installing from CVS
===================
if you are checking out CVS :

Connect to the CVS repository:
cvs -d:pserver:anonymous@cvs.kdenlive.sourceforge.net:/cvsroot/kdenlive login

When asked for a password, press return (there is no password). Then checkout Kdenlive source code:
cvs -z3 -d:pserver:anonymous@cvs.kdenlive.sourceforge.net:/cvsroot/kdenlive co kdenlive

Create a ./configure script:
cd kdenlive
sh bootstrap

Compile Kdenlive:
./configure --prefix=`kde-config --prefix`
make

To install, become root

su
(enter root password at prompt)

make install

./configure takes a number of options, type ./configure --help to
discover what these are. The most important one is --prefix, which
specifies where your KDE installation is when installing. For Mandrake,
use :

./configure --prefix=/usr

Once installed, you can start Kdenlive by typing "kdenlive".

Note that you should also install Piave to do anything useful with Kdenlive. See
the README file for details.

Have Fun!


Basic Installation
==================

   These are generic installation instructions.

   The `configure' shell script attempts to guess correct values for
various system-dependent variables used during compilation.  It uses
those values to create a `Makefile' in each directory of the package.
It may also create one or more `.h' files containing system-dependent
definitions.  Finally, it creates a shell script `config.status' that
you can run in the future to recreate the current configuration, a file
`config.cache' that saves the results of its tests to speed up
reconfiguring, and a file `config.log' containing compiler output
(useful mainly for debugging `configure').

   If you need to do unusual things to compile the package, please try
to figure out how `configure' could check whether to do them, and mail
diffs or instructions to the address given in the `README' so they can
be considered for the next release.  If at some point `config.cache'
contains results you don't want to keep, you may remove or edit it.

   The file `configure.in' is used to create `configure' by a program
called `autoconf'.  You only need `configure.in' if you want to change
it or regenerate `configure' using a newer version of `autoconf'.

The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes a while.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Type `make install' to install the programs and any data files and
     documentation.

  4. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  

Compilers and Options
=====================

   Some systems require unusual options for compilation or linking that
the `configure' script does not know about.  You can give `configure'
initial values for variables by setting them in the environment.  Using
a Bourne-compatible shell, you can do that on the command line like
this:
     CC=c89 CFLAGS=-O2 LIBS=-lposix ./configure

Or on systems that have the `env' program, you can do it like this:
     env CPPFLAGS=-I/usr/local/include LDFLAGS=-s ./configure

Compiling For Multiple Architectures
====================================

   You can compile the package for more than one kind of computer at the
same time, by placing the object files for each architecture in their
own directory.  To do this, you must use a version of `make' that
supports the `VPATH' variable, such as GNU `make'.  `cd' to the
directory where you want the object files and executables to go and run
the `configure' script.  `configure' automatically checks for the
source code in the directory that `configure' is in and in `..'.

   If you have to use a `make' that does not supports the `VPATH'
variable, you have to compile the package for one architecture at a time
in the source code directory.  After you have installed the package for
one architecture, use `make distclean' before reconfiguring for another
architecture.

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

   There may be some features `configure' can not figure out
automatically, but needs to determine by the type of host the package
will run on.  Usually `configure' can figure that out, but if it prints
a message saying it can not guess the host type, give it the
`--host=TYPE' option.  TYPE can either be a short name for the system
type, such as `sun4', or a canonical name with three fields:
     CPU-COMPANY-SYSTEM

See the file `config.sub' for the possible values of each field.  If
`config.sub' isn't included in this package, then this package doesn't
need to know the host type.

   If you are building compiler tools for cross-compiling, you can also
use the `--target=TYPE' option to select the type of system they will
produce code for and the `--build=TYPE' option to select the type of
system on which you are compiling the package.

Sharing Defaults
================

   If you want to set default values for `configure' scripts to share,
you can create a site shell script called `config.site' that gives
default values for variables like `CC', `cache_file', and `prefix'.
`configure' looks for `PREFIX/share/config.site' if it exists, then
`PREFIX/etc/config.site' if it exists.  Or, you can set the
`CONFIG_SITE' environment variable to the location of the site script.
A warning: not all `configure' scripts look for a site script.

Operation Controls
==================

   `configure' recognizes the following options to control how it
operates.

`--cache-file=FILE'
     Use and save the results of the tests in FILE instead of
     `./config.cache'.  Set FILE to `/dev/null' to disable caching, for
     debugging `configure'.

`--help'
     Print a summary of the options to `configure', and exit.

`--quiet'
`--silent'
`-q'
     Do not print messages saying which checks are being made.

`--srcdir=DIR'
     Look for the package's source code in directory DIR.  Usually
     `configure' can determine that directory automatically.

`--version'
     Print the version of Autoconf used to generate the `configure'
     script, and exit.

`configure' also accepts some other, not widely useful, options.

```

---

### Post by metalpancake on 2007-10-02
how exactly do I do all that?:lolflag:

---

### Post by nowshining on 2007-10-02
well guess what :) u don't have to it's in the Ubuntu repos  open up the synaptic package manager do a search for kdenlive hit enter and it should be the first if not let me know..

---

### Post by nowshining on 2007-10-02
oh for if using gnome it's - system - adminstration - synaptic package manager

---

### Post by metalpancake on 2007-10-02
No, nothing came up. yes i am using gnome by the way...:)

---

### Post by nowshining on 2007-10-02
okay open up software sources and under Ubuntu Software tab - if it's the same as feisty check all but the source code - exit and then when asked to reload let it - it will go out to the internet to update the package info. and now try again with the synaptic package manager.

---

### Post by metalpancake on 2007-10-02
yeah, I did all that, but it's still not there!:( maybe it has something to do with the fact that when it was reloading it only managed to do 49 out of the 50 files. I had to cancel it and try the package manager.:confused:

---

### Post by nowshining on 2007-10-02
why did u cancel it it was updating to be able get the info. about the programs in the repos. (repo or repos = repositories by the way)...

---

### Post by metalpancake on 2007-10-02
yeah but the thing is i looked at the packages it had to install and one of them had 'failed' written next to it while the others all had 'done'

---

