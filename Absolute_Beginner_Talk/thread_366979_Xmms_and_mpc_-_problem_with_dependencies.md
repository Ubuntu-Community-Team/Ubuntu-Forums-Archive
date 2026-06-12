---
title: "Xmms and mpc - problem with dependencies"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by fidolip on 2007-02-21
Hi!

Currently I am looking for music player that will fit me, and after trying exaile I decided to give xmms a try. I installed it with a lot of different plugins, but when I tried to install probably the most important one for me, musepack, I got this error:

xmms-musepack:
  Depends: libc6 (>=2.3.6-6) but 2.3.6-0ubuntu20.4 is to be installed
  Depends: libgcc1 (>=1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
  Depends: libmpcdec3 (>=1.2.3) but 1.2.2-1 is to be installed
  Depends: libstdc++6 (>=4.1.1-12) but 4.0.3-1ubuntu5 is to be installed

I tried to install them all, but encountered more troubles. I cannot find this newest version of libc6, and it seems that some of the other ones are dependent on it. What should I do? I am using dapper drake.

---

### Post by terdon on 2007-02-21
Well, there are various options:

i) install edgy
ii) manually install the libc packages
iii) install an older version of xmms with different dependencies

In the two last options you will need to use the command line, if you need help, post something and I'll try and walk you through it.

---

### Post by fidolip on 2007-02-22
I try to use command line to everything I can.;-) As for option 2: can't do:

fidolip@laptop:~$ sudo aptitude install libc6
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
The following packages have been kept back:
  cdrdao dvd+rw-tools lame liblame0 libmodplug0c2 libmpcdec3
0 packages upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
fidolip@laptop:~$


and when I do aptitude search libc6:

fidolip@laptop:~$ aptitude search libc6
v   libapt-inst-libc6.3-6-1.1                          -
v   libapt-pkg-libc6.3-6-3.11                          -
i   libapt-rpm-pkg-libc6.3-6-0                         - APT for RPM library
i   libc6                                              - GNU C Library: Shared libraries and Timezone data
p   libc6-amd64                                        - GNU C Library: 64bit Shared libraries for AMD64
p   libc6-dbg                                          - GNU C Library: Libraries with debugging symbols
p   libc6-dev                                          - GNU C Library: Development Libraries and Header Files
p   libc6-dev-amd64                                    - GNU C Library: 64bit Development Libraries for AMD64
i   libc6-i686                                         - GNU C Library: Shared libraries [i686 optimized]
p   libc6-pic                                          - GNU C Library: PIC archive library
p   libc6-prof                                         - GNU C Library: Profiling Libraries

which looks like I have the latest ver. of it installed.:/ I wonder - is it possible that the latest version works only on Edgy?

If I don't find the solution to my problem, I will try to install edgy..
Cheers!

---

### Post by terdon on 2007-02-22
Well it looks like libc is indeed installed. Another thing you can do is try and install xmms manually (by which i mean complie from source) and see first if it works and then if you get any more usefull error messages:

So, make a directory where you want to save these and download the files:
```

mkdir setups
cd setups
wget http://www.xmms.org/files/1.2.x/xmms-1.2.10.tar.gz
wget http://internap.dl.sourceforge.net/sourceforge/mpegplus/xmms-musepack-1.00.tar.gz

```
XMMS:
```

tar xvvzf xmms-1.2.10.tar.gz
cd xmms-1.2.10
./configure
sudo make
sudo make install

```

Musepack:
```

tar -xvvzf xmms-musepack-1.00.tar.gz
cd xmms-musepack-1.00
sudo cp xmms-musepack-*.dll /usr/X11/lib/xmms/Input/

```


Now, that should either work directly (i wish) or, it should give you more interesting error messages and let us figure out where it is searching for the installed libraries.

NOTE: The /usr/X11/lib/xmms/Input/ directory might be different in your distribution (cab0t check ubuntu now as I am workin on fedora). try running ```
locate xmms | grep Input | grep lib
```
That should give you the right directory (eg /usr/lib/xmms/Input).

