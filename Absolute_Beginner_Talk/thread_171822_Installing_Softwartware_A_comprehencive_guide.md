---
title: "Installing Softwartware A comprehencive guide"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by Omnios on 2006-05-07
[COLOR=Navy]How To Install Software outside of of Repositories a Comprehensive GUide[/COLOR]
 Writing a short guide on different aspects of installing software from tarballs, debs and .rpm packages.

 Tarballs:
 First you will need the following package from synaptic.
```
sudo apt-get update
sudo apt-get install build-essential
``` 
 Usualy there is a install text file that comes with the ttarball like this one.
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
 It is good to read it as sometimes there are special debian install options such as prefix though rare. 

 Anyways first untar the tarball. Cd to the directory where your tarball is.
Example:
 ```

tar -xvzf sensors-applet-0.7.3.tar.gz

``` 
 The basic install is as follows:
```

cd sensors-applet...
./configure
make
sudo make install

``` 
 Now for errors, while doing this you may come accross errors where you need a compiler or dependancy, it is pretty basic and the error will basicly tell you what you need which you can look up in synaptic and install. for ex: say there is an error where you need python-xml 2...., you could look up Python and or python XML and try to match the package mentioned though they are not allways named the same. Edit: also a common error when you already have something the comiler complains about is that it needs the dev version of the file.

 Checkinstall:
 Available in synaptic is a program called checkinstall, I raely like it a lot as it makes an entry in synaptic installed locally which can be easily uninstalled just like synaptic packages. 
Using checkinstall: Basicly checkinstall is used instead of make install
```

./configure
make
sudo checkinstall

``` Note checkinstall is not garanteed to work all the time and has some problems with some tarballs.
 
Deb packages:
Basicly very easy
```

Cd to package_directory
sudo dpkg -i package_name

```  the -i is for install.

RPM: Also not garenteed to work.
You need alian to convert and install a rpm package.
```
sudo apt-get update
sudo apt-get install alien

``` 
```
sudo alien -i filename.rpm
``` 
 I think the hardest aspect of installing is recovering from an error and finding the required packages and dependancies needed to complete the install. Lastly if you ar having problems feel free to post your install problem with the error messages and hopefully someone can help you with the problem.

Edit: this is a highly recomened install guide
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by aysiu on 2006-05-07
If you're going to do a comprehensive guide, why not include the easiest way to install software--Synaptic or apt-get?

You need a *sudo* in front of the *dpkg* command.

Finally, guides like this already exist:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://www.monkeyblog.org/ubuntu/installing.html](http://www.monkeyblog.org/ubuntu/installing.html)

---

### Post by sappman2 on 2006-05-07
[QUOTE=aysiu]If you're going to do a comprehensive guide, why not include the easiest way to install software--Synaptic or apt-get?

...He's helping us install packages that aren't in Synaptic, or haven't been updated in the repos in AGES.. (like GNUCash, KMyMoney,etc, which have enjoyed many bug fixes, but haven't been updated in our Ubuntu repositories) So far, his advice has been helpful to me in this regard... I'm attempting to compile the latest version of Gnucash as we speak.... if I don't completely crash and burn, I'll let you know how it went. ;)    Sometimes, though, compiling things like this can e almost impossible for a novice like myself. I've been unsuccessful at finding some of the various versions of libraries in our Ubuntu repositories that are required for compiling some "outsider" applications.

Hmmm... still compiling the makefile.... I'll get back to you.....

---

### Post by sappman2 on 2006-05-07
Hmmmm.... PC cabinet beginning to break a sweat.....


Processor beginning to glow throught the side of the cabinet.....




......You smell smoke?

---

### Post by aysiu on 2006-05-07
[QUOTE=sappman2]
...He's helping us install packages that aren't in Synaptic, or haven't been updated in the repos in AGES.. [/QUOTE] Which is why it should not be called "a comprehensive guide." It should be "guide to installing software outside the repositories."

---

### Post by Omnios on 2006-05-07
[QUOTE=aysiu]Which is why it should not be called "a comprehensive guide." It should be "guide to installing software outside the repositories."[/QUOTE]

 Well it will not let me change the post title but changed the top title and the Page description on top, wouldn't want anyone to get confused.

---

### Post by Omnios on 2006-05-07
[QUOTE=sappman2][QUOTE=aysiu]If you're going to do a comprehensive guide, why not include the easiest way to install software--Synaptic or apt-get?

