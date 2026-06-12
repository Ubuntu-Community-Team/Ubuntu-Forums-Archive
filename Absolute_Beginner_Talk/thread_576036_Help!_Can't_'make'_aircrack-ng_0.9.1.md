---
title: "Help! Can't 'make' aircrack-ng 0.9.1"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Neodudeman on 2007-10-14
I'm trying to install aircrack-ng version 0.9.1 and am having trouble!

I'm familiar with using the package manager, and would have used it in this case, but the package they have is only version 0.6.2, which is missing a few key functions of the current aircrack-ng release.

I've been searching for several hours, and I can't find an answer to my problem! :(

Using the installation instructions on the official aircrack-ng website at [http://www.aircrack-ng.org/doku.php?id=install_aircrack](http://www.aircrack-ng.org/doku.php?id=install_aircrack)
```

wget http://download.aircrack-ng.org/aircrack-ng-0.9.1.tar.gz
tar -zxvf aircrack-ng-0.9.1.tar.gz
cd aircrack-ng-0.9.1
make
make install

```

I got this malfunctioning output error:
```

root@Breeze:~/aircrack-ng-0.9.1# make
gcc -g -W -Wall -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=`./evalrev` src/aircrack-ng.c src/crypto.c src/sha1-mmx.S src/common.c src/aircrack-ptw-lib.c -o aircrack-ng -lpthread
src/aircrack-ng.c:26:23: error: sys/types.h: No such file or directory
src/aircrack-ng.c:27:25: error: sys/termios.h: No such file or directory
src/aircrack-ng.c:28:23: error: sys/ioctl.h: No such file or directory
src/aircrack-ng.c:29:22: error: sys/wait.h: No such file or directory
src/aircrack-ng.c:30:22: error: sys/stat.h: No such file or directory
src/aircrack-ng.c:31:22: error: sys/time.h: No such file or directory
src/aircrack-ng.c:32:24: error: netinet/in.h: No such file or directory
src/aircrack-ng.c:33:21: error: pthread.h: No such file or directory
src/aircrack-ng.c:34:20: error: unistd.h: No such file or directory
src/aircrack-ng.c:35:20: error: signal.h: No such file or directory
src/aircrack-ng.c:36:20: error: string.h: No such file or directory
src/aircrack-ng.c:37:20: error: stdlib.h: No such file or directory
src/aircrack-ng.c:38:19: error: stdio.h: No such file or directory
src/aircrack-ng.c:39:19: error: fcntl.h: No such file or directory
src/aircrack-ng.c:40:19: error: errno.h: No such file or directory
src/aircrack-ng.c:41:18: error: time.h: No such file or directory
src/aircrack-ng.c:42:20: error: getopt.h: No such file or directory
src/aircrack-ng.c:43:19: error: ctype.h: No such file or directory
src/aircrack-ng.c:44:17: error: err.h: No such file or directory
In file included from src/aircrack-ng.c:49:
src/uniqueiv.c: In function ‘uniqueiv_init’:
src/uniqueiv.c:32: warning: implicit declaration of function ‘malloc’
src/uniqueiv.c:32: warning: incompatible implicit declaration of built-in function ‘malloc’
src/uniqueiv.c:34: error: ‘NULL’ undeclared (first use in this function)
src/uniqueiv.c:34: error: (Each undeclared identifier is reported only once
src/uniqueiv.c:34: error: for each function it appears in.)
src/uniqueiv.c: In function ‘uniqueiv_mark’:
src/uniqueiv.c:53: error: ‘NULL’ undeclared (first use in this function)
src/uniqueiv.c:66: warning: incompatible implicit declaration of built-in function ‘malloc’
src/uniqueiv.c:91: warning: incompatible implicit declaration of built-in function ‘malloc’
src/uniqueiv.c: In function ‘uniqueiv_check’:
src/uniqueiv.c:120: error: ‘NULL’ undeclared (first use in this function)
src/uniqueiv.c: In function ‘uniqueiv_wipe’:
src/uniqueiv.c:158: error: ‘NULL’ undeclared (first use in this function)
src/uniqueiv.c:174: warning: implicit declaration of function ‘free’
In file included from src/aircrack-ng.c:50:
src/aircrack-ptw-lib.h:6:20: error: stdint.h: No such file or directory
In file included from src/aircrack-ng.c:50:
src/aircrack-ptw-lib.h: At top level:
src/aircrack-ptw-lib.h:32: error: expected specifier-qualifier-list before ‘uint8_t’
src/aircrack-ptw-lib.h:38: error: expected specifier-qualifier-list before ‘uint8_t’
src/aircrack-ptw-lib.h:49: error: expected specifier-qualifier-list before ‘uint8_t’
src/aircrack-ptw-lib.h:60: error: expected declaration specifiers or ‘...’ before ‘uint8_t’
src/aircrack-ptw-lib.h:60: error: expected declaration specifiers or ‘...’ before ‘uint8_t’
src/aircrack-ptw-lib.h:61: error: expected declaration specifiers or ‘...’ before ‘uint8_t’
In file included from src/aircrack-ng.c:51:
src/aircrack-ng.h:105: error: expected specifier-qualifier-list before ‘FILE’
src/aircrack-ng.c:70: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘mx_ivb’
src/aircrack-ng.c:71: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘mx_apl’
src/aircrack-ng.c:72: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘mx_eof’
src/aircrack-ng.c:73: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cv_eof’
src/aircrack-ng.c: In function ‘eof_wait’:
src/aircrack-ng.c:172: warning: implicit declaration of function ‘pthread_mutex_lock’
src/aircrack-ng.c:172: error: ‘mx_eof’ undeclared (first use in this function)
src/aircrack-ng.c:174: warning: implicit declaration of function ‘pthread_cond_broadcast’
src/aircrack-ng.c:174: error: ‘cv_eof’ undeclared (first use in this function)
src/aircrack-ng.c:175: warning: implicit declaration of function ‘pthread_mutex_unlock’
src/aircrack-ng.c:178: warning: implicit declaration of function ‘usleep’
src/aircrack-ng.c: In function ‘atomic_read’:
src/aircrack-ng.c:187: error: ‘NULL’ undeclared (first use in this function)
src/aircrack-ng.c:189: warning: incompatible implicit declaration of built-in function ‘malloc’
src/aircrack-ng.c:203: warning: implicit declaration of function ‘memcpy’
src/aircrack-ng.c:203: warning: incompatible implicit declaration of built-in function ‘memcpy’
src/aircrack-ng.c:211: warning: incompatible implicit declaration of built-in function ‘memcpy’
src/aircrack-ng.c:217: warning: implicit declaration of function ‘read’
src/aircrack-ng.c:226: warning: incompatible implicit declaration of built-in function ‘memcpy’
src/aircrack-ng.c: In function ‘known_clear’:
src/aircrack-ng.c:272: warning: implicit declaration of function ‘htons’
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Lines Omitted to fit
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
src/aircrack-ptw-lib.c:416: error: too many arguments to function ‘doComputation’
src/aircrack-ptw-lib.c:422: warning: passing argument 3 of ‘doComputation’ makes pointer from integer without a cast
src/aircrack-ptw-lib.c:422: warning: passing argument 4 of ‘doComputation’ from incompatible pointer type
src/aircrack-ptw-lib.c:422: warning: passing argument 5 of ‘doComputation’ from incompatible pointer type
src/aircrack-ptw-lib.c:422: warning: passing argument 6 of ‘doComputation’ makes integer from pointer without a cast
src/aircrack-ptw-lib.c:422: error: too many arguments to function ‘doComputation’
src/aircrack-ptw-lib.c: At top level:
src/aircrack-ptw-lib.c:435: error: expected declaration specifiers or ‘...’ before ‘uint8_t’
src/aircrack-ptw-lib.c:435: error: expected declaration specifiers or ‘...’ before ‘uint8_t’
src/aircrack-ptw-lib.c: In function ‘PTW_addsession’:
src/aircrack-ptw-lib.c:439: error: ‘uint8_t’ undeclared (first use in this function)
src/aircrack-ptw-lib.c:439: error: expected ‘;’ before ‘buf’
src/aircrack-ptw-lib.c:441: error: ‘iv’ undeclared (first use in this function)
src/aircrack-ptw-lib.c:444: error: ‘PTW_attackstate’ has no member named ‘seen_iv’
src/aircrack-ptw-lib.c:446: error: ‘PTW_attackstate’ has no member named ‘seen_iv’
src/aircrack-ptw-lib.c:447: warning: implicit declaration of function ‘guesskeybytes’
src/aircrack-ptw-lib.c:447: error: ‘keystream’ undeclared (first use in this function)
src/aircrack-ptw-lib.c:447: error: ‘buf’ undeclared (first use in this function)
src/aircrack-ptw-lib.c:449: error: ‘PTW_attackstate’ has no member named ‘table’
src/aircrack-ptw-lib.c:451: error: ‘PTW_attackstate’ has no member named ‘sessions_collected’
src/aircrack-ptw-lib.c:452: warning: incompatible implicit declaration of built-in function ‘memcpy’
src/aircrack-ptw-lib.c:452: error: ‘PTW_attackstate’ has no member named ‘sessions’
src/aircrack-ptw-lib.c:452: error: ‘PTW_attackstate’ has no member named ‘sessions_collected’
src/aircrack-ptw-lib.c:453: error: ‘PTW_attackstate’ has no member named ‘sessions’
src/aircrack-ptw-lib.c:453: error: ‘PTW_attackstate’ has no member named ‘sessions_collected’
src/aircrack-ptw-lib.c:454: error: ‘PTW_attackstate’ has no member named ‘sessions_collected’
src/aircrack-ptw-lib.c: In function ‘PTW_newattackstate’:
src/aircrack-ptw-lib.c:467: error: ‘NULL’ undeclared (first use in this function)
src/aircrack-ptw-lib.c:468: warning: implicit declaration of function ‘malloc’
src/aircrack-ptw-lib.c:468: warning: incompatible implicit declaration of built-in function ‘malloc’
src/aircrack-ptw-lib.c:472: warning: implicit declaration of function ‘bzero’
src/aircrack-ptw-lib.c:472: warning: incompatible implicit declaration of built-in function ‘bzero’
src/aircrack-ptw-lib.c:475: error: ‘PTW_attackstate’ has no member named ‘table’
src/aircrack-ptw-lib.c: In function ‘PTW_freeattackstate’:
src/aircrack-ptw-lib.c:485: warning: implicit declaration of function ‘free’
make: *** [aircrack-ng] Error 1

```

Can someone Please help me out?? I'm Dieing here!! :(:(

---

### Post by Neodudeman on 2007-10-14
Good News! I installed it!

I forgot to get the sources and headers for the kernel. Whoops. =/

Here's the code that did it:

```

sudo apt-get install build-essential

```

---

