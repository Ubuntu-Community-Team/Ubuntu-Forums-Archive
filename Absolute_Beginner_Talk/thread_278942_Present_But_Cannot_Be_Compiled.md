---
title: "Present But Cannot Be Compiled"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by senok on 2006-10-17
**hi there...please help me to solve this error when i try to compile the [GNOME BLUETOOTH REMOTE CONTROL (GBTcr)]("http://gbtcr.chileforge.cl/") from cvs file...how can i fix this prob...the software GBTcr can't function properly cause this error..please help me...**:confused: 

```
checking bluetooth/rfcomm.h usability... no
checking bluetooth/rfcomm.h presence... yes
configure: WARNING: bluetooth/rfcomm.h: present but cannot be compiled
configure: WARNING: bluetooth/rfcomm.h:     check for missing prerequisite headers?
configure: WARNING: bluetooth/rfcomm.h: see the Autoconf documentation
configure: WARNING: bluetooth/rfcomm.h:     section "Present But Cannot Be Compiled"
configure: WARNING: bluetooth/rfcomm.h: proceeding with the preprocessor's result
configure: WARNING: bluetooth/rfcomm.h: in the future, the compiler will take precedence
configure: WARNING:     ## ------------------------------------------ ##
configure: WARNING:     ## Report this to the AC_PACKAGE_NAME lists.  ##
configure: WARNING:     ## ------------------------------------------ ##
checking for bluetooth/rfcomm.h... yes
checking bluetooth/hci.h usability... no
checking bluetooth/hci.h presence... yes
configure: WARNING: bluetooth/hci.h: present but cannot be compiled
configure: WARNING: bluetooth/hci.h:     check for missing prerequisite headers?
configure: WARNING: bluetooth/hci.h: see the Autoconf documentation
configure: WARNING: bluetooth/hci.h:     section "Present But Cannot Be Compiled"
configure: WARNING: bluetooth/hci.h: proceeding with the preprocessor's result
configure: WARNING: bluetooth/hci.h: in the future, the compiler will take precedence
configure: WARNING:     ## ------------------------------------------ ##
configure: WARNING:     ## Report this to the AC_PACKAGE_NAME lists.  ##
configure: WARNING:     ## ------------------------------------------ ##
checking for bluetooth/hci.h... yes
checking bluetooth/hci_lib.h usability... no
checking bluetooth/hci_lib.h presence... yes
configure: WARNING: bluetooth/hci_lib.h: present but cannot be compiled
configure: WARNING: bluetooth/hci_lib.h:     check for missing prerequisite headers?
configure: WARNING: bluetooth/hci_lib.h: see the Autoconf documentation
configure: WARNING: bluetooth/hci_lib.h:     section "Present But Cannot Be Compiled"
configure: WARNING: bluetooth/hci_lib.h: proceeding with the preprocessor's result
configure: WARNING: bluetooth/hci_lib.h: in the future, the compiler will take precedence
configure: WARNING:     ## ------------------------------------------ ##
configure: WARNING:     ## Report this to the AC_PACKAGE_NAME lists.  ##
configure: WARNING:     ## ------------------------------------------ ##
checking for bluetooth/hci_lib.h... yes
```

---

### Post by Sef on 2006-10-17
To compile, you need build-essential.

Have you downloaded it? If not, then open the terminal.

sudo aptitude update

sudo aptitude install build-essential


Also take a look at this tutorial: [How to Install Anything.]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by senok on 2006-10-17
Thank for the response...
I already install build-essential packages and try compile again...but the same problem happen..

I googling and find this [[COLOR="Red"]solution[/COLOR]]("http://www.kaffe.org/pipermail/kaffe/2003-May/042053.html") but can't understand what should i do..