Good luck!

---

### Post by fidolip on 2007-02-22
Everything went well until:

```

fidolip@laptop:~/setups/xmms-1.2.10$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for prefix by checking for xmms... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

```

Want me to paste config.log as well? (probably would find it, but just in case - where is it?:>)

---

### Post by terdon on 2007-02-22
config.log is in the directory where you ran ./configure . Easier would be to do
```
 which gcc
```
If nothing is returned, you don't have a C compiler installed. Just install it (use synaptic and search for gcc) and then run configure again.

---

### Post by fidolip on 2007-02-22
More troubles:

```

fidolip@laptop:~/setups/xmms-1.2.10$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for prefix by checking for xmms... no
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

btw. wasn't linux written in C? Then why isn't there a C compiler right away?

---

### Post by terdon on 2007-02-22
Yes linux is written in C, but since it is already compiled, a compiler is not necessary for the operating system to function. Most linux distributions install the compiler by default. Since ubuntu aims to be a system where users do not need to compile anything, it does not install gcc by default. 

As for your problem: 

This may simply be a permissions issue. try doing ```
sudo ./configure
```

And post your config.log while you're at it :)

---

### Post by fidolip on 2007-02-22
Nope. Sudo didn't work:

```

fidolip@laptop:~/setups/xmms-1.2.10$ sudo ./configure
Password:
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for prefix by checking for xmms... no
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

My config.log:

