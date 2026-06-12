---
title: "Trouble Installing Supertux"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by mac9416 on 2008-02-27
I am posting this from someone elses computer and don't have my Ubuntu Ultimate Edition 1.6 machine hooked up to the internet. I tried both the Supertux autopackage and tar.gz and here are the results:

tar.gz:
> 
mac9416@mac9416-desktop:~$ cd ~/supertux-0.3.1/
mac9416@mac9416-desktop:~/supertux-0.3.1$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for ar... /usr/bin/ar
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking whether byte ordering is bigendian... no
checking for xgettext... xgettext
checking if xgettext supports lisp... yes
checking for flex... no
checking for lex... no
checking for bison... no
checking for bison.exe... no
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking whether byte ordering is bigendian... (cached) no
checking for void *... yes
checking size of void *... 4
checking for build variant... optimize
checking whether binary relocation support should be enabled... no
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... /bin/bash: mk/autoconf/config.rpath: No such file or directory
done
checking for iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for gawk... gawk
checking for curl-config... no
checking whether libcurl is usable... no
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.4... yes
checking for Ogg... no
*** Could not run Ogg test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means Ogg was incorrectly installed
*** or that you have moved Ogg since it was installed.
configure: error: Please install libogg
mac9416@mac9416-desktop:~/supertux-0.3.1$ make
make: *** No targets specified and no makefile found.  Stop.
mac9416@mac9416-desktop:~/supertux-0.3.1$ 


autopackage:

> 
autopackage for "SuperTux platform game"


The installation of this software requires some additional support
code to be installed.

A] If the support code is found in a local directory, it will be used.
   The file containing the support code will be called:

      "autopackage.tar.bz2"

 or

B] If there is an active Internet connection, the support code will be
   downloaded from:

      "http://autopackage.org/downloads/latest/autopackage.tar.bz2"

   Proxy users should ensure the http_proxy environment variable is
   set, otherwise the download may fail.


Selection B --> OK to download and install support code now? (Y/n): y

Attempting download of [http://autopackage.org/downloads/latest/autopackage.tar.bz2](http://autopackage.org/downloads/latest/autopackage.tar.bz2) ... 
--10:15:55--  [http://autopackage.org/downloads/latest/autopackage.tar.bz2](http://autopackage.org/downloads/latest/autopackage.tar.bz2)
           => `autopackage.tar.bz2'
Resolving autopackage.org... failed: Name or service not known.
Download failed.


Attempting download of [http://www.wildgardenseed.com/autopackage/latest/autopackage.tar.bz2](http://www.wildgardenseed.com/autopackage/latest/autopackage.tar.bz2) ... 
--10:15:56--  [http://www.wildgardenseed.com/autopackage/latest/autopackage.tar.bz2](http://www.wildgardenseed.com/autopackage/latest/autopackage.tar.bz2)
           => `autopackage.tar.bz2'
Resolving [www.wildgardenseed.com](www.wildgardenseed.com)... failed: Name or service not known.
Download failed.


Attempting download of [http://www.allaboutgames.co.uk/autopackage/latest/autopackage.tar.bz2](http://www.allaboutgames.co.uk/autopackage/latest/autopackage.tar.bz2) ... 
--10:15:56--  [http://www.allaboutgames.co.uk/autopackage/latest/autopackage.tar.bz2](http://www.allaboutgames.co.uk/autopackage/latest/autopackage.tar.bz2)
           => `autopackage.tar.bz2'
Resolving [www.allaboutgames.co.uk](www.allaboutgames.co.uk)... failed: Name or service not known.
Download failed.



Please check your Internet connection, or try again later.

Press Enter to close this window.

The autopackage support code could not be installed.

It can be manually downloaded and installed by running the
installation script located in the downloaded archive.

Just remember, I can't use Synaptic so I am turning to the Forum for a workaround.

Thanks in advance.

---

### Post by mac9416 on 2008-02-27
Sorry to double post but I thought maybe I could download libogg and move it manually to my "Ultimate" machine. Assuming I could download libogg how could I install it?

---

### Post by eragon100 on 2008-02-27
You shuold just install ubuntu ultimate gamers edition, it comes with a ton of games including supertux :)

---

### Post by mac9416 on 2008-02-27
Yessir, I would do that but I hate to do another reformat/reinstall. Also Gamers Edition is aging. I like to have the latest/greatest. Thanks for helping me not to think I'm talking to a shadow though. I'm gettin' kind of lonely.:roll:

PS: I love the moderators anyway.:)

---

