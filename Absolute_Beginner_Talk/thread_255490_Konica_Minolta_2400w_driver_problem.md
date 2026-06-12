---
title: "Konica Minolta 2400w driver problem"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by Mister T on 2006-09-11
Hi,

I'm trying to install my printer and I've already tried a lot of things. I've downloaded the driver and the readme file says:

Building and installing the driver from the source distribution:
----------------------------------------------------------------

    1. Make sure that all prerequisites are installed (see above)

    2. Download m2300w-<version>.tar.gz from
       [http://sourceforge.net/project/showfiles.php?group_id=108751](http://sourceforge.net/project/showfiles.php?group_id=108751)

    3. Unpack the archive:

       $ tar zxvf m2300w-<version>.tar.gz
       	   or
       $ gzip -dc m2300w-<version>.tar.gz | tar xvf -
       (if you are not using GNU tar)

    4. Enter the top-level directory and run "configure"

       $ cd m2300w-<version>
       $ ./configure

    5. Run make

       $ make

    6. Install the files (needs to be done as root)

	$ su
	Password: ********
	# make install

    7. Run cups config to install a new printer

       If you are upgrading from a previous version of the m2300w
       driver, then REMOVE all printer queues which are associated
       with the m2300w driver and reinstall them from the scratch.

Everything goes fine until step 6. The console give's the error:

************************************************************
*** Please remove all printer queues which are associated
*** with the m2300w driver from your spooler's configuartion
*** and reinstall them from the scratch
************************************************************

I don't really understand what that means and what I should to do or how I should do it, so can somebody help me please?

Thanks!
Tom

---

### Post by aseneca on 2006-09-30
You know the driver used to work quite well.  I think there's been a recent update (...say about 4 months ago) that has rendered the driver useless on a direct connect basis. 

What I did was made it a network printer on a windows machine.  Ever since then I have had no difficulties printing to....  Not sure what your network configurations are....
Jason

---

### Post by taladon on 2006-11-05
Mister T,

It sounds like you got very far along with the printer driver.
I also own a 2400w.

The message you are getting means you just need to go in and delete the all the printers in System->Administration->Printing and re-install selecting the 2400 from Konica Minolta.

After adding the printer, it will work but it will take a very long time to print (5-15 minutes per page)

There is a known bug causing it. To fix it requires downloading the latest cups source code from [www.cups.org](www.cups.org) and changing a couple lines, then installing using ./configure, make, and make install.

I realize this sounds complicated, but it's really not too bad.

I'm using cups 1.3svn-r6068, but any 1.3 should work.

First off extract the source code using the following command:

$ tar zxvf m2300w-<version>.tar.gz
or
$ gzip -dc m2300w-<version>.tar.gz | tar xvf -
(if you are not using GNU tar)

into whatever directory you want. I created a folder off my home directory called printsrc so for me my "main folder" was /home/taladon/printsrc

i.e. mkdir /home/taladon/printsrc
cd /home/taladon/printsrc

gzip -dc /home/taladon/download/m2300w-r6068.gz | tar xvf -

From your main folder, 
Start by editing /backend/usb-unix.c

Go to where the big comment that starts with "Disable backchannel data when printing...

The line below that says use_bc = ....

Delete that line and put use_bc = 0;

Save the file and exit.

From the main folder, do the following:

./configure
make
sudo make install

Then for good measure I did

sudo /etc/init.d/cupsys restart
sudo /etc/init.d/cupsd restart

Then go into System->Administration->Printing and delete / install the printer again.

Let me know if you have any more questions. I'll do what I can to help.

--John Jackson
[email]--taladon@gmail.com[/email]

---

### Post by wakalapi on 2006-12-04
Edgy came with 1.2.4. I got my 2400W to print (finally) after following the same procedure, except I upgraded to CUPS 1.2.7 rather than 1.3.x. So if (for whatever reason) you don't want the most bleeding edge version of CUPS I can vouch that even 1.2.7 works, but I haven't tried 1.3.x yet to make any kind of performance comparison. Be sure to do the edit mentioned above.

---

### Post by rhyshowitt on 2007-02-01
Great work guys, and could you please provide a few more of the intermediate steps for us newbies?

OK, I've downloaded CUPS 1.2.7.

Where do I extract it to?

The instructions say to edit a file -- which one, one of the CUPS files in the unidentified directory?

I think I can do the edits (sudo gedit?) and have a good go at the rest.  But I'm sure there are others even more bright shiny new at this than I am, so a consolidated list of the steps would be a great help.

Rhys Howitt
Canberra, Australia

---

### Post by dewme5 on 2007-02-19
I'm new to linux in general, and problems like this is why I've been unable to conquer it before.  [http://www.ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://www.ubuntuforums.org/images/smilies/smiley-faces-75.gif)

Anyway.  After several attempts, I wasn't getting anything to work not even after 15min.  So, I decided to start from scratch.  I deleted the previous attempts from system>administration>printing

I also deleted everything in quey

then, I went in a deleted everything minolta related in my /tmp file (that's where all previous work was done from)  

So, now from starting from nothing, I downloaded CUPS 1.2.7 tar.gz into my /tmp as well as m2300w 0.51 tar.gz


 I followed taladon's instructions (to the letter!) first, but using CUPS 1.2.7 instead of 1.3

then, I followed mister T's instructions, once again to the letter!  and, I am now printing in both color and b/w.  and it's printing as quick as it did on the windows machine (well, almost)

Thank you [http://ubuntuforums.org/images/smilies/star.png](http://ubuntuforums.org/images/smilies/star.png)

---

### Post by taladon on 2007-04-11
Note: I used Cups 1.3 because I could not get it to work in the CUPS 1.2 versions I tried. I would not recommend using any version of cups prior to the 1.2.7 that others have got to work.

---

### Post by limbourg31 on 2007-06-28
when I try to do ./configure, the program generates these outputs:
[INDENT]
user@user-desktop:~/printers/cups-1.3svn-r6605$ ./configure
checking for gawk... gawk
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
[/INDENT]

I made "printers" my folder for cups in my home directory, unpacked the KonicaMinolta packages and also extracted the cups-1.3svn-r6605 package. since nothing worked the first time around, with the same output, i did autoconf -f like it said in the cups INSTALL.txt file. Any idea what's going on? 

config.log says:

[INDENT]
This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by configure, which was
generated by GNU Autoconf 2.61.  Invocation command line was

  $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = MORT
uname -m = i686
uname -r = 2.6.20-16-generic
uname -s = Linux
uname -v = #2 SMP Thu Jun 7 20:19:32 UTC 2007

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = i686
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
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

configure:1965: checking for gawk
configure:1981: found /usr/bin/gawk
configure:1992: result: gawk
configure:2051: checking for gcc
configure:2067: found /usr/bin/gcc
configure:2078: result: gcc
configure:2316: checking for C compiler version
configure:2323: gcc --version >&5
gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2326: $? = 0
configure:2333: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
configure:2336: $? = 0
configure:2343: gcc -V >&5
gcc: '-V' option must have argument
configure:2346: $? = 1
configure:2369: checking for C compiler default output file name
configure:2396: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:2399: $? = 1
configure:2437: result: 
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define CUPS_SVERSION "CUPS v1.3svn"
| #define CUPS_MINIMAL "CUPS/1.3svn"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:2444: error: C compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_env_CCC_set=
ac_cv_env_CCC_value=
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
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_prog_AWK=gawk
ac_cv_prog_ac_ct_CC=gcc

## ----------------- ##
## Output variables. ##
## ----------------- ##

AMANDIR=''
AR=''
ARCH32FLAGS=''
ARCH64FLAGS=''
ARCHFLAGS=''
ARFLAGS=''
AWK='gawk'
BACKLIBS=''
CC='gcc'
CFLAGS=''
CPP=''
CPPFLAGS=''
CUPSDLIBS=''
CUPS_BROWSE_LOCAL_PROTOCOLS=''
CUPS_BROWSE_REMOTE_PROTOCOLS=''
CUPS_BROWSE_SHORT_NAMES=''
CUPS_BROWSING=''
CUPS_CACHEDIR=''
CUPS_CONFIG_FILE_PERM=''
CUPS_DATADIR=''
CUPS_DEFAULT_DOMAINSOCKET=''
CUPS_DEFAULT_SHARED=''
CUPS_DOCROOT=''
CUPS_FONTPATH=''
CUPS_GROUP=''
CUPS_IMPLICIT_CLASSES=''
CUPS_LISTEN_DOMAINSOCKET=''
CUPS_LOCALEDIR=''
CUPS_LOGDIR=''
CUPS_LOG_FILE_PERM=''
CUPS_MAX_COPIES=''
CUPS_PRIMARY_SYSTEM_GROUP=''
CUPS_REQUESTS=''
CUPS_REVISION=''
CUPS_SERVERBIN=''
CUPS_SERVERROOT=''
CUPS_STATEDIR=''
CUPS_SYSTEM_AUTHKEY=''
CUPS_SYSTEM_GROUPS=''
CUPS_USER=''
CUPS_USE_NETWORK_DEFAULT=''
CUPS_VERSION='1.3svn'
CXX=''
CXXFLAGS=''
CXXLIBS=''
DBUSDIR=''
DEFAULT_IPP_PORT=''
DEFAULT_LAUNCHD_CONF=''
DEFAULT_RAW_PRINTING=''
DEFS=''
DNSSDLIBS=''
DSO32FLAGS=''
DSO64FLAGS=''
DSO=''
DSOFLAGS=''
DSOLIBS=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
ENCRYPTION_REQUIRED=''
EXEEXT=''
EXPORT_LDFLAGS=''
EXPORT_LIBJPEG=''
EXPORT_LIBPNG=''
EXPORT_LIBTIFF=''
EXPORT_LIBZ=''
EXPORT_SSLLIBS=''
FONTS=''
GREP=''
HTMLDOC=''
ICONDIR=''
IMGFILTERS=''
IMGLIBS=''
INITDDIR=''
INITDIR=''
INSTALL32=''
INSTALL64=''
INSTALLSTATIC=''
INSTALL_DATA=''
INSTALL_LANGUAGES=''
INSTALL_PROGRAM=''
INSTALL_SCRIPT=''
INSTALL_SYSV=''
JAVA=''
KRB5CONFIG=''
LANGUAGES=''
LARGEFILE=''
LAUNCHDLIBS=''
LD=''
LDARCHFLAGS=''
LDFLAGS=''
LEGACY_BACKENDS=''
LIB32CUPS=''
LIB32CUPSIMAGE=''
LIB32DIR=''
LIB64CUPS=''
LIB64CUPSIMAGE=''
LIB64DIR=''
LIBCUPS=''
LIBCUPSIMAGE=''
LIBCUPSORDER=''
LIBGNUTLSCONFIG=''
LIBGSSAPI=''
LIBJPEG=''
LIBLDAP=''
LIBMALLOC=''
LIBOBJS=''
LIBPAPER=''
LIBPNG=''
LIBS=''
LIBSLP=''
LIBTIFF=''
LIBTOOL=''
LIBZ=''
LINKCUPS=''
LINKCUPSIMAGE=''
LN=''
LTLIBOBJS=''
MAN1EXT=''
MAN5EXT=''
MAN7EXT=''
MAN8DIR=''
MAN8EXT=''
MENUDIR=''
MV=''
OBJEXT=''
OPTIM=''
PACKAGE_BUGREPORT=''
PACKAGE_NAME=''
PACKAGE_STRING=''
PACKAGE_TARNAME=''
PACKAGE_VERSION=''
PAMDIR=''
PAMFILE=''
PAMLIBS=''
PAMMOD=''
PAP=''
PATH_SEPARATOR=':'
PDFTOPS=''
PERL=''
PHP=''
PHPCONFIG=''
PHPDIR=''
PIEFLAGS=''
PKGCONFIG=''
PMANDIR=''
PTHREAD_FLAGS=''
PYTHON=''
RANLIB=''
RCLEVELS=''
RCSTART=''
RCSTOP=''
RELROFLAGS=''
RM=''
RMDIR=''
SED=''
SHELL='/bin/bash'
SSLFLAGS=''
SSLLIBS=''
STRIP=''
UNINSTALL32=''
UNINSTALL64=''
UNINSTALL_LANGUAGES=''
XINETD=''
ac_ct_CC='gcc'
ac_ct_CXX=''
bindir='${exec_prefix}/bin'
build_alias=''
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE}'
dvidir='${docdir}'
exec_prefix='NONE'
host_alias=''
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
mandir='${datarootdir}/man'
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

#define PACKAGE_NAME ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""
#define PACKAGE_STRING ""
#define PACKAGE_BUGREPORT ""
#define CUPS_SVERSION "CUPS v1.3svn"
#define CUPS_MINIMAL "CUPS/1.3svn"

configure: exit 77
[/INDENT]

---

### Post by christhemonkey on 2007-06-28
You need to have build-essential installed to be able to compile anything.

```
sudo apt-get install build-essential 
```

---

### Post by limbourg31 on 2007-06-28
thank you very much. I just reinstalled ubuntu, so i forgot to reinstall build-essential

---

### Post by limbourg31 on 2007-06-28
just another quick question... i ran  sudo /etc/init.d/cupsys restart but when i dot the next step  
"sudo /etc/init.d/cupsd restart" i get an error that the command is not found

---

### Post by christhemonkey on 2007-06-28
Try using tab to autocomplete,

so type:
```
sudo /etc/init.d/cups<PRESS TAB TWICE> 
```

That should list all the files in /etc/init.d/ that begin with cups (although if there is just one, then it will auto complete and you should continue with the howto after this step!)

---

### Post by PaulHuffman on 2007-09-20
Oh crap.  I'm just installed Ubuntu for the first time this week.  I couldn't get my Konica Minolta 2430 DL to print correctly.  I followed the above procedures, including install build-essential, except when I went to download cups I found a version 1.4 now available.  Anyway, I got a little error when I did the make install the cup after editing the changes to usb-unix-c.  Then the restart of cupsd gave an error:

[B]Installing in locale...
/usr/bin/install: missing file operand
Try `/usr/bin/install --help' for more information.
make[1]: *** [install-languages] Error 1
make: *** [install] Error 1
paul@paul-ESeries:~/cups/cups-1.4svn-r6956$ sudo /etc/init.d/cupsys restart
 * Restarting Common Unix Printing System: cupsd                                /usr/sbin/cupsd: symbol lookup error: /usr/sbin/cupsd: undefined symbol: _httpReadGNUTLS[/B]

Now when I go to System->Admin->Printing, all my printers are gone and Add a Printer goes through it's process but nothing happens, no printer appears, and no error message.  Also, when I look at step 2 of Add a Printer, now there's nothing in the Manufacturer pulldown list.  Looks like I shot down the printing system. Should I go back to cups 1.3?

Now System->Admin->Printing tells me the CUPS server could not be contacted.  I tried to kick CUPS in the *** with a sudo /etc/init.d/cupsys start command, but I get the following in the terminal window: /usr/sbin/cupsd: symbol lookup error: /usr/sbin/cupsd: undefined symbol: _httpReadGNUTLS    Looks like I have a bad symbol or line in the printer files.  The first time I went to System->Admin->Printing after kicking cupsys, I had an add new printer window behind the "Cups Server could not be contacted." message.  But now I just get the message. 

I thought my Solaris experience would help me, but this is so much different.

---