```

This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by configure, which was
generated by GNU Autoconf 2.57.  Invocation command line was

  $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = laptop
uname -m = i686
uname -r = 2.6.15-28-386
uname -s = Linux
uname -v = #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = i686
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
hostinfo               = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/X11R6/bin


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1518: checking build system type
configure:1536: result: i686-pc-linux-gnulibc1
configure:1544: checking host system type
configure:1558: result: i686-pc-linux-gnulibc1
configure:1584: checking for a BSD-compatible install
configure:1638: result: /usr/bin/install -c
configure:1649: checking whether build environment is sane
configure:1692: result: yes
configure:1725: checking for gawk
configure:1754: result: no
configure:1725: checking for mawk
configure:1741: found /usr/bin/mawk
configure:1751: result: mawk
configure:1761: checking whether make sets $(MAKE)
configure:1781: result: yes
configure:2017: checking for xmms
configure:2050: result: no
configure:2134: checking for gcc
configure:2150: found /usr/bin/gcc
configure:2160: result: gcc
configure:2404: checking for C compiler version
configure:2407: gcc --version </dev/null >&5
gcc (GCC) 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2410: $? = 0
configure:2412: gcc -v </dev/null >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.0 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-awt=gtk-default --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --with-tune=pentium4 --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
configure:2415: $? = 0
configure:2417: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:2420: $? = 1
configure:2444: checking for C compiler default output
configure:2447: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:2450: $? = 1
configure: failed program was:
| #line 2423 "configure"
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "xmms"
| #define VERSION "1.2.10"
| #define DEV_DSP "/dev/dsp"
| #define DEV_MIXER "/dev/mixer"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:2489: error: C compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=i686-pc-linux-gnulibc1
ac_cv_build_alias=i686-pc-linux-gnulibc1
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_host=i686-pc-linux-gnulibc1
ac_cv_host_alias=i686-pc-linux-gnulibc1
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_AWK=mawk
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_make_make_set=yes

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /home/fidolip/setups/xmms-1.2.10/missing --run aclocal-1.7'
ALLOCA=''
ALSA_CFLAGS=''
ALSA_LIBS=''
AMDEPBACKSLASH=''
AMDEP_FALSE=''
AMDEP_TRUE=''
AMTAR='${SHELL} /home/fidolip/setups/xmms-1.2.10/missing --run tar'
ARCH_DEFINES=''
ARCH_X86_FALSE=''
ARCH_X86_TRUE=''
AUTOCONF='${SHELL} /home/fidolip/setups/xmms-1.2.10/missing --run autoconf'
AUTOHEADER='${SHELL} /home/fidolip/setups/xmms-1.2.10/missing --run autoheader'
AUTOMAKE='${SHELL} /home/fidolip/setups/xmms-1.2.10/missing --run automake-1.7'
AWK='mawk'
BUILD_INCLUDED_LIBINTL=''
CATOBJEXT=''
CC='gcc'
CCAS=''
CCASFLAGS=''
CCDEPMODE=''
CFLAGS=''
CPP=''
CPPFLAGS=''
CYGPATH_W='echo'
DATADIRNAME=''
DEFS=''
DEPDIR=''
ECHO='echo'
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EFFECT_PLUGINS=''
EFFECT_PLUGIN_DIR=''
EGREP=''
ESD_CFLAGS=''
ESD_CONFIG=''
ESD_LIBS=''
EXEEXT=''
GENCAT=''
GENERAL_PLUGINS=''
GENERAL_PLUGIN_DIR=''
GLIBC21=''
GLIB_CFLAGS=''
GLIB_CONFIG=''
GLIB_LIBS=''
GMSGFMT=''
GTK_CFLAGS=''
GTK_CONFIG=''
GTK_LIBS=''
HAVE_ALSA_FALSE=''
HAVE_ALSA_TRUE=''
HAVE_CDROM_FALSE=''
HAVE_CDROM_TRUE=''
HAVE_ESD_FALSE=''
HAVE_ESD_TRUE=''
HAVE_LINUX_JOYSTICK_FALSE=''
HAVE_LINUX_JOYSTICK_TRUE=''
HAVE_MIKMOD_FALSE=''
HAVE_MIKMOD_TRUE=''
HAVE_OGGVORBIS_FALSE=''
HAVE_OGGVORBIS_TRUE=''
HAVE_OPENGL_FALSE=''
HAVE_OPENGL_TRUE=''
HAVE_OSS_FALSE=''
HAVE_OSS_TRUE=''
HAVE_SOLARIS_FALSE=''
HAVE_SOLARIS_TRUE=''
HAVE_SUN_FALSE=''
HAVE_SUN_TRUE=''
INPUT_PLUGINS=''
INPUT_PLUGIN_DIR=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='${SHELL} $(install_sh) -c -s'
INSTOBJEXT=''
INTLBISON=''
INTLLIBS=''
INTLOBJS=''
INTL_LIBTOOL_SUFFIX_PREFIX=''
LDFLAGS=''
LIBICONV=''
LIBINTL=''
LIBMIKMOD_CFLAGS=''
LIBMIKMOD_CONFIG=''
LIBMIKMOD_LDADD=''
LIBMIKMOD_LIBS=''
LIBOBJS=''
LIBS=''
LIBTOOL=''
LN_S=''
LTLIBICONV=''
LTLIBINTL=''
LTLIBOBJS=''
MAKEINFO='${SHELL} /home/fidolip/setups/xmms-1.2.10/missing --run makeinfo'
MKINSTALLDIRS=''
MSGFMT=''
MSGMERGE=''
OBJEXT=''
OGG_CFLAGS=''
OGG_LIBS=''
OPENGL_LIBS=''
OUTPUT_PLUGINS=''
OUTPUT_PLUGIN_DIR=''
PACKAGE='xmms'
PACKAGE_BUGREPORT=''
PACKAGE_NAME=''
PACKAGE_STRING=''
PACKAGE_TARNAME=''
PACKAGE_VERSION=''
PATH_SEPARATOR=':'
PLUGIN_LDFLAGS=''
POSIX_LIBS=''
POSUB=''
PTHREAD_LIBS=''
RANLIB=''
SET_MAKE=''
SHELL='/bin/sh'
SM_LIBS=''
STRIP=''
USE_INCLUDED_LIBINTL=''
USE_IPV6=''
USE_IPV6_FALSE=''
USE_IPV6_TRUE=''
USE_NLS=''
USE_SIMD_FALSE=''
USE_SIMD_TRUE=''
USE_X86ASM_FALSE=''
USE_X86ASM_TRUE=''
VERSION='1.2.10'
VISUALIZATION_PLUGINS=''
VISUALIZATION_PLUGIN_DIR=''
VM_LIBS=''
VORBISENC_LIBS=''
VORBISFILE_LIBS=''
VORBIS_CFLAGS=''
VORBIS_LIBS=''
XGETTEXT=''
XMMS_DEFINES=''
XMMS_PATH=''
Z_LIBS=''
ac_ct_CC='gcc'
ac_ct_RANLIB=''
ac_ct_STRIP=''
ac_prefix_program=''
am__fastdepCC_FALSE=''
am__fastdepCC_TRUE=''
am__include=''
am__leading_dot='.'
am__quote=''
bindir='${exec_prefix}/bin'
build='i686-pc-linux-gnulibc1'
build_alias=''
build_cpu='i686'
build_os='linux-gnulibc1'
build_vendor='pc'
datadir='${prefix}/share'
exec_prefix='NONE'
host='i686-pc-linux-gnulibc1'
host_alias=''
host_cpu='i686'
host_os='linux-gnulibc1'
host_vendor='pc'
includedir='${prefix}/include'
infodir='${prefix}/info'
install_sh='/home/fidolip/setups/xmms-1.2.10/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir=''
localstatedir='${prefix}/var'
mandir='${prefix}/man'
oldincludedir='/usr/include'
plugindir=''
pluginsubs=''
prefix='NONE'
program_transform_name='s,x,x,'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
subdirs=''
sysconfdir='${prefix}/etc'
target_alias=''
xmmsdir=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define DEV_DSP "/dev/dsp"
#define DEV_MIXER "/dev/mixer"
#define PACKAGE "xmms"
#define PACKAGE_BUGREPORT ""
#define PACKAGE_NAME ""
#define PACKAGE_STRING ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""
#define VERSION "1.2.10"

configure: exit 77

```

