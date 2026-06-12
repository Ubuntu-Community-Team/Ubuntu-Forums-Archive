---
title: "Wine 0.9.12 installation problem"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by Iesos on 2006-04-23
Hi, I reasently got a new system and I'm trying to get StarCraft and Diablo 2 working. I got StarCraft working with wine --version = Wine 20050725, on a 2.6.12-10-amd64-k8 kernel. (By using chroot). When I tried Diablo 2 it complained over NoCD, so I mailed the guys at winehq and they recomended that I upgraded to wine 0.9.12 since my version got cd-protection problems. When I run ./tools/wineinstall in the "source-folder" (or what one should call it), I get an error:

```

In file included from signal_i386.c:57:
ntdll_misc.h:54: error: syntax error before 'server_start_time'
ntdll_misc.h:54: warning: type defaults to 'int' in declaration of 'server_start_time'
ntdll_misc.h:54: warning: data definition has no type or storage class
signal_i386.c:108:4: error: #error The sigaction syscall is part of the Linux i386 ABI, but your headers does not define it. Please raise a bug with your distribution.
signal_i386.c: In function 'wine_sigaction':
signal_i386.c:123: error: '__NR_sigaction' undeclared (first use in this function)
signal_i386.c:125: error: 'errno' undeclared (first use in this function)
signal_i386.c: At top level:
signal_i386.c:132: warning: 'struct sigaltstack' declared inside parameter list
signal_i386.c:132: warning: its scope is only this definition or declaration, which is probably not what you want
signal_i386.c: In function 'wine_sigaltstack':
signal_i386.c:140: error: 'SYS_sigaltstack' undeclared (first use in this function)
signal_i386.c:142: error: 'errno' undeclared (first use in this function)
In file included from signal_i386.c:425:
../../include/wine/exception.h:24:20: error: setjmp.h: No such file or directoryIn file included from signal_i386.c:425:
../../include/wine/exception.h: At top level:
../../include/wine/exception.h:146: error: syntax error before 'sigjmp_buf'
../../include/wine/exception.h:146: warning: no semicolon at end of struct or union
../../include/wine/exception.h:150: error: syntax error before '}' token
../../include/wine/exception.h:150: warning: type defaults to 'int' in declaration of '__WINE_FRAME'
../../include/wine/exception.h:150: warning: data definition has no type or storage class
signal_i386.c: In function 'save_context':
signal_i386.c:731: warning: implicit declaration of function 'memset'
signal_i386.c:731: warning: incompatible implicit declaration of built-in function 'memset'
signal_i386.c: In function 'int_handler':
signal_i386.c:1318: error: 'SIGINT' undeclared (first use in this function)
signal_i386.c: In function 'get_signal_stack_total_size':
signal_i386.c:1380: error: 'MINSIGSTKSZ' undeclared (first use in this function)signal_i386.c: In function 'set_handler':
signal_i386.c:1397: error: storage size of 'sig_act' isn't known
signal_i386.c:1404: error: 'SA_RESTART' undeclared (first use in this function)
signal_i386.c:1405: error: 'SIGINT' undeclared (first use in this function)
signal_i386.c:1406: error: 'SIGUSR1' undeclared (first use in this function)
signal_i386.c:1407: error: 'SIGUSR2' undeclared (first use in this function)
signal_i386.c:1414: warning: implicit declaration of function 'sigemptyset'
signal_i386.c:1415: warning: implicit declaration of function 'sigaddset'
signal_i386.c:1430: warning: implicit declaration of function 'sigaction'
signal_i386.c:1397: warning: unused variable 'sig_act'
signal_i386.c: In function 'SIGNAL_Init':
signal_i386.c:1454: error: storage size of 'ss' isn't known
signal_i386.c:1458: warning: implicit declaration of function 'sigaltstack'
signal_i386.c:1467: error: 'SIGINT' undeclared (first use in this function)
signal_i386.c:1468: error: 'SIGFPE' undeclared (first use in this function)
signal_i386.c:1469: error: 'SIGSEGV' undeclared (first use in this function)
signal_i386.c:1470: error: 'SIGILL' undeclared (first use in this function)
signal_i386.c:1471: error: 'SIGABRT' undeclared (first use in this function)
signal_i386.c:1472: error: 'SIGTERM' undeclared (first use in this function)
signal_i386.c:1473: error: 'SIGUSR1' undeclared (first use in this function)
signal_i386.c:1488: warning: implicit declaration of function 'perror'
signal_i386.c:1454: warning: unused variable 'ss'
make[2]: *** [signal_i386.o] Error 1
make[2]: Leaving directory `/home/johan/Accesories/Wine/wine-0.9.12/dlls/ntdll'
make[1]: *** [ntdll] Error 2
make[1]: Leaving directory `/home/johan/Accesories/Wine/wine-0.9.12/dlls'
make: *** [dlls] Error 2

Compilation failed, aborting install.

```

Do anyone know what the problem is and how to solve it? (I get the same error in my chroot enviorment as in my normal terminal.)

---

### Post by benvdh on 2006-04-23
Hey,

You could try this how-to on how-to upgrade to the latest wine release :

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Has always worked great for me.

Regards,

Ben

---

### Post by Iesos on 2006-04-23
I have tried that, but the latest release for deb packages are 0.9.10, I need a later version.

---

### Post by Bagnaj97 on 2006-04-23
These steps worked for me on Dapper Beta i386 version:

(1). Install build-essential using synaptic or the command line if you prefer.

(2). Install all the packages listed under the Ubuntu Dapper section and the Programs section here: [http://wiki.winehq.org/Recommended_Packages](http://wiki.winehq.org/Recommended_Packages)

(3). download the wine 0.9.12 tarball to your desktop and then do:
```
tar -xjf wine-0.9.12.tar.bz2
cd wine-0.9.12
./configure && make depend && make
sudo make install
```

Run winecfg to configure it. As long as the windows version is set to 2000 or XP Diablo 2 should work perfectly without the nocd (unless you have a pirate copy :mad: ). I'm using it and it runs fine on battle net and single player.

---

### Post by Kimm on 2006-04-23
to get the required packages to build wine, just do this in terminal (after adding wine repositories):

sudo apt-get build-dep wine

---

### Post by hotrodg on 2006-04-27
I have a similar problem.  I am trying to build wine 0.9.12 for an amd_64 machine.  The compile fails.  The screen output from make is:

signal_i386.c:108:4: error: #error The sigaction syscall is part of the Linux i386 ABI, but your headers does not define it. Please raise a bug with your distribution.
signal_i386.c: In function ‘wine_sigaction’:
signal_i386.c:123: error: ‘__NR_sigaction’ undeclared (first use in this function)
signal_i386.c:123: error: (Each undeclared identifier is reported only once
signal_i386.c:123: error: for each function it appears in.)
make[2]: *** [signal_i386.o] Error 1
make[2]: Leaving directory `/home/hotrodg/Desktop/wine-0.9.12/dlls/ntdll'
make[1]: *** [ntdll] Error 2
make[1]: Leaving directory `/home/hotrodg/Desktop/wine-0.9.12/dlls'
make: *** [dlls] Error 2

     The problems looks simple enough -- a definition is missing from a header file. I have been compiling against linux-headers-amd64-generic version 2.6.12.16.1.  Am I using the wrong headers?  If the headers are the right ones, the appropriate action is to do as the error message suggests and report a bug.  Has anyone had this compile succeed?

---

### Post by YokoZar on 2006-04-29
[QUOTE=Iesos]I have tried that, but the latest release for deb packages are 0.9.10, I need a later version.[/QUOTE]
Zuh?  The apt repository has 0.9.12.

---

