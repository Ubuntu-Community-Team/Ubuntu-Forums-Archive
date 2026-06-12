---
title: "Installing Package Using Make"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-01-19
I am tryin to install the [Baghira]("http://www.kde-look.org/content/show.php?content=8692") theme but I am having a hard time.

As written in the page from kde-look.org:
> Installation
-----------------
tar -xjf baghira.tar.bz2
cd baghira/baghira
./configure --prefix=`kde-config --prefix` --disable-debug [--enable-final]
(!!!BEGINNERS: the direction of the accents is _important_ (top-left to bottom-right), the rectangular brackets mean [this is optional] - don't type them!!!)
make
and finally as root:
make install

after going to the directory, I entered ./configure --prefix=`kde-config --prefix` --disable-debug
```
user@Laptop:/tmp/fr-MlzNRh/baghira-0.8$ ./configure --prefix=`kde-config --prefix` --disable-debug
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as requested)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
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

```

Then, I entered "make"
```
user@Laptop:/tmp/fr-MlzNRh/baghira-0.8$ make
make: *** No targets specified and no makefile found.  Stop.
user@Laptop:/tmp/fr-MlzNRh/baghira-0.8$

```

What do I do next?

---

### Post by mcduck on 2007-01-19
You need to install all the stuff needed for compiling first: 'sudo apt-get install build-essential'

---

### Post by lsutiger on 2007-05-18
Similar problem. When I run ./configure I get the following at the end of everything:```
checking for glibmm-2.4 >= 2.4... Package glibmm-2.4 was not found in the pkg-config search path. Perhaps you should add the directory containing `glibmm-2.4.pc' to the PKG_CONFIG_PATH environment variable No package 'glibmm-2.4' found
configure: error: Library requirements (glibmm-2.4 >= 2.4) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```
I ran the apt-get suggested here
Now I am getting this error after installing glibmm:
checking for gdkmm-2.4 >= 2.4... Package gdkmm-2.4 was not found in the pkg-config search path. Perhaps you should add the directory containing `gdkmm-2.4.pc' to the PKG_CONFIG_PATH environment variable No package 'gdkmm-2.4' found
configure: error: Library requirements (gdkmm-2.4 >= 2.4) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

What do I have to install to the package manager to make this happen?

---

### Post by Seisen on 2007-05-18
Is it gtkmm-2.4 or gdkmm-2.4?

---

### Post by lsutiger on 2007-05-18
Well, I just copied and pasted what the output was...gdkmm

---

### Post by chamberlain2006 on 2007-05-18
To get the files necessary to compile the program, you'll need the gdkmm-dev package.  The -dev suffix means the developement files.

---

### Post by lsutiger on 2007-05-18
When I do a search n Synaptic for gdkmm I get nothing. Do I have to add something to the package manager?
BTW Thanx

---

### Post by carlosqueso on 2007-05-18
YOu could try to install libgtkmm-2.4-dev and see if it works....

---

### Post by aysiu on 2007-05-18
There's a *libglibmm-2.4-1c2a* in the repositories. Also a *libgtkmm-2.4-1c2a*. Not sure if that helps.

---

### Post by chamberlain2006 on 2007-05-18
I wasn't sure of the package name, but more of the importance of the *-dev* suffix.

---

