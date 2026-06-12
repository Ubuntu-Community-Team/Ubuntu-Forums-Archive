---
title: "downloaded tar.gz file--what to do afterwards?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by prince_alfie on 2007-05-07
I just downloaded the rhythmbox-0.9.6.tar.gz and I am wondering what I should do to compile to get replace the rhythmbox-0.9.3 I downloaded from the repository. Do I just download it to the desktop and then double click on it to run or do I need commands from the terminal?

---

### Post by Bachstelze on 2007-05-07
Extract the tarball with

```
tar xzvf rhythmbox-0.9.6.tar.gz
```

Then look around in the extracted dir, there should be a README or something.

---

### Post by fakie_flip on 2007-05-07
Extract the files.

tar -xvzf rhythmbox-0.9.6.tar.gz

man tar

cd rhythmbox-0.9.6

These are the standard commands for compiling in Linux.

./configure

make

sudo make install

---

### Post by fakie_flip on 2007-05-07
Maybe you should uninstall the Rhythmbox you have before compiling and installing the new one. You can do that from Synaptic.

---

### Post by silent1643 on 2007-05-07
is there not a package manager where you can double click on the tar file and "unzip" ?

---

### Post by fakie_flip on 2007-05-07
> **silent1643 said:**
> is there not a package manager where you can double click on the tar file and "unzip" ?

file-roller

---

### Post by fakie_flip on 2007-05-07
Right click on the file and choose "Extract here"

---

### Post by prince_alfie on 2007-05-07
Sounds good... looks like compiling it should be straightforward now :)

---

### Post by prince_alfie on 2007-05-07
> **fakie_flip said:**
> Extract the files.

tar -xvzf rhythmbox-0.9.6.tar.gz

man tar

cd rhythmbox-0.9.6

These are the standard commands for compiling in Linux.

./configure

make

sudo make install

I got to the cd rhythmbox-0.9.6... it says: albertwang@albertwang-laptop:~/rhythmbox-0.9.6$

should I type in

sudo make install rhythmbox-0.9.6 now?

---

### Post by fakie_flip on 2007-05-07
No, type this.

./configure

It may complain of missing dependency software. Then you will have to look in Synaptic for the software that is missing. After that run ./configure again until it does not give you anymore errors.

---

### Post by fakie_flip on 2007-05-07
Do the commands in the order I gave you. sudo make install is the last one you do.

---

### Post by prince_alfie on 2007-05-07
> **fakie_flip said:**
> No, type this.

./configure

It may complain of missing dependency software. Then you will have to look in Synaptic for the software that is missing. After that run ./configure again until it does not give you anymore errors.

I see... it gave me a configure: error: XML:: Parser perl module is required for intltool error... so should I look for a intltool in the Synaptic?

---

### Post by fakie_flip on 2007-05-07
Try installing this package from Synaptic.

libtotem-plparser-dev

Always get the packages ending with -dev. Those are needed for compiling aka development.

---

### Post by fakie_flip on 2007-05-07
Then run this again, and let me know what happens.

./configure

---

### Post by prince_alfie on 2007-05-07
> **fakie_flip said:**
> Then run this again, and let me know what happens.

./configure

Sounds good. I have to wait until I get home since I don't have wireless here at this location :) I will post any updates on this issue, thanks! :D

---

### Post by rich.bradshaw on 2007-05-07
What are the differences between this version and the version in the repos?

---

### Post by rich.bradshaw on 2007-05-07
Especially when the version in the repos is version 0.10.0?

---

### Post by fakie_flip on 2007-05-07
> **rich.bradshaw said:**
> Especially when the version in the repos is version 0.10.0?

I think he wants to learn how to compile software.

---

### Post by prince_alfie on 2007-05-07
Actually I'm installing rhythmbox on Xubuntu which isn't GNOME based but XCFE so the highest rhythmbox software only does 0.9.3. I really want to have my album art displayed so upgrading by compiling is the only way.

Unless I'm missing something in the repro?

---

### Post by gigaferz on 2007-05-07
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)


read this it'll help you

---

### Post by fakie_flip on 2007-05-07
Then you are probably missing some gnome dependencies and running ./configure will complain about those.

---

### Post by fakie_flip on 2007-05-07
You might want to use checkinstall while compiling. It creates a deb of what you are compiling, and so it is easier to manage and remove later.

---

