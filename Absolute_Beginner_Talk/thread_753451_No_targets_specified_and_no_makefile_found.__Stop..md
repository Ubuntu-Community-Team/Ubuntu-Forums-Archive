---
title: "*** No targets specified and no makefile found.  Stop."
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by chachu on 2008-04-12
I'm stuck on installing stuff onto ubuntu 7.10,

this is how far i've got till now,
Downloaded the software 
extracted it to desktop.
moved the terminal to the right director,
./configure
make
this is where im stuck, make command dosen't work
 ```
 mohsin@mohsin-desktop:~$ cd '/home/mohsin/Desktop/d4x-2.5.7.1'




mohsin@mohsin-desktop:~/Desktop/d4x-2.5.7.1$ ./configure





-----------------------------------------------------------------------------

                         d4x -- Web Downloader for X

 Version: 2.5.7.1                                           chuchelo@krasu.ru
-----------------------------------------------------------------------------
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... (cached) mawk
checking for ranlib... ranlib
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for library containing strerror... none required
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for signed... yes
checking for inline... inline
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for off_t... yes
checking for size_t... yes
checking for long long... yes
checking for long double... yes
checking for wchar_t... yes
checking for wint_t... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for intmax_t... yes
checking whether printf() supports POSIX/XSI format strings... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether we are using the GNU C Library 2.1 or newer... yes
checking whether integer division by zero raises SIGFPE... yes
checking for unsigned long long... yes
checking for inttypes.h... yes
checking whether the inttypes.h PRIxNN macros are broken... no
checking for stdint.h... (cached) yes
checking for SIZE_MAX... yes
checking for stdint.h... (cached) yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for ptrdiff_t... yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking nl_types.h usability... yes
checking nl_types.h presence... yes
checking for nl_types.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for asprintf... yes
checking for fwprintf... yes
checking for getcwd... yes
checking for getegid... yes
checking for geteuid... yes
checking for getgid... yes
checking for getuid... yes
checking for mempcpy... yes
checking for munmap... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for snprintf... yes
checking for stpcpy... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strtoul... yes
checking for tsearch... yes
checking for wcslen... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for __fsetlocking... yes
checking whether _snprintf is declared... no
checking whether _snwprintf is declared... no
checking whether feof_unlocked is declared... yes
checking whether fgets_unlocked is declared... no
checking whether getc_unlocked is declared... yes
checking for iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo and CODESET... yes
checking for LC_MESSAGES... yes
checking for bison... no
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for autogen... ${SHELL} /home/mohsin/Desktop/d4x-2.5.7.1/admin/missing --run autogen
checking for doxygen... ${SHELL} /home/mohsin/Desktop/d4x-2.5.7.1/admin/missing --run doxygen
checking for gengetopt... no
checking for rpm... ${SHELL} /home/mohsin/Desktop/d4x-2.5.7.1/admin/missing --run rpm
checking for dot... no
checking whether ln -s works... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for esd-config... no
checking for ESD - version >= 0.2.7... no
*** The esd-config script installed by ESD could not be found
*** If ESD was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the ESD_CONFIG environment variable to the
*** full path to esd-config.
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.4.0... yes (version 2.14.1)
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GTK+ - version >= 2.4.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: *** GTK >= 2.4.0 not installed! ***



mohsin@mohsin-desktop:~/Desktop/d4x-2.5.7.1$ make


make: *** No targets specified and no makefile found.  Stop.


mohsin@mohsin-desktop:~/Desktop/d4x-2.5.7.1$ 

```


I've added a screen shot for the folder of the program aswell 

why do i get the error make: *** No targets specified and no makefile found.  Stop.  And how do i fix,

FYI today is the second day of me using Ubuntu and i have never ever used linux before so please go slow with what every you are explaining.

Thanks.

---

### Post by llamakc on 2008-04-12
```
checking for GTK+ - version >= 2.4.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: *** GTK >= 2.4.0 not installed! ***
```

Make is ran AFTER a successful ./configure is ran. Yours was not successful. See the error above.

You need to satisfy the dependencies for the program. What does the README show?

More importantly why are you building it from source? This same version is available with apt-get or Synaptic.

```

sudo apt-get install d4x

```

Voila!

---

