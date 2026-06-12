---
title: "trying to install emacs from source"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by vertex78 on 2006-09-01
Hello, I am trying to learn how to install programs from source so I thought a good one to start with is emacs. I downloaded the latest tarball from gnu-emacs and ran the ./configure file and here is the results from it:

```

zach@ubuntu:~/Desktop/emacs-21.4$ ./configure
creating cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking whether ln -s works... yes
checking how to run the C preprocessor... gcc -E
checking for a BSD compatible install... /usr/bin/install -c
checking for bison... no
checking for byacc... no
checking for ranlib... ranlib
checking for AIX... no
checking the machine- and system-dependent files to find out
 - which libraries the lib-src programs will want, and
 - whether the GNU malloc routines are usable
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking for machine/soundcard.h... no
checking for sys/soundcard.h... yes
checking for soundcard.h... no
checking for _oss_ioctl in -lossaudio... no
checking for sys/select.h... yes
checking for sys/timeb.h... yes
checking for sys/time.h... yes
checking for unistd.h... yes
checking for utime.h... yes
checking for linux/version.h... yes
checking for sys/systeminfo.h... no
checking for termios.h... yes
checking for limits.h... yes
checking for string.h... yes
checking for stdlib.h... yes
checking for termcap.h... no
checking for stdio_ext.h... yes
checking for fcntl.h... yes
checking for term.h... no
checking for strings.h... yes
checking for ANSI C header files... yes
checking whether time.h and sys/time.h may both be included... yes
checking for sys_siglist declaration in signal.h or unistd.h... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for struct utimbuf... yes
checking return type of signal handlers... void
checking for speed_t... yes
checking for struct timeval... yes
checking for struct exception... no
checking whether struct tm is in sys/time.h or time.h... time.h
checking for tm_zone in struct tm... yes
checking for tm_gmtoff in struct tm... yes
checking for gcc option to accept ANSI C... none needed
checking for function prototypes... yes
checking for working volatile... yes
checking for working const... yes
checking for void * support... yes
checking whether make sets ${MAKE}... yes
checking for long file names... yes
checking for X... no
checking for malloc_get_state... yes
checking for malloc_set_state... yes
checking whether __after_morecore_hook exists... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for sys/stat.h... yes
checking for getpagesize... yes
checking for working mmap... yes
checking for dnet_ntoa in -ldnet... no
checking for main in -lXbsd... no
checking for cma_open in -lpthreads... no
checking for XFree86 in /usr/X386... no
checking whether netdb declares h_errno... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for sqrt in -lm... yes
checking for maillock in -lmail... no
checking for maillock in -llockfile... no
checking for liblockfile.so... no
checking for touchlock... no
checking for maillock.h... no
checking for gethostname... yes
checking for getdomainname... yes
checking for dup2... yes
checking for rename... yes
checking for closedir... yes
checking for mkdir... yes
checking for rmdir... yes
checking for sysinfo... yes
checking for random... yes
checking for lrand48... yes
checking for bcopy... yes
checking for bcmp... yes
checking for logb... yes
checking for frexp... yes
checking for fmod... yes
checking for rint... yes
checking for cbrt... yes
checking for ftime... yes
checking for res_init... no
checking for setsid... yes
checking for strerror... yes
checking for fpathconf... yes
checking for select... yes
checking for mktime... yes
checking for euidaccess... yes
checking for getpagesize... (cached) yes
checking for tzset... yes
checking for setlocale... yes
checking for utimes... yes
checking for setrlimit... yes
checking for setpgid... yes
checking for getcwd... yes
checking for getwd... yes
checking for shutdown... yes
checking for strftime... yes
checking for getaddrinfo... yes
checking for __fpending... yes
checking for mblen... yes
checking for mbrlen... yes
checking for strsignal... yes
checking for setitimer... yes
checking for ualarm... yes
checking for index... yes
checking for rindex... yes
checking for gai_strerror... yes
checking for mkstemp... yes
checking for sys/time.h... (cached) yes
checking for unistd.h... (cached) yes
checking for alarm... yes
checking for working mktime... yes
checking for getloadavg... yes
checking for getloadavg... (cached) yes
checking whether getloadavg requires setgid... no
checking for _LARGEFILE_SOURCE value needed for large files... 1
checking for fseeko... yes
checking for grantpt... yes
checking for getpt... yes
checking for tparm in -lncurses... no
checking for dgettext in -lintl... no
checking whether localtime caches TZ... no
checking for gettimeofday... yes
checking whether gettimeofday can accept two arguments... yes
checking for struct timezone... yes
checking for socket... yes
checking for netinet/in.h... yes
checking for arpa/inet.h... yes
checking whether system supports dynamic ptys... yes
checking for pid_t... yes
checking for vfork.h... no
checking for working vfork... yes
checking for size_t... yes

Configured for `i686-pc-linux-gnu'.

  Where should the build process find the source code?    /home/zach/Desktop/emacs-21.4
  What operating system and machine description files should Emacs use?
        `s/gnu-linux.h' and `m/intel386.h'
  What compiler should emacs be built with?               gcc -g -O2
  Should Emacs use the GNU version of malloc?             yes
      (Using Doug Lea's new malloc from the GNU C Library.)
  Should Emacs use a relocating allocator for buffers?    yes
  Should Emacs use mmap(2) for buffer allocation?         no
  What window system should Emacs use?                    none
  What toolkit should Emacs use?                          none
  Where do we find X Windows header files?                NONE
  Where do we find X Windows libraries?                   NONE
  Does Emacs use -lXaw3d?                                 no
  Does Emacs use -lXpm?                                   no
  Does Emacs use -ljpeg?                                  no
  Does Emacs use -ltiff?                                  no
  Does Emacs use -lungif?                                 no
  Does Emacs use -lpng?                                   no
  Does Emacs use X toolkit scroll bars?                   no

updating cache ./config.cache
creating ./config.status
creating Makefile
creating lib-src/Makefile.c
creating oldXMenu/Makefile
creating man/Makefile
creating lwlib/Makefile
creating src/Makefile.c
creating lisp/Makefile
creating leim/Makefile
creating src/config.h
creating src/epaths.h
creating lib-src/Makefile
creating src/Makefile
zach@ubuntu:~/Desktop/emacs-21.4$

```

In the top where it says checking for whatever... then either yes or no, where is says no are these things that I have to fix? 

Then are the things in the following stuff I also need to fix?
```

Should Emacs use mmap(2) for buffer allocation?         no
  What window system should Emacs use?                    none
  What toolkit should Emacs use?                          none
  Where do we find X Windows header files?                NONE
  Where do we find X Windows libraries?                   NONE
  Does Emacs use -lXaw3d?                                 no
  Does Emacs use -lXpm?                                   no
  Does Emacs use -ljpeg?                                  no
  Does Emacs use -ltiff?                                  no
  Does Emacs use -lungif?                                 no
  Does Emacs use -lpng?                                   no
  Does Emacs use X toolkit scroll bars?                   no

```

---

### Post by jordanmthomas on 2006-09-01
Not sure about the second part

The first part, where it says 'no' is not a problem, it's just deciding how it needs to be compiled.  It looks like you are ready to run make, but you may want to check on the missing X headers and X libraries.

You might need to install  xserver-xorg-dev 
```
sudo apt-get install  xserver-xorg-dev 
```

---

### Post by vertex78 on 2006-09-01
I intalled xserver-xorg-dev and then i ran make distclean for emacs, then i re-ran ./configure and it did not change anything. So I guess I will just go ahead and try to compile the code.

---

### Post by monktbd on 2006-09-01
I did not look at the emacs installing procedure but probably the x-server settings can be set with something like:

> ./configure --enable-x11

This should be described in the install.txt or similar file.

---

### Post by vertex78 on 2006-09-01
well i ran make and I got all kinds a warnings like:

```

process.c:4036: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
process.c:4036: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
process.c:4036: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
process.c:4036: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
process.c:4036: warning: pointer targets in passing argument 1 of ‘__builtin_strcmp’ differ in signedness
gcc -c -D_BSD_SOURCE   -Demacs -DHAVE_CONFIG_H   -I. -I/home/zach/Desktop/emacs-21.4/src -D_BSD_SOURCE -g -O2 callproc.c
callproc.c: In function ‘Fcall_process’:
callproc.c:373: warning: pointer targets in passing argument 1 of ‘emacs_open’ differ in signedness
callproc.c:511: warning: pointer targets in passing argument 1 of ‘creat’ differ in signedness
callproc.c:779: warning: pointer targets in passing argument 1 of ‘insert_1_both’ differ in signedness
callproc.c:791: warning: pointer targets in passing argument 2 of ‘detect_coding’ differ in signedness
callproc.c:799: warning: pointer targets in passing argument 2 of ‘decode_coding’ differ in signedness
callproc.c:799: warning: pointer targets in passing argument 3 of ‘decode_coding’ differ in signedness
callproc.c:818: warning: pointer targets in passing argument 1 of ‘insert_1_both’ differ in signedness
callproc.c:856: warning: pointer targets in passing argument 1 of ‘insert_1_both’ differ in signedness
callproc.c:884: warning: pointer targets in initialization differ in signedness
callproc.c:884: warning: pointer targets in initialization differ in signedness

```

After it was finished, i tried typing emacs and emacs21 at the terminal to see if it would load and it just said bash: /usr/bin/emacs: No such file or directory

any suggestions of what i should try next?

---

### Post by monktbd on 2006-09-01
did the make finish without an error?
the warnings usually do not matter.

after a make you should do a > sudo make installto install the program at the right place. 
disadvantage: you cannot easily uninstall it unless the source files came with an uninstall script.
easier would be to install checkinstall which makes a deb or rpm which you then can easily install/deinstall with the package manager (deb und dpkg in the case of ubuntu).


edit: see also [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