### Post by prince_alfie on 2007-05-07
> **fakie_flip said:**
> Then you are probably missing some gnome dependencies and running ./configure will complain about those.

Actually not... surprisingly the rhythmbox 0.9.3 version didn't give me a single error when I installed it from the synpatic manager.

---

### Post by prince_alfie on 2007-05-07
Okay, I got this error:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
albertwang@albertwang-laptop:~/rhythmbox-0.9.6$ make
bash: make: command not found
albertwang@albertwang-laptop:~/rhythmbox-0.9.6$ sudo make install
Password:
sudo: make: command not found

What does that mean?

---

### Post by Bachstelze on 2007-05-07
```
sudo apt-get install build-essential libxml-parser-dev
```

that should get rid of that dependency but you will surely get new ones.

---

### Post by prince_alfie on 2007-05-07
> **HymnToLife said:**
> ```
sudo apt-get install build-essential libxml-parser-dev
```

that should get rid of that dependency but you will surely get new ones.

albertwang@albertwang-laptop:~$ sudo apt-get install build-essential libxml-parser-dev
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
albertwang@albertwang-laptop:~$

Hmm... any thoughts?

---

### Post by Bachstelze on 2007-05-07
Do you have Synaptic opened or something like that ? (You can also install those packages in Synaptic if you prefer.)

---

### Post by prince_alfie on 2007-05-07
> **HymnToLife said:**
> Do you have Synaptic opened or something like that ? (You can also install those packages in Synaptic if you prefer.)

I close Synaptic and I get this:

albertwang@albertwang-laptop:~$ sudo apt-get install build-essential libxml-parser-dev
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libxml-parser-dev
albertwang@albertwang-laptop:~$

---

### Post by jiminycricket on 2007-05-07
What about sudo apt-get install build-essential libxml-parser-perl ?

---

### Post by qamelian on 2007-05-07
> **prince_alfie said:**
> Actually I'm installing rhythmbox on Xubuntu which isn't GNOME based but XCFE so the highest rhythmbox software only does 0.9.3. I really want to have my album art displayed so upgrading by compiling is the only way.

Unless I'm missing something in the repro?

Well, your profile say you're a Feisty user and a quick:
```
apt-cache showpkg rhythmbox
```shows:```
Package: rhythmbox
Versions: 
0.10.0-0ubuntu2 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages

``` in the Feisty repos. It doesn't matter whether you're using Ubuntu, Kubuntu,  or Xubuntu, you'll be using the same repos.

---

### Post by fakie_flip on 2007-05-07
> **prince_alfie said:**
> Okay, I got this error:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
albertwang@albertwang-laptop:~/rhythmbox-0.9.6$ make
bash: make: command not found
albertwang@albertwang-laptop:~/rhythmbox-0.9.6$ sudo make install
Password:
sudo: make: command not found

What does that mean?

The make file does not get created until you get all the dependencies, and ./configure runs without errors, so you shouldn't try to run make or sudo make install yet.

---

### Post by fakie_flip on 2007-05-07
sudo apt-get build-dep rhythmbox

---

### Post by prince_alfie on 2007-05-07
> **jiminycricket said:**
> What about sudo apt-get install build-essential libxml-parser-perl ?

checking pkg-config is at least version 0.9.0... yes
checking for RB_CLIENT... yes
checking for RHYTHMBOX... configure: error: Package requirements (  gtk+-2.0 >= 2.6.0                                        libgnomeui-2.0  libglade-2.0                                             gnome-vfs-2.0 >= 2.7.  gnome-vfs-module-2.0) were not met:

No package 'libgnomeui-2.0' found
No package 'libglade-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables RHYTHMBOX_CFLAGS
and RHYTHMBOX_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


is the new error.

I'm a Feisty Fawn user on my Powerbook G4 but this is my iBook G3 I'm working on! :D

---

### Post by fakie_flip on 2007-05-08
run ./configure again. now what happens?

---

### Post by fakie_flip on 2007-05-08
sudo apt-get build-dep rhythmbox

---

### Post by prince_alfie on 2007-05-08
hello there,

after installing a ton of gnome libraries which ./configure asked for, I finally got rhythmbox-0.9.6 up and running. Everything works perfectly except for the album art part!!! OH well :D

I think that the album art is related to some python script? No clue except I need to figure out how to repair this.

---

### Post by fakie_flip on 2007-05-08
You need to recompile and add an option to ./configure when you run it next time so that support for album art will be in the make file. That might also require another dev package.