...He's helping us install packages that aren't in Synaptic, or haven't been updated in the repos in AGES.. (like GNUCash, KMyMoney,etc, which have enjoyed many bug fixes, but haven't been updated in our Ubuntu repositories) So far, his advice has been helpful to me in this regard... I'm attempting to compile the latest version of Gnucash as we speak.... if I don't completely crash and burn, I'll let you know how it went. ;)    Sometimes, though, compiling things like this can e almost impossible for a novice like myself. I've been unsuccessful at finding some of the various versions of libraries in our Ubuntu repositories that are required for compiling some "outsider" applications.

Hmmm... still compiling the makefile.... I'll get back to you.....[/QUOTE]

 Have you checked out the backports on this forum. They are newer programs that are available through backports.

---

### Post by sappman2 on 2006-05-07
**Hey Omnios... thanks so much for your help.** Yours was the easiest page to follow... some others had a little too much "chit-chat" going on during the instructions.

I'm now running GNUCash 1.9.5 (the bleedeing edge version) compiled from a *TAR.GZ file downloaded from their website... thankfully, all the libraries and dependant files but "G-wrap 1.9.6" were available from the repos. I used your instructions for installing the new version of G-wrap from their website in a TAR.GZ file. Funny, but I've now had more success installing things from a TAR.GZ file than I have from *.DEB files.

By the way, if anyone is interested, I have a *.deb file for GnuCash 1.9.5 now... you'll have to find the dependancies, though... be sure to upgrade G-wrap to the latest version by going to [http://www.nongnu.org/g-wrap/](http://www.nongnu.org/g-wrap/) ad downloading the TAR.GZ, then using the above instructions for compiling. (Do this first.) Drop me a line and I'll email the *deb file to you.... I have yet to put it through it's paces fully, though....

---

### Post by jezjones on 2006-05-15
Hi there,

One question... 
I (foolishly) did some conversion of Alsa rpm to try and get a later driver than the one in dapper.
Now after installing the 3 debs i made i cannot boot, it is complaining that GLIBC is not 2.4
This is not a surprise as Ubuntu is not up to 2.4 yet... obviously a case of RPM Hell, which turned me away from RH in the first place.

So i know what the debs were called but i can't seem to match them to installed packages, so i can't seem to remove them.
Can you tell me how to find recent installed packages or how to get the package name (as apt / dselect knows the package) from the .deb file name.
Thanks

p.s. i am working at the recover console so please no-one tell me to click on installed packages in synaptic, thanks.

jez

---

### Post by Omnios on 2006-05-15
Check out [http://packages.ubuntulinux.org/breezy/]("http://packages.ubuntulinux.org/breezy/")

 Its a repository which has the Breezy packages, you should be able to find the packages you nee there and could possibly use wget to download them onto your Ubuntu

---

### Post by sixseat7 on 2006-07-19
Help...I just loaded the latest version of ubuntu. I'm now trying to load the gnucash 2.0.0. This is my first time using linux of any type. I downloaded the package. I extracted teh package. I did the ./configure command as specified above. I tried typing "make" next as specified, but it came up with an error "no targets specified and no makefile found". So what do i do next? I just want to get the software installed.

---

### Post by aysiu on 2006-07-19
Read this:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

Installing *gnucash* through Synaptic Package Manager is a lot easier than compiling it from source.

---

### Post by sixseat7 on 2006-07-20
i ead that article. thanks i learned a lot. unfortunately i didnt see gnucash 2.0.0 in synaptics. also, i was able to uncompress, and to ./configure, but when i went into the extracted directory and tried to run "make" it didnt work. Any thoughts?

---

### Post by aysiu on 2006-07-20
Is there something special about 2.0.0 that satisfies your needs in a way that 1.8.12 doesn't?

---

### Post by alan yeates on 2006-07-21
Well I for one appreciate any help on tarballs, having coped with a couple I am still stuck on installing Turboprint. As soon as I unpack it, installer runs but does not bring up the GUI, I don't get the chance to compile or make, and details given in the readme make it sound as if it was designed for the K desktop. Have installed Konqueror and build-essential, any other thoughts?

---

### Post by slimdog360 on 2006-07-21
> **sixseat7 said:**
> i ead that article. thanks i learned a lot. unfortunately i didnt see gnucash 2.0.0 in synaptics. also, i was able to uncompress, and to ./configure, but when i went into the extracted directory and tried to run "make" it didnt work. Any thoughts?
are you sure that when you ran the ./configure everything worked properly? Maybe try this in a terminal then do it again.
```
sudo aptitude install build-essential
```

---

