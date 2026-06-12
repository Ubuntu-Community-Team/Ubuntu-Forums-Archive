---
title: "Can't configure GnuPG 1.0.1"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by benjimouse on 2007-09-13
Hi,

OK, so I've recently installed Ubuntu feisty fawn on my computer having got utterly sick of windows. I didn't expect all this terminal stuff, but I'm trying to get my head round it. Anyway a program I need for work (GnuPG1.0.1) is giving me some problems:

I've downloaded gnu-1.0.1.tar.gz and decompressed it, so I've got a folder called gnupg-1.0.1 with this stuff in:

[PHP]root@benjithemouses-desktop:/var/tmp/gnupg-1.0.1# ls
ABOUT-NLS     AUTHORS    cipher        config.log    debian   INSTALL      mpi       README      TODO     zlib
acconfig.h    BUGS       confdefs.h    configure     doc      intl         NEWS      scripts     tools
acinclude.m4  ChangeLog  config.cache  configure.in  g10      Makefile.am  po        stamp-h.in  util
aclocal.m4    checks     config.h.in   COPYING       include  Makefile.in  PROJECTS  THANKS      VERSION[/PHP]
 Next thing I'm supposed to do is configure it, so I type "./configure" it says:

[PHP]root@benjithemouses-desktop:/var/tmp/gnupg-1.0.1# ./configure
loading cache ./config.cache
checking which static random module to use... default
checking whether use of /dev/random is requested... yes
checking whether use of extensions is requested... yes
checking whether assembler modules are requested... yes
checking whether memory debugging is requested... no
checking whether memory guard is requested... no
checking whether included zlib is requested... no
checking whether use of capabilities is requested... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking host system type... configure: error: can not guess host type; you must specify one
[/PHP]

I have worked out that I'm supposed to specify a 'host' as an option but I don't know what one is, or where to find the right thing to type (a name for the host? because in "install"it says: 

> Specifying the System Type
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

There isn't a "config.sub" in the folder but, it still asks for the host to be specified?

---

### Post by dreadlord_chris on 2007-09-13
it would be **much** easier to just install the _official_ GPG package - it's available in the repositories...
from the command-line:
```

sudo apt-get install gnupg

```
if you also want a GUI front-end to go with it:
```

sudo apt-get install gpgp

```
will install the Gnome version - replace _gpgp_ with _kgpg_ if you want the KDE version...

---

### Post by Maestro23 on 2007-09-13
Also for future reference, if you're going to compile a program from source... you need [COLOR="Red"]"build-essential"[/COLOR] installed first.  Check the following section out in the Feisty Starter's Guilde:[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_compile_a_program_from_source_code](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_compile_a_program_from_source_code)

*Installing from source can be a headache for someone new to linux.  Always check the repos first for a program like the person above posted.

Welcome to Ubuntu and Good luck.:guitar:

---

### Post by benjimouse on 2007-09-13
Thanks a lot, guys. I was hoping there would be an easier way
:lolflag:

---

### Post by dreadlord_chris on 2007-09-13
> **benjimouse said:**
> Thanks a lot, guys. I was hoping there would be an easier way
:lolflag:
no prob....
could you mark the thread [Solved], please?
Have fun!

---

