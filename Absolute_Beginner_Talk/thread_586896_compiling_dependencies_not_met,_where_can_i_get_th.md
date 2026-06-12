---
title: "compiling dependencies not met, where can i get them?"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Luksion Knight on 2007-10-22
I used to be running breezy (i thought i was running feisty lol) and i had compiling all set up, but when i tried to upgrade straight to gutsy, it messed up my computer and i had to do a clean install. where can i get what i need for compiling? heres the error log for a failed configuration:
```
## ----------- ##
## Core tests. ##
## ----------- ##

configure:1751: checking for a BSD-compatible install
configure:1807: result: /usr/bin/install -c
configure:1818: checking whether build environment is sane
configure:1861: result: yes
configure:1889: checking for a thread-safe mkdir -p
configure:1928: result: /bin/mkdir -p
configure:1941: checking for gawk
configure:1971: result: no
configure:1941: checking for mawk
configure:1957: found /usr/bin/mawk
configure:1968: result: mawk
configure:1979: checking whether make sets $(MAKE)
configure:2000: result: yes
configure:2257: checking for g++
configure:2287: result: no
configure:2257: checking for c++
configure:2287: result: no
configure:2257: checking for gpp
configure:2287: result: no
configure:2257: checking for aCC
configure:2287: result: no
configure:2257: checking for CC
configure:2287: result: no
configure:2257: checking for cxx
configure:2287: result: no
configure:2257: checking for cc++
configure:2287: result: no
configure:2257: checking for cl.exe
configure:2287: result: no
configure:2257: checking for FCC
configure:2287: result: no
configure:2257: checking for KCC
configure:2287: result: no
configure:2257: checking for RCC
configure:2287: result: no
configure:2257: checking for xlC_r
configure:2287: result: no
configure:2257: checking for xlC
configure:2287: result: no
configure:2315: checking for C++ compiler version
configure:2322: g++ --version >&5
./configure: line 2323: g++: command not found
configure:2325: $? = 127
configure:2332: g++ -v >&5
./configure: line 2333: g++: command not found
configure:2335: $? = 127
configure:2342: g++ -V >&5
./configure: line 2343: g++: command not found
configure:2345: $? = 127
configure:2368: checking for C++ compiler default output file name
configure:2395: g++    conftest.cpp  >&5
./configure: line 2396: g++: command not found
configure:2398: $? = 127
configure:2436: result: 
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME "SpringLobby"
| #define PACKAGE_TARNAME "springlobby"
| #define PACKAGE_VERSION "0.0.1.0466"
| #define PACKAGE_STRING "SpringLobby 0.0.1.0466"
| #define PACKAGE_BUGREPORT "FIXME_our_bugs_email_address"
| #define PACKAGE "springlobby"
| #define VERSION "0.0.1.0466"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:2443: error: C++ compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_env_CCC_set=
ac_cv_env_CCC_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_path_install='/usr/bin/install -c'
ac_cv_path_mkdir=/bin/mkdir
ac_cv_prog_AWK=mawk
ac_cv_prog_make_make_set=yes

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /home/linkous/Desktop/springlobby-0.0.1.0466/missing --run aclocal-1.10'
AMDEPBACKSLASH=''
AMDEP_FALSE=''
AMDEP_TRUE=''
AMTAR='${SHELL} /home/linkous/Desktop/springlobby-0.0.1.0466/missing --run tar'
AUTOCONF='${SHELL} /home/linkous/Desktop/springlobby-0.0.1.0466/missing --run autoconf'
AUTOHEADER='${SHELL} /home/linkous/Desktop/springlobby-0.0.1.0466/missing --run autoheader'
AUTOMAKE='${SHELL} /home/linkous/Desktop/springlobby-0.0.1.0466/missing --run automake-1.10'
AWK='mawk'
CPPFLAGS=''
CXX='g++'
CXXDEPMODE=''
CXXFLAGS=''
CYGPATH_W='echo'
DEFS=''
DEPDIR=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EXEEXT=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='$(install_sh) -c -s'
LDFLAGS=''
LIBOBJS=''
LIBS=''
LTLIBOBJS=''
MAKEINFO='${SHELL} /home/linkous/Desktop/springlobby-0.0.1.0466/missing --run makeinfo'
OBJEXT=''
PACKAGE='springlobby'
PACKAGE_BUGREPORT='FIXME_our_bugs_email_address'
PACKAGE_NAME='SpringLobby'
PACKAGE_STRING='SpringLobby 0.0.1.0466'
PACKAGE_TARNAME='springlobby'
PACKAGE_VERSION='0.0.1.0466'
PATH_SEPARATOR=':'
SET_MAKE=''
SHELL='/bin/bash'
STRIP=''
VERSION='0.0.1.0466'
WX_CFLAGS=''
WX_CFLAGS_ONLY=''
WX_CONFIG_PATH=''
WX_CPPFLAGS=''
WX_CXXFLAGS=''
WX_CXXFLAGS_ONLY=''
WX_LIBS=''
WX_LIBS_STATIC=''
WX_VERSION=''
ac_ct_CXX=''
am__fastdepCXX_FALSE=''
am__fastdepCXX_TRUE=''
am__include=''
am__isrc=''
am__leading_dot='.'
am__quote=''
am__tar='${AMTAR} chof - "$$tardir"'
am__untar='${AMTAR} xf -'
bindir='${exec_prefix}/bin'
build_alias=''
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE_TARNAME}'
dvidir='${docdir}'
exec_prefix='NONE'
host_alias=''
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
install_sh='$(SHELL) /home/linkous/Desktop/springlobby-0.0.1.0466/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
mkdir_p='/bin/mkdir -p'
oldincludedir='/usr/include'
pdfdir='${docdir}'
prefix='NONE'
program_transform_name='s,x,x,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE_NAME "SpringLobby"
#define PACKAGE_TARNAME "springlobby"
#define PACKAGE_VERSION "0.0.1.0466"
#define PACKAGE_STRING "SpringLobby 0.0.1.0466"
#define PACKAGE_BUGREPORT "FIXME_our_bugs_email_address"
#define PACKAGE "springlobby"
#define VERSION "0.0.1.0466"

configure: exit 77
```

---

### Post by Maestro23 on 2007-10-22
First step: Get "build-essential"

> sudo apt-get install build essential

Try your compiling again.

---

### Post by Luksion Knight on 2007-10-22
E: Couldn't find package build

?

EDIT: you for got the hyphen in build essential, shoulod have been build-essential

---

### Post by Maestro23 on 2007-10-22
> **Luksion Knight said:**
> E: Couldn't find package build

?

EDIT: you for got the hyphen in build essential, shoulod have been build-essential

should be build-essential.

My bad...

---

