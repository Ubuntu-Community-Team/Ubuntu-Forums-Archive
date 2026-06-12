---
title: "kernel compliation - make defconfig"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by rstevens on 2008-04-20
richard@richard-desktop:~/linux/linux-2.6.25$ pwd
/home/richard/linux/linux-2.6.25

richard@richard-desktop:~/linux/linux-2.6.25$ ls
arch     CREDITS        drivers  init    kernel       Makefile  README          scripts   usr
block    crypto         fs       ipc     lib          mm        REPORTING-BUGS  security  virt
COPYING  Documentation  include  Kbuild  MAINTAINERS  net       samples         sound

richard@richard-desktop:~/linux/linux-2.6.25$ make defconfig
  HOSTCC  scripts/kconfig/zconf.tab.o
In file included from scripts/kconfig/zconf.tab.c:2473:
scripts/kconfig/lex.zconf.c: In function ‘yy_get_next_buffer’:
scripts/kconfig/lex.zconf.c:1537: error: ‘EINTR’ undeclared (first use in this function)
scripts/kconfig/lex.zconf.c:1537: error: (Each undeclared identifier is reported only once
scripts/kconfig/lex.zconf.c:1537: error: for each function it appears in.)
In file included from scripts/kconfig/zconf.tab.c:2475:
scripts/kconfig/confdata.c: In function ‘conf_split_config’:
scripts/kconfig/confdata.c:636: error: ‘ENOENT’ undeclared (first use in this function)
make[1]: *** [scripts/kconfig/zconf.tab.o] Error 1
make: *** [defconfig] Error 2

richard@richard-desktop:~/linux/linux-2.6.25$ 

Any recommendations?

---

