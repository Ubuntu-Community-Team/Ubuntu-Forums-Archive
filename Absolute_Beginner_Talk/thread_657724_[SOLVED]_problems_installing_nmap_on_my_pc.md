---
title: "[SOLVED] problems installing nmap on my pc"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by Gipsy25 on 2008-01-03
Im trying to instal NMAP on my pc when i do ./configure i receive this message

the program i want to install is called nmap-4.52.tar.bz2
I have ubuntu 7.10
***********************************************
-ubu:~/Desktop/nmap-4.52$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
gipsy@gipsy-ubu:~/Desktop/nmap-4.52$ C [B]compiler cannot create executables
bash: C: command not found[/B]

Any ideas of what can be happening .. when i check the config log this is what i get:

********************************************************
 $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = xxxx
uname -m = i686
uname -r = 2.6.22-14-generic
uname -s = Linux
uname -v = #1 SMP Tue Dec 18 08:02:57 UTC 2007

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
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
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1398: checking build system type
configure:1416: result: i686-pc-linux-gnulibc1
configure:1424: checking host system type
configure:1438: result: i686-pc-linux-gnulibc1
configure:1492: checking for gcc
configure:1508: found /usr/bin/gcc
configure:1518: result: gcc
configure:1762: checking for C compiler version
configure:1765: gcc --version </dev/null >&5
gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:1768: $? = 0
configure:1770: gcc -v </dev/null >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
configure:1773: $? = 0
configure:1775: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:1778: $? = 1
**configure:1801: checking for C compiler default output file name**
configure:1804: gcc    conftest.c  >&5
/**usr/bin/ld: crt1.o: No such file: No such file or directory**
collect2: ld returned 1 exit status
configure:1807: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:1846: error: C compiler cannot create executables
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
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
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
ac_cv_prog_ac_ct_CC=gcc

## ----------------- ##
## Output variables. ##
## ----------------- ##

BUILDZENMAP=''
CC='gcc'
CFLAGS=''
COMPAT_OBJS=''
COMPAT_SRCS=''
CPP=''
CPPFLAGS=''
CXX=''
CXXFLAGS=''
CXXPROG=''
DEFS=''
DNET_BUILD=''
DNET_CLEAN=''
DNET_DEPENDS=''
DNET_DIST_CLEAN=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
INSTALLNSE=''
INSTALLZENMAP=''
LDFLAGS=''
LIBDNETDIR=''
LIBDNET_LIBS=''
LIBLUADIR=''
LIBLUA_LIBS=''
LIBNBASE_LIBS=''
LIBNSOCK_LIBS=''
LIBOBJS=''
LIBPCAP_LIBS=''
LIBPCREDIR=''
LIBPCRE_LIBS=''
LIBS=''
LTLIBOBJS=''
LUAFLAGS=''
LUA_BUILD=''
LUA_CLEAN=''
LUA_DEPENDS=''
LUA_DIST_CLEAN=''
NBASEDIR=''
NBASE_BUILD=''
NSELIB_CLEAN=''
NSELIB_DIST_CLEAN=''
NSOCKDIR=''
NSOCK_BUILD=''
OBJEXT=''
OPENSSL_LIBS=''
PACKAGE_BUGREPORT=''
PACKAGE_NAME=''
PACKAGE_STRING=''
PACKAGE_TARNAME=''
PACKAGE_VERSION=''
PATH_SEPARATOR=':'
PCAP_BUILD=''
PCAP_CLEAN=''
PCAP_DEPENDS=''
PCAP_DIST_CLEAN=''
PCRE_BUILD=''
PCRE_CLEAN=''
PCRE_DEPENDS=''
PCRE_DIST_CLEAN=''
PYTHON=''
PYTHON_EXEC_PREFIX=''
PYTHON_PLATFORM=''
PYTHON_PREFIX=''
PYTHON_VERSION=''
SHELL='/bin/bash'
STRIP=''
ZENMAP_CLEAN=''
ZENMAP_DIST_CLEAN=''
ac_ct_CC='gcc'
ac_ct_CXX=''
ac_pt_STRIP=''
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
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
libpcapdir='libpcap'
localstatedir='${prefix}/var'
mandir='${prefix}/man'
oldincludedir='/usr/include'
pcredir='libpcre'
pkgpyexecdir=''
pkgpythondir=''
prefix='NONE'
program_transform_name='s,x,x,'
pyexecdir=''
pythondir=''
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
subdirs=''
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE_BUGREPORT ""
#define PACKAGE_NAME ""
#define PACKAGE_STRING ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""

configure: exit 77


*********************************************************
There are 2 parts i placed in bold because i think that is the problem but i dont know hot to correct this error ... please help ... 
Thank yoy

---

### Post by mkzimms on 2008-01-03
why not try using apt-get...

```
sudo apt-get install nmap
```

if you want to use the GUI front end try

```
sudo apt-get install nmapfe
```

---

### Post by Gipsy25 on 2008-01-03
ok it didnt gime an error so i am assuming thats good ... you were right thank you. 
now is the program installed or i nedd to do make  config and all that .. 
sorry im new at this ... 
if is installed how do i bring the program up ?

thank you again ..

---

### Post by Dr Small on 2008-01-03
No, you were previously attempting to compile the program from source. When you ran the latter commands, it automatically installed it for you from the Ubuntu Repositories.

To launch the applications with GUI, run:
```
nmapfe
```

Or, from the command line:
```
nmap
```

---

### Post by Gipsy25 on 2008-01-03
k first let me thank you for taking the time and help me out here 
but when u said "apps with gui" i dont know what u mean also the command line im assuming you are talking about the terminal right ???
ok i tried nmap and it gives me a bunch of optinos so im assuming this one is for the terminal and the other to use with a gui ... (use the gui front end) do i got this right ???

Thank you again ...

---

### Post by mkzimms on 2008-01-03
i would start out with nmapfe because it will give you a graphical representation of what its doing in the command line...  it will even show you at the bottom of the window the command its inputing to the command line so you can get a feel for what switches are being set (switches = options).  

[-X **be careful what networks you run nmap against.  a lot of network administrators will respond to this type of probing as an attack.**

---

### Post by Gipsy25 on 2008-01-03
Thanks for the advice i appreciate it .. i mean that .. well now is working .. so 
Im a happy camper

---

