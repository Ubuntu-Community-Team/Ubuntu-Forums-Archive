---
title: "[SOLVED] Lib/cpp/ fails sanity check"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Wylkar on 2008-01-19
I cannot run the "./configure" command when I try I get this error:

root@william-desktop:/home/william/Desktop/aquamarine-0.2.1# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... no
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... no
checking whether g++ supports -Wno-long-long... no
checking whether g++ supports -Wno-non-virtual-dtor... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
root@william-desktop:/home/william/Desktop/aquamarine-0.2.1# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... no
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... no
checking whether g++ supports -Wno-long-long... no
checking whether g++ supports -Wno-non-virtual-dtor... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

I looked at other forum threads and I could not find anything to help

---

### Post by PeterJS on 2008-01-19
Do you have build-essential installed?

For fiesty there's a prebuilt aquamarine package, and for gutsy aquamarine has been rolled in to the decorator plugin as kde-window-decorator. Documentation here:
[http://wiki.compiz-fusion.org/Decorators/KDEWindowDecorator](http://wiki.compiz-fusion.org/Decorators/KDEWindowDecorator)

---

### Post by Wylkar on 2008-01-19
Thanks, 
 now I get:

 checking for Qt... configure: error: Qt (>= Qt 3.3 and < 4.0) (headers and libraries) not found.

I do not know which package to install for this.
(I tried to install libqt3-mt-dev but it says that :
ibqt3-mt-dev:
 Depends: libcupsys2-dev but it is not going to be installed
  Depends: libqt3-mt (=3:3.3.8really3.3.7-0ubuntu11) but 3:3.3.8really3.3.7-0ubuntu11.1 is to be installed
I have no idea what this means or even if this is the right package to be installing)

---

### Post by PeterJS on 2008-01-20
> **Wylkar said:**
> Thanks, 
 now I get:

 checking for Qt... configure: error: Qt (>= Qt 3.3 and < 4.0) (headers and libraries) not found.

I do not know which package to install for this.
(I tried to install libqt3-mt-dev but it says that :
libqt3-mt-dev:
 Depends: libcupsys2-dev but it is not going to be installed

That's odd, both libqt3-mt-dev and libcupsys2-dev are in the main repository, so if you can install one you should be able to install the other.
> 
  Depends: libqt3-mt (=3:3.3.8really3.3.7-0ubuntu11) but 3:3.3.8really3.3.7-0ubuntu11.1 is to be installed

Now this one is even weirder, you've got a version libqt3-mt from the future, do you have backports, or the kde4 ppa, or some other weird repository enabled?
> 
I have no idea what this means or even if this is the right package to be installing)

---

### Post by Wylkar on 2008-01-20
I looked in synaptic>setting>repositories and I did not have any third party software sources (I have enabled all of the ubuntu sofftware sources) and if backports are unsupported updates I have not enabled them either. I do not see anything on KDE4 ppa.

---

### Post by Wylkar on 2008-01-21
Okay I fixed my repositories list and got the qt threaded files but now I get:
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

---

### Post by Wylkar on 2008-01-21
Nevermind I got it working
thanks for the help

---

