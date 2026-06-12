---
title: "cannot build package from source?"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by salvador dali on 2007-09-12
I downloaded the newest wesnoth build but when i try to build it from source i get an odd message at the end of the ./configure sequence:
```
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for intltool >= 0.34.0... 0.34.1 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking for glib-genmarshal... no
checking for dlltool... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```

Any suggestions on why my version of GCC can't create executables? Running the command via sudo doesn't work either. Thanks.

---

### Post by llamakc on 2007-09-12
EDIT: I assume the OP has gcc actually installed already. If not, see post below.

---

### Post by Celegorm on 2007-09-12
You need the build-essential package, I believe. ```
sudo apt-get install build-essential
```

---

### Post by reckless2k2 on 2007-09-12
sudo apt-get install build-essential

that should give you all you need with compilers and such. 

you need sudo anyway on last step of 5 step extract and build.

---

### Post by salvador dali on 2007-09-13
thanks guys. why wasn't that bundle into fiesty? just wondering. anyways thanks again.

---

### Post by ramjet_1953 on 2007-09-13
Don't forget that when building a Debian package from sourcecode you have to satisfy dependencies manually.

Often the site that you download the sourcecode from will list the dependencies and you will need to heed what they say.

Another thing is that you will also probably need to download both the regular package and the development package for most of the dependencies.

For example, if they say you need the widget.lib library, you will also almost certainly need widget.dev package.

Also, another thing to remember is that if you need to ask questions like this one, you probably need to do more reading on the subject of compiling from sourcecode before plunging in, anyway.

Regards,
Roger :cool:

---

### Post by salvador dali on 2007-09-13
any suggestions? on reading that is.

---

### Post by Maestro23 on 2007-09-13
> **salvador dali said:**
> any suggestions? on reading that is.

Basics: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Handling_.22.tar.bz.22_.28Tar.2FBZip.29_Archives](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Handling_.22.tar.bz.22_.28Tar.2FBZip.29_Archives)

*As stated above, when compiling from source, satisfying the dependencies is sorely on the user.  Consult the documentation for whatever program you're  trying to compile, it will tell you exactly what it needs.  Then you can use Synaptic to find the packages and install them.

Good luck.

---

### Post by apparle on 2007-09-13
The package has been bundled with the CD.
Enter the disc in the tray. By default it will open Synaptic. Mark the build-essential package for installation

---