### Post by hyper_ch on 2008-04-12
d4x is in the repos... use that [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by forestpixie on 2008-04-12
Is d4x a download manager if it is you can get it from the repos, at least it's in hardy

```
sudo apt-get install d4x
```

Edit - if you haven't enabled your software sources yet - the apt-get mightn't work. Open software sources - System > Admin - tick all the boxes except sources and reload

---

### Post by llamakc on 2008-04-12
> **forestpixie said:**
> Is d4x a download manager if it is you can get it from the repos, at least it's in hardy

```
sudo apt-get install d4x
```

Good catch! I'm on HH too and skipped right over their use of 7.10. Luckily it's available for the OP also.


[http://packages.ubuntu.com/search?keywords=d4x&searchon=names&suite=gutsy&section=all](http://packages.ubuntu.com/search?keywords=d4x&searchon=names&suite=gutsy&section=all)

---

### Post by forestpixie on 2008-04-12
Of course - neither of us have thought that the op might not know what to do with the code - so hyper_ch caught that one!

---

### Post by chachu on 2008-04-12
> **llamakc said:**
> 
More importantly why are you building it from source? This same version is available with apt-get or Synaptic.

```

sudo apt-get install d4x

```

Voila!


Thank you for the help, i got it installed, and its working fine, but i'd still like to resolve this issue of building stuff from source.

If you dont mind helping me out.

So i'm missing GTK+ somthing right?? where do i get that from? or how


[quote=forestpixie]
Edit - if you haven't enabled your software sources yet - the apt-get mightn't work. Open software sources - System > Admin - tick all the boxes except sources and reload
[/quote]

I did not get this part, i mean there are no boxes to tick :S:confused:

---

### Post by forestpixie on 2008-04-12
Not gonna be much help with the build from source- only done it once. But for the other a picture paints a thousand words.

---

### Post by llamakc on 2008-04-12
> So i'm missing GTK+ somthing right?? where do i get that from? or how

I asked you what was in the README file. Open it and read it. See if it lists the dependencies. Some source packages will list the dependencies with a "Debian-like" name so it makes it easy to figure it out.

If not, you are typically gonna want the *-dev packages. That means if the ./configure script spits out that you're missing foo2.1 you would search for and install foo2.1-dev and then RE-RUN the ./configure script. It will most likely then be MISSING something else. Repeat the above scenario.

You can search for packages in the terminal with the command

```


apt-get search foo | grep dev


```

where "foo" is what the configure script said you were missing.

Also, that psychocats link that was posted is an EXCELLENT place for you to start.

---

### Post by chachu on 2008-04-13
Thanks, i'll to figure out, and report back :)

BTw this is what thre readme file said.

```

~~~~~~~~~~~~~~~~~~~~~~~~~~~~
*      REQUIREMENTS        *
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To make this package you need the following tools/libs:

GTK+ 2.4.0
http://www.gtk.org


~~~~~~~~~~~~~~~~~~~~~~~~~~~~
* UPGRADE FROM 2.0x to 2.4 *
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Begining from version 2.4 Downloader for X uses .ntrc_2 directory in your
home directory to store its configuration data, queues of downloads etc.
The main reason to change default directory is switching from GTK1.x to GTK2.
GTK2 is fully unicode library so D4X have to be unicode too. If you want to
convert your old .ntrc data to new just recode them to utf8 code page.
For example in my case I've used next command (bash):

for i in ~/ntrc/*; do iconv -f koi8-r -t utf8 $i>~/ntrc_2/`basename $i'; done

You can use another codepage converting tool instead of 'iconv' and most of
you have to use another codepage instead of 'koi8-r'


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
* --enable-extra-optimize notes *
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To get even more hardcore optimized code it is recommended to
specify architecture specific options (like code and data align)
in $prefix/etc/config.site file by defining CXXFLAGS like this:

CXXFLAGS="-march=athlon-xp -mfpmath=387,sse"

Alternative method to specify config.site location is to use
CONFIG_SITE environment variable.

Also to set architecture specific options you can define CXXFLAGS
just before running ./configure script in command line.
Read gcc manual to get list of supported architecture options.

BTW, it is not neccessary to specify both --enable-release and
--enable-extra-optimize options... -- read ./configure --help
once again :)


```

---

### Post by llamakc on 2008-04-13
```

sudo apt-get install libgtk2.0-dev

```

:)

---

