---
title: "Installing on Linux Mint"
date: 2012-11-13
forum: Any Other OS
---

### Post by Hasan55 on 2012-11-13
hey ,there i have just installed LINUX MINT 12 LISA dvd of my desktop .  but can not install any tar.ball ....but i can nicely install deb. file . is there any thing necessary  to update to  of my system. please give me a proper direction  i am not experienced in Linux

---

### Post by monkeybrain2012 on 2012-11-13
> **Hasan55 said:**
> hey ,there i have just installed LINUX MINT 12 LISA dvd of my desktop .  but can not install any tar.ball ....but i can nicely install deb. file . is there any thing necessary  to update to  of my system. please give me a proper direction  i am not experienced in Linux

 What tar ball? May be your tar ball needs to be compiled first, in that case you need to install build-essentials and automake.

---

### Post by Hasan55 on 2012-11-13
thanks....... but can you give me proper direction of any kinds of  tar.ball  installsion

---

### Post by lisati on 2012-11-13
> **Hasan55 said:**
> thanks....... but can you give me proper direction of any kinds of  tar.ball  installsion

A "tar.ball" is roughly equivalent to a "zip" or "rar" file in Windows. You'll usually (but not always) need to unpack it first. There is often a "readme" file with instructions for installation included in the tarball.

---

### Post by monkeybrain2012 on 2012-11-13
> **Hasan55 said:**
> thanks....... but can you give me proper direction of any kinds of  tar.ball  installsion


There should be a readme or a file called install in the tar ball which gives you the directions which may differ from program to program.

The common thing (but not always, check the readme) is 
1) unzip the tar ball (just right click it an extract or you can use a command line depending on what kind of tar ball it is (tar.gz or tar.bz etc)

2) cd into the directory where the tar ball is unzipped to,

3) type ./configure and note the output, it will tell you if you have missing dependencies, there are other options you may enable or disable depending on your program.

4) if step 3 works without error, type make

5) sudo make install 
(instead of this you can install the package checkinstall and run sudo checkinstall, this way it will create and install a .deb package, which is easy to remove from package managers such as synaptic, otherwise there may be pieces scattered all over that you need to remove them manually in case you don't want the program any more)

Like I said, this is the way to compile and install many programs from source but not always, read the instructions first,

---

### Post by Hasan55 on 2012-11-13
hey , i have downloaded rhythmbox 0.13.3 . i have extract it and open terminal type: ./configure it works but when i typed make then it does not work ....the terminal shows like...

hasan@ruhul-desktop ~/Desktop/rhythmbox-0.13.3 $ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether NLS is requested... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for intltool >= 0.35.0... 0.41.1 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.12.4
checking for XML::Parser... ok
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating ./config.lt
config.lt: creating libtool
checking whether byte ordering is bigendian... no
checking size of long... 4
checking for GNU extension fwrite_unlocked... yes
checking for mkdtemp... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for RB_CLIENT... yes
checking for RHYTHMBOX... no
configure: error: Package requirements (          gtk+-2.0 >= 2.18.0      glib-2.0 >= 2.18.0                  gio-2.0 >= 2.18.0          gio-unix-2.0 >= 2.18.0                  gnome-media-profiles >= 2.8       libsoup-2.4 >= 2.26.0                  libsoup-gnome-2.4 >= 2.26.0) were not met:

No package 'gnome-media-profiles' found
No package 'libsoup-2.4' found
No package 'libsoup-gnome-2.4' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables RHYTHMBOX_CFLAGS
and RHYTHMBOX_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
hasan@ruhul-desktop ~/Desktop/rhythmbox-0.13.3 $ make
make: *** No targets specified and no makefile found.  Stop.
hasan@ruhul-desktop ~/Desktop/rhythmbox-0.13.3 $ 





what should i do now????????????

---

### Post by blade4 on 2012-11-13
The prompt says you need the following packages : 

> No package 'gnome-media-profiles' found
No package 'libsoup-2.4' found
No package 'libsoup-gnome-2.4' found

Install these first . 

```
sudo apt-get install gnome-media-profiles libsoup-2.4 libsoup-gnome-2.4 
```

I'm not sure if these are available in the repo but try it out anyway . If this doesn't work , find the tarballs to these files , configure and make install them .
Then you can go ahead with your rhythmbox installation .

---

### Post by monkeybrain2012 on 2012-11-13
./configure does not work because you have unmet dependencies

```
configure: error: Package requirements ( gtk+-2.0 >= 2.18.0 glib-2.0 >= 2.18.0 gio-2.0 >= 2.18.0 gio-unix-2.0 >= 2.18.0 gnome-media-profiles >= 2.8 libsoup-2.4 >= 2.26.0 libsoup-gnome-2.4 >= 2.26.0) were not met:
```
This means that these dependencies are either not already installed or installed but are of the wrong version.

But why compile it yourself? I think rhythmbox comes with Ubuntu???

If you want the latest stable release (2.98) you can just add this ppa to your sources list and install it that way.

[https://launchpad.net/~webupd8team/+archive/rhythmbox?field.series_filter=](https://launchpad.net/~webupd8team/+archive/rhythmbox?field.series_filter=)

---

### Post by NikTh on 2012-11-13
Hi , 

are you a newbie in Linux ? If yes , and you want to compile , build and install a package from source , then is not going to happen easily. The procedure is not so easy. (for a newbie). 
I suggest you to read these first 
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

If you want a specific package (eg: Rhythmbox) then first search if this package has an available .deb file , so you can install it more easy (or maybe through a PPA). 

Also Linux-Mint Lisa is Ubuntu 11.10 based (I think) and will be EOL in a few months. April 2013. 
Maybe is time to consider an upgrade to Linux-mint 13 (Ubuntu 12.04 LTS based , supported until April 2017). 

Very old package version  0.13.3
Rythmbox now is in 2.98 version => [https://launchpad.net/ubuntu/+source/rhythmbox](https://launchpad.net/ubuntu/+source/rhythmbox)

---

### Post by techvish81 on 2012-11-13
if you just want to install some required software,  you don't need to compile anything or download any tar balls :-),   just go to software centre and find your desired applications and install them,  actually it is much easier than windows.:-)

---

### Post by newb85 on 2012-11-14
A couple things stand out to me here:
[list]
[*]I don't think *.tar.ball is a standard file extension.  But then, maybe ball is a compression format I've never heard of and they forgot to include in the tar manpage.  :)
[*]The OP is trying to install Rhythmbox 0.13.3 from a .tar file.  The version in the repos for 12.04 is 2.96.  Did I miss something here?
[/list]

---

### Post by lisati on 2012-11-14
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by MadmanRB on 2012-11-16
Why are you trying to install a tarball for?
Most software can be found in the package repositories.
What application are you trying to install?

---

