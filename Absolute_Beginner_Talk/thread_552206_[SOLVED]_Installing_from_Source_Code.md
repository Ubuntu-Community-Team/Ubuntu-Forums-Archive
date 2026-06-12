---
title: "[SOLVED] Installing from Source Code"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by lordfkiller on 2007-09-16
Hello.

I am trying to install Mono Core 1.2.5 from source code. When I run ./configure, I get an error. Here is the result of ./configure:
[INDENT]checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/bash: /home/farshid/Downloads/Mono: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether ln -s works... yes
./configure: line 2804: ./libtool: No such file or directory
checking host platform characteristics... ok
checking for gcc... gcc
checking for gcc... (cached) gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.[/INDENT]
If I run make after that, I get: make: *** No targets specified and no makefile found.  Stop.

Any help would be appreciated.

Note: Please do NOT remind me that I could use Synaptic and get an older, tested version. :)

---

### Post by reckless2k2 on 2007-09-16
sudo apt-get build-essential


then try it...if you have problems then.....post the "See `config.log' for more details." details here.

---

### Post by lordfkiller on 2007-09-16
sudo apt-get build-essential --> E: Invalid operation build-essential

Config.log: (truncated, see next post)
[INDENT]This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes...
...configure: exit 77[/INDENT]

---

### Post by Viskovitz on 2007-09-16
He meant:
```
sudo apt-get install build-essential
```
You got invalid operation because the operation is install, not the name of the package. Then retry to compile the code.

Good luck.

---

### Post by lordfkiller on 2007-09-16
Thanks! It worked :D . This package contained some compilers, right?

But I got a new error: configure: error: You need to install bison

:(

---

### Post by tvrg on 2007-09-16
the error tells you exactly what to do

apt-get install bison

i'm not sure why you need mono from source (it's in the repositories) but if you do, try to read the install docs on the mono site.

---

### Post by lordfkiller on 2007-09-16
I am installing from source code because I want the latest version. Also, I am following the instructions from Mono website.

Thanks for your help. I used to receive the first answer 50 minutes after I start a thread. This time I got an answer in 4 minutes! You guys make Microsoft cry ;)

---

### Post by tvrg on 2007-09-16
you need to make sure you've got all dependencies installed, if you get a "you need to install" or "could not find" error, you have to install something else first. if it still fails post back

---

