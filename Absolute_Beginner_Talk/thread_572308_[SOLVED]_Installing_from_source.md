---
title: "[SOLVED] Installing from source"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by lmlypfan on 2007-10-10
I'm trying to install Icecast from source.  I get to the make step and get to ./configure

and get this:

**checking for C compiler default output file name... configure: error: C compiler cannot create executables**

I then check the config.log and get this:

ix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
configure:2293: $? = 0
configure:2295: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:2298: $? = 1
configure:2321: checking for C compiler default output file name
configure:2324: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:2327: $? = 1
configure: failed program was:
| /* confdefs.h.  */
|
| #define PACKAGE_NAME "Icecast"
| #define PACKAGE_TARNAME "icecast"
| #define PACKAGE_VERSION "2.3.1"
| #define PACKAGE_STRING "Icecast 2.3.1"
| #define PACKAGE_BUGREPORT "icecast@xiph.org"
| #define PACKAGE "icecast"
| #define VERSION "2.3.1"
| /* end confdefs.h.  */
|
| int
| main ()
| {
|
|   ;
|   return 0;
| }
configure:2366: error: C compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXCPP_set=
ac_cv_env_CXXCPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_F77_set=
ac_cv_env_F77_value=
ac_cv_env_FFLAGS_set=
ac_cv_env_FFLAGS_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_OGG_PREFIX_set=
ac_cv_env_OGG_PREFIX_value=
ac_cv_env_SPEEX_set=
ac_cv_env_SPEEX_value=
ac_cv_env_THEORA_set=
ac_cv_env_THEORA_value=
ac_cv_env_VORBIS_PREFIX_set=
ac_cv_env_VORBIS_PREFIX_value=
ac_cv_env_XSLTCONFIG_set=
ac_cv_env_XSLTCONFIG_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_AWK=gawk
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_make_make_set=yes

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /home/bo/icecast-2.3.1/missing --run aclocal-1.6'
AMDEPBACKSLASH=''
AMDEP_FALSE=''
AMDEP_TRUE=''
AMTAR='${SHELL} /home/bo/icecast-2.3.1/missing --run tar'
AR=''
AUTOCONF='${SHELL} /home/bo/icecast-2.3.1/missing --run autoconf'
AUTOHEADER='${SHELL} /home/bo/icecast-2.3.1/missing --run autoheader'
AUTOMAKE='${SHELL} /home/bo/icecast-2.3.1/missing --run automake-1.6'
AWK='gawk'
CC='gcc'
CCDEPMODE=''
CFLAGS=''
CPP=''
CPPFLAGS=''
CURL_CONFIG=''
CXX=''
CXXCPP=''
CXXDEPMODE=''
CXXFLAGS=''
DEBUG=''
DEFS=''
DEPDIR=''
ECHO='echo'
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
F77=''
FFLAGS=''
FGREP=''
ICECAST_OPTIONAL=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='${SHELL} $(install_sh) -c -s'
LDFLAGS=''
LIBOBJS=''
LIBS=''
LIBTOOL=''
LIBTOOL_DEPS=''
LN_S=''
LTLIBOBJS=''
MAINT='#'
MAINTAINER_MODE_FALSE=''
MAINTAINER_MODE_TRUE='#'
MAKEINFO='${SHELL} /home/bo/icecast-2.3.1/missing --run makeinfo'
OBJEXT=''
OGG_CFLAGS=''
OGG_LDFLAGS=''
OGG_LIBS=''
OGG_PREFIX=''
PACKAGE='icecast'
PACKAGE_BUGREPORT='icecast@xiph.org'
PACKAGE_NAME='Icecast'
PACKAGE_STRING='Icecast 2.3.1'
PACKAGE_TARNAME='icecast'
PACKAGE_VERSION='2.3.1'
PATH_SEPARATOR=':'
PROFILE=''
PTHREAD_CC=''
PTHREAD_CFLAGS=''
PTHREAD_CPPFLAGS=''
PTHREAD_LIBS=''
RANLIB=''
SET_MAKE=''
SHELL='/bin/bash'
SPEEX=''
SPEEX_CFLAGS=''
SPEEX_LDFLAGS=''
SPEEX_LIBS=''
STRIP=''
THEORA=''
THEORA_CFLAGS=''
THEORA_LDFLAGS=''
THEORA_LIBS=''
VERSION='2.3.1'
VORBISENC_LIBS=''
VORBISFILE_LIBS=''
VORBIS_CFLAGS=''
VORBIS_LDFLAGS=''
VORBIS_LIBS=''
VORBIS_PREFIX=''
XIPH_CFLAGS=''
XIPH_CPPFLAGS=''
XIPH_LDFLAGS=''
XIPH_LIBS=''
XSLTCONFIG=''
ac_ct_AR=''
ac_ct_CC='gcc'
ac_ct_CXX=''
ac_ct_F77=''
ac_ct_RANLIB=''
ac_ct_STRIP=''
acx_pthread_config=''
am__include=''
am__quote=''
bindir='${exec_prefix}/bin'
build=''
build_alias=''
build_cpu=''
build_os=''
build_vendor=''
datadir='${prefix}/share'
exec_prefix='NONE'
host=''
host_alias=''
host_cpu=''
host_os=''
host_vendor=''
includedir='${prefix}/include'
infodir='${prefix}/info'
install_sh='/home/bo/icecast-2.3.1/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localstatedir='${prefix}/var'
mandir='${prefix}/man'
oldincludedir='/usr/include'
prefix='NONE'
program_transform_name='s,x,x,'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE "icecast"
#define PACKAGE_BUGREPORT "icecast@xiph.org"
#define PACKAGE_NAME "Icecast"
#define PACKAGE_STRING "Icecast 2.3.1"
#define PACKAGE_TARNAME "icecast"
#define PACKAGE_VERSION "2.3.1"
#define VERSION "2.3.1"

Please help

---

### Post by lmlypfan on 2007-10-10
Any Help?

Maybe this should be moved to the Installation & Upgrades  section.

---

### Post by milosz.galazka on 2007-10-10
apt-get install build-essential
or maybe 
apt-get install libc6-dev
?

---

### Post by svalding on 2007-10-10
can you install anything else from source? Sounds to me like your gcc compiler is either missing, or out of date.  Have you installed the buildessential package from Synaptic? 

If not type 

```
 apt-get install build-essential
```

in the command line and you should be good to go.

---

### Post by lmlypfan on 2007-10-10
This is my first time trying to install anything from source.
I'll try what you both suggested and see what happens.

---

### Post by lmlypfan on 2007-10-10
I had to run "sudo apt-get update"

Then installed build-essential

Then ran ./Configure

Now i get a new error:

 **XSLT configuration could not be found**

---

### Post by lmlypfan on 2007-10-10
Is installing from source always this difficult?

---

### Post by lmlypfan on 2007-10-10
well,

I found it in the repos under icecast2, but would still like to learn how to install from source better. 

I'll search the forums for additional info.

Thanks for all the suggestions.

---

### Post by milosz.galazka on 2007-10-10
for **XSLT configuration could not be found** you probably need
apt-get install libxslt-dev

---