```

Header Present But Cannot Be Compiled
=====================================

   The most important guideline to bear in mind when checking for
features is to mimic as much as possible the intended use.
Unfortunately, old versions of `AC_CHECK_HEADER' and `AC_CHECK_HEADERS'
failed to follow this idea, and called the preprocessor, instead of the
compiler, to check for headers.  As a result, incompatibilities between
headers went unnoticed during configuration, and maintainers finally
had to deal with this issue elsewhere.

   As of Autoconf 2.56 both checks are performed, and `configure'
complains loudly if the compiler and the preprocessor do not agree.
For the time being the result used is that of the preprocessor, to give
maintainers time to adjust their `configure.ac', but in the near
future, only the compiler will be considered.

   Consider the following example:

     $ cat number.h
     typedef int number;
     $ cat pi.h
     const number pi = 3;
     $ cat configure.ac
     AC_INIT
     AC_CHECK_HEADERS(pi.h)
     $ autoconf -Wall
     $ ./configure
     checking for gcc... gcc
     checking for C compiler default output... a.out
     checking whether the C compiler works... yes
     checking whether we are cross compiling... no
     checking for suffix of executables...
     checking for suffix of object files... o
     checking whether we are using the GNU C compiler... yes
     checking whether gcc accepts -g... yes
     checking for gcc option to accept ANSI C... none needed
     checking how to run the C preprocessor... gcc -E
     checking for egrep... grep -E
     checking for ANSI C header files... yes
     checking for sys/types.h... yes
     checking for sys/stat.h... yes
     checking for stdlib.h... yes
     checking for string.h... yes
     checking for memory.h... yes
     checking for strings.h... yes
     checking for inttypes.h... yes
     checking for stdint.h... yes
     checking for unistd.h... yes
     checking pi.h usability... no
     checking pi.h presence... yes
     configure: WARNING: pi.h: present but cannot be compiled
     configure: WARNING: pi.h: check for missing prerequisite headers?
     configure: WARNING: pi.h: proceeding with the preprocessor's result
     configure: WARNING:     ## ------------------------------------ ##
     configure: WARNING:     ## Report this to bug-autoconf@gnu.org. ##
     configure: WARNING:     ## ------------------------------------ ##
     checking for pi.h... yes

The proper way the handle this case is using the fourth argument (*note
Generic Headers::):

     $ cat configure.ac
     AC_INIT
     AC_CHECK_HEADERS(number.h pi.h,,,
     [[#if HAVE_NUMBER_H
     # include <number.h>
     #endif
     ]])
     $ autoconf -Wall
     $ ./configure
     checking for gcc... gcc
     checking for C compiler default output... a.out
     checking whether the C compiler works... yes
     checking whether we are cross compiling... no
     checking for suffix of executables...
     checking for suffix of object files... o
     checking whether we are using the GNU C compiler... yes
     checking whether gcc accepts -g... yes
     checking for gcc option to accept ANSI C... none needed
     checking for number.h... yes
     checking for pi.h... yes

   See *Note Particular Headers::, for a list of headers with their
prerequisite.
```

This line i don't really understand...:confused: 

```
[COLOR="Red"]
    $ cat number.h
     typedef int number;
     $ cat pi.h
     const number pi = 3;
     $ cat configure.ac
     AC_INIT
     AC_CHECK_HEADERS(pi.h)
     $ autoconf -Wall[/COLOR]
```

Thanx 4 any any help again....

---

### Post by monktbd on 2006-10-17
actually there are only warnings and no error.

so does the configure script terminate properly ( = without errors)?

the warnings should only become a problem (=errors) in future versions of the build environment

---

### Post by docshawnc on 2006-10-17
I'm not an expert on compiling things, but once had a problem doing so even though I had the build-essential present.  The problem was I didn't have the headers - fixed it by:

sudo apt-get install build-essential linux-headers-`uname -r`

---

### Post by senok on 2006-10-17
The sript have a error, the bluetooth from my pc can detect the mobile phone but when transfer data from pc to mobile phone give some error

```
sere@sere:~/gbtcr/src$ ./gbtcr
[Leyendo configuraciones]
[Chequeando dispositivo Bluetooth]
[Iniciando GBTcr 0.81beta]
-Encontrados 5 plugins
Warning: No puedo liberar socket (!w /dev/rfcomm0): Operation not permitted
Warning: No puedo crear socket (!w /dev/rfcomm0): Operation not permitted

```

I try this, sudo apt-get install build-essential linux-headers-`uname -r`..but the same probe occur...any help appriciate

---

### Post by monktbd on 2006-10-17
maybe the bluetooth program needs to be started with root rights?

i dont know and it might be wise to check the documentation if that is necessary. 
but some operations on devices (/dev) are surely only available for  root unless otherwise specified.

edit: (a guess out in the blue is that it might want to write to those devices and cannot - !w <- let's me think that)

---