### Post by lordfkiller on 2007-09-16
./configure --> 
[INDENT]checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 1.3.11) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
[/INDENT]
sudo apt-get install glib-2.0 --> 
[INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package glib-2.0
[/INDENT]

Any idea?

---

### Post by tvrg on 2007-09-16
install libglib2.0-dev ?

---

### Post by tvrg on 2007-09-16
if you are compiling stuff you usually need the -dev version of the package installed, not just the package

---

### Post by lordfkiller on 2007-09-16
Yup!

---

### Post by lordfkiller on 2007-09-16
Last lines of make command result:
[INDENT]make[4]: *** [libmono.la] Error 9
make[4]: Leaving directory `/home/farshid/Downloads/Mono Project/Source Code/Mono Core/1.2.5/mono-1.2.5/mono-1.2.5/mono/mini'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/farshid/Downloads/Mono Project/Source Code/Mono Core/1.2.5/mono-1.2.5/mono-1.2.5/mono/mini'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/farshid/Downloads/Mono Project/Source Code/Mono Core/1.2.5/mono-1.2.5/mono-1.2.5/mono'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/farshid/Downloads/Mono Project/Source Code/Mono Core/1.2.5/mono-1.2.5/mono-1.2.5'
make: *** [all] Error 2
[/INDENT]

What should I do?

---

### Post by lordfkiller on 2007-09-16
Any idea?

---

### Post by tvrg on 2007-09-17
i'm afraid i'll need the lines before that.
the error occurs earlyer

---

### Post by lordfkiller on 2007-09-17
The entire command result is attached.

---

### Post by tvrg on 2007-09-17
permission denied, did you try it as root first and as regular user now?

---

### Post by lordfkiller on 2007-09-17
I think I first tried a regular user and then retried as root(sudo). Maybe I have run make command as root in other cases before.

---

### Post by tvrg on 2007-09-17
try removing everything (probably as root) and starting over as a regular user  then :)

the make command cannot remove some files at the moment

---

### Post by lordfkiller on 2007-09-17
What do u mean from everything? Should I delete the source code and extract again? Or remove all dependencies I've installed as well?

---

### Post by tvrg on 2007-09-17
just the source, not the dependencies

---

### Post by lordfkiller on 2007-09-17
I just extracted again(using GUI, not from command-line). Ran ./configure and make, and I got the same error when I ran make.

Should I start over as root?

---

### Post by lordfkiller on 2007-09-17
Got the same result with sudo.

---

### Post by tvrg on 2007-09-17
is that a nightly build you are using

---

### Post by lordfkiller on 2007-09-17
---

---

### Post by lordfkiller on 2007-09-17
I don't know the meaning of nightly build(please let me know). The problem was just solved though!

I extracted everything to /opt and it compiled successfully :D
The only problem I faced after that was an error when installing the package which was solved by forcing overwrite (--force-overwrite).

Although I have installed the latest version of Mono Core, Mono Common, Mono Runtime etc are the old version in Synaptic and only the package I've built and installed is shown with version 1.2.5 . Why?

Thanks everyone for helping me :)

---

### Post by tvrg on 2007-09-17
if you compile from source synaptic doesn't know about it, so it won't be auto updated either

make sure you keep the source tree so you can do a make uninstall later on

---

### Post by lordfkiller on 2007-09-17
But I did not use "make install". I used "checkinstall --install=no" and installed created package using dpkg.

Is it still okay for Syanptic to show older version or I really do not have new version installed?

---

### Post by tvrg on 2007-09-17
if you installed using dpkg it should list the new version

try 
```
dpkg -l | grep mono
```

---

### Post by lordfkiller on 2007-09-17
Again old version:

ii  libmono-accessibility2.0-cil               1.2.3.1-1ubuntu1                       Mono Accessibility library
ii  libmono-cairo1.0-cil                       1.2.3.1-1ubuntu1                       Mono Cairo library
ii  libmono-corlib1.0-cil                      1.2.3.1-1ubuntu1                       Mono core library (1.0)
ii  libmono-corlib2.0-cil                      1.2.3.1-1ubuntu1                       Mono core library (2.0)
ii  libmono-data-tds2.0-cil                    1.2.3.1-1ubuntu1                       Mono Data Library
ii  libmono-peapi1.0-cil                       1.2.3.1-1ubuntu1                       Mono PEAPI library
ii  libmono-peapi2.0-cil                       1.2.3.1-1ubuntu1                       Mono PEAPI library
ii  libmono-security2.0-cil                    1.2.3.1-1ubuntu1                       Mono Security library
ii  libmono-sharpzip2.84-cil                   1.2.3.1-1ubuntu1                       Mono SharpZipLib library
ii  libmono-sqlite2.0-cil                      1.2.3.1-1ubuntu1                       Mono Sqlite library
ii  libmono-system-data2.0-cil                 1.2.3.1-1ubuntu1                       Mono System.Data Library
ii  libmono-system-web2.0-cil                  1.2.3.1-1ubuntu1                       Mono System.Web Library
ii  libmono-system1.0-cil                      1.2.3.1-1ubuntu1                       Mono System libraries (1.0)
ii  libmono-system2.0-cil                      1.2.3.1-1ubuntu1                       Mono System libraries (2.0)
ii  libmono0                                   1.2.3.1-1ubuntu1                       libraries for the Mono JIT
ii  libmono2.0-cil                             1.2.3.1-1ubuntu1                       Mono libraries (2.0)
ii  mono                                       1.2.5-1                                Mono 1.2.5 Core.
ii  mono-common                                1.2.3.1-1ubuntu1                       common files for Mono
ii  mono-gac                                   1.2.3.1-1ubuntu1                       Mono GAC tool
ii  mono-jit                                   1.2.3.1-1ubuntu1                       fast CLI JIT/AOT compiler for Mono
ii  mono-runtime                               1.2.3.1-1ubuntu1                       Mono runtime
rc  mono-xsp                                   1.2.1-1ubuntu1                         simple web server to run ASP.NET application
rc  mono-xsp2                                  1.2.1-1ubuntu1                         simple web server to run ASP.NET application
rc  monodevelop                                0.12+dfsg-1ubuntu1                     C#/Boo/Java/Nemerle/ILasm/ASP.NET Developmen
rc  monodoc-browser                            1.2.3-0ubuntu1                         MonoDoc GTK+ based viewer

---

### Post by tvrg on 2007-09-17
except for mono itself
ii mono 1.2.5-1 Mono 1.2.5 Core.

wtf, did you build everything and did you install everything?

it appears your mono is updated but all the rest isn't

---

### Post by lordfkiller on 2007-09-17
Yes. I did compile it successfully and installed it. When compiling, it said that classes for GIF won't be built. And when installing, I got an error. So I ran it with --force-overwrite and it was installed.

Is there a way to uninstall everything including the old Mono and install the new one?

---

### Post by lordfkiller on 2007-09-17
It seems that installing the new version does not update the old one(I don't see new runtime though, only the old packages). Anyway... I am currently trying to update using their SVN. This is what Mono website recommends. Also, I need the source code.

I'll post the result.

---

### Post by tvrg on 2007-09-18
to completely uninstall you can use apt-get remove --purge

---

### Post by lordfkiller on 2007-09-18
I just compiled and installed (using make) from SVN. The version in Synaptic is still old, but this time it is usual as I have used make install, not checkinstall. mono --version returns 1.2.5 though.

I cannot uninstall that package. I said in a previous post that I have forced dpkg to overwrite if needed when installing the package I'd created. Therefore, it's made some changes in GCC files. As a result, when I uninstall that package, the C compiler does not work. Fortunately when I re-installed it, everything was okay. Let's leave it there ;)

Maybe Mono was updated with that package, too. I prefer to use SVN anyway.

Once again, thanks for your help.

---

