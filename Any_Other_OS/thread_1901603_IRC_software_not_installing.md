---
title: "IRC software not installing"
date: 2011-12-28
forum: Any Other OS
---

### Post by freshmeat20 on 2011-12-28
I don't know if this is the right support category. Or if I should put this in sevenforums. But I'm trying to install the irc client Bitchx through cygwin on windows7. I get part way through the ./configure and it stops here

checking for getpgid in unistd.h...


Am I missing a library? Ive tried re-downloading etc and still the same problem. Any ideas?

---

### Post by searchfgold6789 on 2011-12-28
Does anything come after that line you posted?

---

### Post by freshmeat20 on 2011-12-28
Nope it just stops right there. Heres the full log

checking for gcc... gcc
checking for C compiler default output... a.exe
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... .exe
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether ln -s works... yes
checking for gmake... no
checking for make... make
checking whether make sets ${MAKE}... yes
checking how to run the C preprocessor... gcc -E
checking whether gcc needs -traditional... no
checking for library containing strerror... none required
checking for AIX... no
checking for gawk... gawk
checking for getpwnam in -lsun... no
checking for inet_addr in -ldgc... no
checking for res_mkquery in -lresolv... yes
checking for res_mkquery in -lc... yes
checking for crypt in -lcrypt... yes
checking for pow in -lm... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
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
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking net/if.h usability... yes
checking net/if.h presence... yes
checking for net/if.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/fcntl.h usability... yes
checking sys/fcntl.h presence... yes
checking for sys/fcntl.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/file.h usability... yes
checking sys/file.h presence... yes
checking for sys/file.h... yes
checking sys/syslimits.h usability... no
checking sys/syslimits.h presence... no
checking for sys/syslimits.h... no
checking netinet/in_systm.h usability... yes
checking netinet/in_systm.h presence... yes
checking for netinet/in_systm.h... yes
checking sys/in_systm.h usability... no
checking sys/in_systm.h presence... no
checking for sys/in_systm.h... no
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking sys/un.h usability... yes
checking sys/un.h presence... yes
checking for sys/un.h... yes
checking sys/filio.h usability... no
checking sys/filio.h presence... no
checking for sys/filio.h... no
checking regex.h usability... yes
checking regex.h presence... yes
checking for regex.h... yes
checking resolv.h usability... yes
checking resolv.h presence... yes
checking for resolv.h... yes
checking arpa/nameser.h usability... yes
checking arpa/nameser.h presence... yes
checking for arpa/nameser.h... yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking sys/ndir.h usability... no
checking sys/ndir.h presence... no
checking for sys/ndir.h... no
checking sys/dir.h usability... yes
checking sys/dir.h presence... yes
checking for sys/dir.h... yes
checking ndir.h usability... no
checking ndir.h presence... no
checking for ndir.h... no
checking for stpcpy in string.h... yes
checking for getpgid in unistd

---

### Post by oldos2er on 2011-12-29
Moved to Other OS/Distro Talk.

---