---

### Post by terdon on 2007-02-22
OK, we come back to the idea of ubuntu as a "desktop" linux and missing some basic compiling tools. I am not sure if this is the problem, but one of the things configure complains about is that it can find ld. ld is essentially a linker:
> ld  combines a number of object and archive files, relocates their data
       and ties up symbol references. Usually the last  step  in  compiling  a
       program is to run ld.

If the command```
which ld
```

returns nothing, try installing ld from synaptic (also install make, automake and autoconf while you're at it) and try again.

Mind you, if you can install xmms without the plugins from synaptic you could just do that and then install the plugin alone manually as described in one of my previous posts.

---

### Post by fidolip on 2007-02-22
Will have to try tommorow, as right now I am not at home. First I will install this linker + all the other stuff that was missing and try to install xmms by hand. If that doesn't work I will install xmms from synaptic (done that before, even with plugins. Only musepack gave me the troubles.:/) and try to install musepack plugin by hand. Uff.. Hope one of these will work.;-) Will post the results either tonight or tmrw morning.:-)

Could you tell me a bit more about these 'missing compiling tools'? I've used some python on ubuntu before, and did not have too much trouble w/ it. Is it only C's problem?

---

### Post by terdon on 2007-02-22
> **fidolip said:**
> 
Could you tell me a bit more about these 'missing compiling tools'? I've used some python on ubuntu before, and did not have too much trouble w/ it. Is it only C's problem?

No, it is not only C. It is for any compiled language. Languages such as python or perl (often called scripting languages) are "interpreted". This means there is a program running in the background, eg python, which will take your script and translate it (essentially compile it on the fly) into something the computer will understand.

Programs written in languages such as C or Fortran on the other hand are compiled first and then run. That is, you write the program and then run the compiler to translate this into binary and then execute the binary. 

Hope that clears things up.

PS. If you had no problems installing xmms alone, I recommend you do so and then just copy the plugins. That should work. Nevertheless, it is a good idea to install the tools mentioned as you will probably need them at some point

---

### Post by paculz on 2007-02-22
> **fidolip said:**
> Hi!

Currently I am looking for music player that will fit me, and after trying exaile I decided to give xmms a try. I installed it with a lot of different plugins, but when I tried to install probably the most important one for me, musepack, I got this error:

xmms-musepack:
  Depends: libc6 (>=2.3.6-6) but 2.3.6-0ubuntu20.4 is to be installed
  Depends: libgcc1 (>=1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
  Depends: libmpcdec3 (>=1.2.3) but 1.2.2-1 is to be installed
  Depends: libstdc++6 (>=4.1.1-12) but 4.0.3-1ubuntu5 is to be installed

I tried to install them all, but encountered more troubles. I cannot find this newest version of libc6, and it seems that some of the other ones are dependent on it. What should I do? I am using dapper drake.

Amarok is a good player. You can install this by using your synaptec package manager and type in amarok as it would display the application to install. Further you alsoneed to install 'arts' package. Then you can experience the great sound from the player installed. Its better or like the winamp.

---

### Post by fidolip on 2007-02-22
Hm. I'm using gnome and I am little afraid that it's gonna take quite a while for amarok to load. Will it?

Is it really similar to winamp? I'm using exaile (which is supposed to be gnome ver. of amarok), and it's nothing like winamp.;-) AFAIK xmms is linux's version of winamp?

---

### Post by fidolip on 2007-02-24
Hi! I installed xmms via synaptic and then tried to follow your instructions about installing the plugin. Have some troubles:
```

fidolip@laptop:~/setups/xmms-musepack-1.00$ dir
\            huffsv7.c                      README_mpc-plugin_korean.txt
akg_k141     huffsv7.h                      README_mpc-plugin_spanish.txt
akg_k141.h   in_mpc.c                       requant.c
akg_k401     in_mpc.h                       requant.h
akg_k401.h   Makefile                       sf_amati
akg_k501     Makefile.Linux.IA32            sf_amati.h
akg_k501.h   Makefile.MacOSX.PPC            sh_hd580
bitstream.c  minimax.h                      sh_hd580.h
bitstream.h  mpc_dec.c                      sh_hd600
ChangeLog    mpc_dec.h                      sh_hd600.h
config.h     mppdec.h                       synth_filter.c
CVS          mppenc.h                       synth_filter.h
equal.c      mpp.h                          tags.c
equal.h      mpplus_blue.xpm                Wanted
equalizer.c  profile.h                      xmms.dsp
equalizer.h  README_mpc-plugin_english.txt  xmms-musepack.spec
huffsv46.c   README_mpc-plugin_finnish.txt  xmms.vcproj
huffsv46.h   README_mpc-plugin_german.txt
fidolip@laptop:~/setups/xmms-musepack-1.00$ sudo cp xmms-musepack-*.dll /usr/lib/xmms/Input/
cp: cannot stat `xmms-musepack-*.dll': No such file or directory

```

Any ideas?

---

### Post by terdon on 2007-02-24
Well, I ma not quite sure what you are trying to do with this copy but if fails because you are telling it to copy all files which start with xmms-musepack and end in .dll . There are no such files apparent in the directory listing you have posted. Why are you looking for dll files anyway?

---

### Post by terdon on 2007-02-24
OK, yes, I see why you are copying dlls, I reread my post :oops:

Umm... I don't know actually, I copied the dll thing from the plugin's readme and assumed they would know what they are talking about...

Try doing
```
 make

```
In the directory where you have extracted the plugin. (This didn't work for me, I got a load of uninformative compiler messages so I wouldn't get my hopes up...)

I am going to try a few things and let you know

---

### Post by terdon on 2007-02-25
Right, try this:

1) Install xmms-dev, libtag1-dev, libmpcdec and g++ with synaptic
2) libmpcdec
```

wget http://files.musepack.net/source/libmpcdec-1.2.5.tar.bz2
tar xvvjf libmpcdec-1.2.5.tar.bz2
cd libmpcdec-1.2.5
./configure
make
sudo make install

```
3) musepack
```

wget http://files.musepack.net/linux/plugins/xmms-musepack-1.2.1.tar.bz2
tar xvvjf xmms-musepack-1.2.1.tar.bz2 
cd xmms-musepack-1.2.1
bash ./configure
make
sudo make install

```

You may need to install additional packages, these are the ones that were
necessary for my system. Let me know how it goes.

---

### Post by fidolip on 2007-02-25
Grr.. Again, problems w/ libc6.
When isntalling libmpcdec:
```

libmpcdec-dev:
  Depends: libmpcdec3 (>=1.2.4-0rarewares1) but 1.2.2-1 is to be installed

```

And when I try to install newest libmpcdec3:
```

libmpcdec3:
  Depends: libc6 (>=2.3.6-6) but 2.3.6-0ubuntu20.4 is to be installed

```

Unfortunately synaptic doesn't find ver. 2.3.6-6.:/ I found it in the Internet ([http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fglibc%2Flibc6_2.3.6.ds1-11_i386.deb&md5sum=b1972b96aabfd69c7b95dfd9f46e0e0c&arch=i386&type=main)](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fglibc%2Flibc6_2.3.6.ds1-11_i386.deb&md5sum=b1972b96aabfd69c7b95dfd9f46e0e0c&arch=i386&type=main)), yet it's not the 'stable' version, but called 'testing'. It's downloading right now, we'll see if it helps at all.;-)

---

### Post by fidolip on 2007-02-25
While libc6 is downloading (I have really crappy connection in my dorms.:/) I did what you told me to do in your last post. One question and one problem:

Question: why 'bash ./configure', and not only './configure' when installing musepack? It worked, but would like to understand what I am doing once in a while.;-)

Problem:
```

fidolip@laptop:~/xmms-musepack-1.2.1$ make
cd . && /bin/sh /home/fidolip/xmms-musepack-1.2.1/config/missing --run aclocal-1.9
/usr/share/aclocal/glib.m4:8: warning: underquoted definition of AM_PATH_GLIB
  run info '(automake)Extending aclocal'
  or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
aclocal:configure.ac:10: warning: macro `AM_DISABLE_STATIC' not found in library cd . && /bin/sh /home/fidolip/xmms-musepack-1.2.1/config/missing --run automake-1.9 --foreign
src/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
src/Makefile.am:3:
src/Makefile.am:3: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'src/Makefile.am:3: to `configure.ac' and run `aclocal' and `autoconf' again.
make: *** [Makefile.in] Error 1

```

---

### Post by terdon on 2007-02-25
OK, see if that helps, if not you can always use a previous version of libmpcdec.

---

### Post by fidolip on 2007-02-25
Ehh.. Downloaded the latest libc6, it required tzdata:
```

(Reading database ... 97260 files and directories currently installed.)
Unpacking tzdata ( from ../Desktop/tzdata_2007b-1_all.deb) ...
dpkg: error processing /home/fidolip/Desktop/tzdata_2007b-1_all.deb (--install):
 trying to overwrite '/usr/share/zoneinfo/Canada/Atlantic', which is also in package locales
dpkg-deb: subprocess paste killed by signal (Broken pipe)

```

So now I can't make the musepack for some reason, and can't install libc6, because of unsatisfied dependency of tzdata, which I cannot install.:-( Any ideas?

---

### Post by terdon on 2007-03-07
Hey, 
     sorry it took me so long but I have been really busy lately. Plus, I don't have any more ideas... :( The only thing that occurs to me is to upgrade your distro. Either do a complete upgrade to edgy or, just
```

sudo aptitude update
sudo aptitude dist-upgrade

```

See if that helps any... 

Just a thought, have you refreshed your sources list recently? If not, do so (just hit refresh on synaptic) you might then have all the correct versions of the relevant packages

---