---

### Post by fakie_flip on 2007-05-08
Run ./configure --help to see what flags you need for configure to make Rhythmbox have support for album art. Here is an example from my computer.

```
chris@ubuntu:~/MY GAMES/sauerbraten/src/enet$ ./configure --help
`configure' configures libenet 12-12-2006 to adapt to many kinds of systems.

Usage: ./configure [OPTION]... [VAR=VALUE]...

To assign environment variables (e.g., CC, CFLAGS...), specify them as
VAR=VALUE.  See below for descriptions of some of the useful variables.

Defaults for the options are specified in brackets.

Configuration:
  -h, --help              display this help and exit
      --help=short        display options specific to this package
      --help=recursive    display the short help of all the included packages
  -V, --version           display version information and exit
  -q, --quiet, --silent   do not print `checking...' messages
      --cache-file=FILE   cache test results in FILE [disabled]
  -C, --config-cache      alias for `--cache-file=config.cache'
  -n, --no-create         do not create output files
      --srcdir=DIR        find the sources in DIR [configure dir or `..']

Installation directories:
  --prefix=PREFIX         install architecture-independent files in PREFIX
                          [/usr/local]
  --exec-prefix=EPREFIX   install architecture-dependent files in EPREFIX
                          [PREFIX]

By default, `make install' will install all the files in
`/usr/local/bin', `/usr/local/lib' etc.  You can specify
an installation prefix other than `/usr/local' using `--prefix',
for instance `--prefix=$HOME'.

For better control, use the options below.

Fine tuning of the installation directories:
  --bindir=DIR           user executables [EPREFIX/bin]
  --sbindir=DIR          system admin executables [EPREFIX/sbin]
  --libexecdir=DIR       program executables [EPREFIX/libexec]
  --sysconfdir=DIR       read-only single-machine data [PREFIX/etc]
  --sharedstatedir=DIR   modifiable architecture-independent data [PREFIX/com]
  --localstatedir=DIR    modifiable single-machine data [PREFIX/var]
  --libdir=DIR           object code libraries [EPREFIX/lib]
  --includedir=DIR       C header files [PREFIX/include]
  --oldincludedir=DIR    C header files for non-gcc [/usr/include]
  --datarootdir=DIR      read-only arch.-independent data root [PREFIX/share]
  --datadir=DIR          read-only architecture-independent data [DATAROOTDIR]
  --infodir=DIR          info documentation [DATAROOTDIR/info]
  --localedir=DIR        locale-dependent data [DATAROOTDIR/locale]
  --mandir=DIR           man documentation [DATAROOTDIR/man]
  --docdir=DIR           documentation root [DATAROOTDIR/doc/libenet]
  --htmldir=DIR          html documentation [DOCDIR]
  --dvidir=DIR           dvi documentation [DOCDIR]
  --pdfdir=DIR           pdf documentation [DOCDIR]
  --psdir=DIR            ps documentation [DOCDIR]

Program names:
  --program-prefix=PREFIX            prepend PREFIX to installed program names
  --program-suffix=SUFFIX            append SUFFIX to installed program names
  --program-transform-name=PROGRAM   run sed PROGRAM on installed program names

Optional Features:
  --disable-FEATURE       do not include FEATURE (same as --enable-FEATURE=no)
  --enable-FEATURE[=ARG]  include FEATURE [ARG=yes]
  --disable-dependency-tracking  speeds up one-time build
  --enable-dependency-tracking   do not reject slow dependency extractors
  --enable-crc32   enable CRC32 packet verification

Some influential environment variables:
  CC          C compiler command
  CFLAGS      C compiler flags
  LDFLAGS     linker flags, e.g. -L<lib dir> if you have libraries in a
              nonstandard directory <lib dir>
  CPPFLAGS    C/C++/Objective C preprocessor flags, e.g. -I<include dir> if
              you have headers in a nonstandard directory <include dir>
  CPP         C preprocessor

Use these variables to override the choices made by `configure' or to help
it to find libraries and programs with nonstandard names/locations.

chris@ubuntu:~/MY GAMES/sauerbraten/src/enet$
```

---

### Post by prince_alfie on 2007-05-08
Sounds good. I will give it a shot of course :) I will be doing it when I get back from my NYC trip next week :>

---

### Post by fakie_flip on 2007-05-08
You could have always installed openssh-server and no-ip would help too. Then you could have access to your computer at home from anywhere in the world.

---

