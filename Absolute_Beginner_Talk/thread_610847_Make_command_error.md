---
title: "Make command error"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by abhiroopb on 2007-11-12
I am having problems with the "make" command.

I tried to install gnuchess and after doing ./configure when I do make I get the following:

```

Making all in src
make[1]: Entering directory `/home/abhiroop/Desktop/gnuchess-5.07/src'
make  all-am
make[2]: Entering directory `/home/abhiroop/Desktop/gnuchess-5.07/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.    -pthread -g -O2 -MT input.o -MD -MP -MF ".deps/input.Tpo" \
          -c -o input.o `test -f 'input.c' || echo './'`input.c; \
        then mv -f ".deps/input.Tpo" ".deps/input.Po"; \
        else rm -f ".deps/input.Tpo"; exit 1; \
        fi
input.c:95: error: static declaration of ‘input_thread’ follows non-static declaration
common.h:719: error: previous declaration of ‘input_thread’ was here
make[2]: *** [input.o] Error 1
make[2]: Leaving directory `/home/abhiroop/Desktop/gnuchess-5.07/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/abhiroop/Desktop/gnuchess-5.07/src'
make: *** [all-recursive] Error 1

```

When trying to install sjeng I get:

```

make  all-recursive
make[1]: Entering directory `/home/abhiroop/Desktop/Sjeng-Free-11.2'
Making all in books
make[2]: Entering directory `/home/abhiroop/Desktop/Sjeng-Free-11.2/books'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/abhiroop/Desktop/Sjeng-Free-11.2/books'
Making all in tests
make[2]: Entering directory `/home/abhiroop/Desktop/Sjeng-Free-11.2/tests'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/abhiroop/Desktop/Sjeng-Free-11.2/tests'
make[2]: Entering directory `/home/abhiroop/Desktop/Sjeng-Free-11.2'
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c attacks.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c crazy.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c epd.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c learn.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c partner.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c seval.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c ttable.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c book.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c ecache.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c eval.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c moves.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c search.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c sjeng.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c utils.c
gcc -DHAVE_CONFIG_H -I. -I. -I.     -g -O2 -c newbook.c
newbook.c:27:18: error: gdbm.h: No such file or directory
newbook.c:35:2: error: #error You need the GNU DBM library (GDBM). Go to ftp.gnu.org
newbook.c:114: error: expected ‘)’ before ‘binbook’
newbook.c:158: error: expected declaration specifiers or ‘...’ before ‘GDBM_FILE’
newbook.c: In function ‘replay_game’:
newbook.c:320: error: ‘binbook’ undeclared (first use in this function)
newbook.c:320: error: (Each undeclared identifier is reported only once
newbook.c:320: error: for each function it appears in.)
newbook.c: At top level:
newbook.c:326: error: expected ‘)’ before ‘binbook’
newbook.c: In function ‘build_book’:
newbook.c:377: error: ‘GDBM_FILE’ undeclared (first use in this function)
newbook.c:377: error: expected ‘;’ before ‘binbook’
newbook.c:393: error: ‘binbook’ undeclared (first use in this function)
newbook.c:393: error: ‘GDBM_NEWDB’ undeclared (first use in this function)
newbook.c:393: error: ‘GDBM_FAST’ undeclared (first use in this function)
newbook.c:435: error: too many arguments to function ‘replay_game’
newbook.c: In function ‘choose_binary_book_move’:
newbook.c:453: error: ‘GDBM_FILE’ undeclared (first use in this function)
newbook.c:453: error: expected ‘;’ before ‘binbook’
newbook.c:456: error: ‘datum’ undeclared (first use in this function)
newbook.c:456: error: expected ‘;’ before ‘index’
newbook.c:457: error: expected ‘;’ before ‘data’
newbook.c:469: error: ‘binbook’ undeclared (first use in this function)
newbook.c:469: error: ‘GDBM_READER’ undeclared (first use in this function)
newbook.c:514: error: request for member ‘dptr’ in something not a structure or union
newbook.c:515: error: request for member ‘dsize’ in something not a structure or union
newbook.c:517: error: ‘data’ undeclared (first use in this function)
newbook.c: In function ‘book_learning’:
newbook.c:596: error: ‘GDBM_FILE’ undeclared (first use in this function)
newbook.c:596: error: expected ‘;’ before ‘binbook’
newbook.c:599: error: ‘datum’ undeclared (first use in this function)
newbook.c:599: error: expected ‘;’ before ‘index’
newbook.c:600: error: expected ‘;’ before ‘data’
newbook.c:610: error: ‘binbook’ undeclared (first use in this function)
newbook.c:610: error: ‘GDBM_WRITER’ undeclared (first use in this function)
newbook.c:635: error: request for member ‘dptr’ in something not a structure or union
newbook.c:636: error: request for member ‘dsize’ in something not a structure or union
newbook.c:638: error: ‘data’ undeclared (first use in this function)
newbook.c:686: error: ‘GDBM_REPLACE’ undeclared (first use in this function)
make[2]: *** [newbook.o] Error 1
make[2]: Leaving directory `/home/abhiroop/Desktop/Sjeng-Free-11.2'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/abhiroop/Desktop/Sjeng-Free-11.2'
make: *** [all-recursive-am] Error 2

```

Also when trying to install the pwc module I get further make errors.

I assume this is a general problem I am having, help in this matter would be appreciated.

It is unfortunate because I have never had any problems with compiling from source before. It is only after upgrading to Gutsy that I have had this problem.

Also I'm not too familiar with the commands, I only know that I have to do ./configure and then make, and then make install. Other than that I am quite clueless. In the past this has usually worked for me.

---

### Post by Paul820 on 2007-11-12
Do you have build-essential installed?
> sudo apt-get install build-essential

I have just had a look in synaptic and these programs you are tying to build are in there. Same versions, just download them.

---

### Post by llamakc on 2007-11-12
That version of GNUChess is in the repositories. Install it via Synaptic or the command line.

```

sudo apt-get install gnuchess

```

As is version 11.2 of sjeng.

```

sudo apt-get install sjeng

```

Or do them both at the same time:

```

sudo apt-get install gnuchess sjeng

```

Why are you compiling software when the same versions are already compiled and available in the repositories?

You should normally try searching for the package in Synaptic first. Here's how you would do it in the command line:

```

apt-cache search sjeng

sjeng - A chess program that plays many variants

```

You can use "apt-cache show NAMEOFPACKAGE" to get details about it.

---

### Post by abhiroopb on 2007-11-12
Thanks a lot for the help.

when I go to install build-essential I get:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

So, I am guessing it is installed, and if I recall this is what was suggested when I was trying to compile the pwc module for my webcam as well.

Thanks a lot for the synaptic install guide though worked like a charm. Unfortunately I was looking in the "Add/Remove" section and there was nothing there which was a bit odd!

Still have problems with compiling from source though.

About the pwc module errors:

I am running Gutsy (kernel: 2.6.22-14-generic).

I have a logitech quickcam 3000 pro.

While I had fiesty I tried getting my cam to work using the pwc driver and I remember it working briefly. But after that I gave up as skype did not even have a video option. Now that skype has that option I want to get my cam working again.

So I went to the pwc site and downloaded the latest one: pwc-10.0.12-rc1.

I followed the instructions, unpacked the tarball and did make and this is what I get:
```

make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/abhiroop/Desktop/pwc-10.0.12-rc1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.o
In file included from /home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:69:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc.h:28:26: error: linux/config.h: No such file or directory
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:166: error: variable &#8216;pwc_template&#8217; has initializer but incomplete type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:167: error: unknown field &#8216;owner&#8217; specified in initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:167: warning: excess elements in struct initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:167: warning: (near initialization for &#8216;pwc_template&#8217;)
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:168: error: unknown field &#8216;name&#8217; specified in initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:168: warning: excess elements in struct initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:168: warning: (near initialization for &#8216;pwc_template&#8217;)
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:169: error: unknown field &#8216;type&#8217; specified in initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:169: warning: excess elements in struct initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:169: warning: (near initialization for &#8216;pwc_template&#8217;)
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:170: error: unknown field &#8216;hardware&#8217; specified in initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:170: warning: excess elements in struct initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:170: warning: (near initialization for &#8216;pwc_template&#8217;)
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:171: error: unknown field &#8216;release&#8217; specified in initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:171: error: &#8216;video_device_release&#8217; undeclared here (not in a function)
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:171: warning: excess elements in struct initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:171: warning: (near initialization for &#8216;pwc_template&#8217;)
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:172: error: unknown field &#8216;fops&#8217; specified in initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:172: warning: excess elements in struct initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:172: warning: (near initialization for &#8216;pwc_template&#8217;)
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:173: error: unknown field &#8216;minor&#8217; specified in initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:173: warning: excess elements in struct initializer
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:173: warning: (near initialization for &#8216;pwc_template&#8217;)
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_isoc_init&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:921: warning: assignment from incompatible pointer type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;cd_to_pwc&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1019: warning: implicit declaration of function &#8216;to_video_device&#8217;
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1019: warning: initialization makes pointer from integer without a cast
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1020: warning: implicit declaration of function &#8216;video_get_drvdata&#8217;
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1020: warning: return makes pointer from integer without a cast
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_create_sysfs_files&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1062: warning: initialization makes pointer from integer without a cast
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1064: warning: implicit declaration of function &#8216;video_device_create_file&#8217;
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_remove_sysfs_files&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1070: warning: initialization makes pointer from integer without a cast
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1072: warning: implicit declaration of function &#8216;video_device_remove_file&#8217;
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_video_open&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1112: warning: implicit declaration of function &#8216;video_devdata&#8217;
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1112: warning: initialization makes pointer from integer without a cast
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1117: error: dereferencing pointer to incomplete type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_video_close&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1231: error: dereferencing pointer to incomplete type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_video_read&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1292: error: dereferencing pointer to incomplete type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_video_poll&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1359: error: dereferencing pointer to incomplete type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_video_ioctl&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1375: warning: implicit declaration of function &#8216;video_usercopy&#8217;
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;pwc_video_mmap&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1388: error: dereferencing pointer to incomplete type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;usb_pwc_probe&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1722: warning: implicit declaration of function &#8216;video_device_alloc&#8217;
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1722: warning: assignment makes pointer from integer without a cast
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1729: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_device&#8217; 
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1729: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_device&#8217; 
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1729: error: invalid application of &#8216;sizeof&#8217; to incomplete type &#8216;struct video_device&#8217; 
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1730: error: dereferencing pointer to incomplete type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1731: error: dereferencing pointer to incomplete type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1732: error: dereferencing pointer to incomplete type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1733: warning: implicit declaration of function &#8216;video_set_drvdata&#8217;
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1756: error: dereferencing pointer to incomplete type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1757: warning: implicit declaration of function &#8216;video_register_device&#8217;
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1757: error: &#8216;VFL_TYPE_GRABBER&#8217; undeclared (first use in this function)
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1757: error: (Each undeclared identifier is reported only once
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1757: error: for each function it appears in.)
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1760: warning: implicit declaration of function &#8216;video_device_release&#8217;
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1765: error: dereferencing pointer to incomplete type
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c: In function &#8216;usb_pwc_disconnect&#8217;:
/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.c:1819: warning: implicit declaration of function &#8216;video_unregister_device&#8217;
make[2]: *** [/home/abhiroop/Desktop/pwc-10.0.12-rc1/pwc-if.o] Error 1
make[1]: *** [_module_/home/abhiroop/Desktop/pwc-10.0.12-rc1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2

```

---

### Post by Paul820 on 2007-11-12
Well after some digging around on google i found that linux/config.h is deprecated. This is what is supposed to be in the file that you need

```
#ifndef _LINUX_CONFIG_H
#define _LINUX_CONFIG_H
/* This file is no longer in use and kept only for backward compatibility.
 * autoconf.h is now included via -imacros on the commandline
 */
#include <linux/autoconf.h>

#endif
```

Doing a search on google for ** linux/config.h** will find you a bit more help.

---

### Post by abhiroopb on 2007-11-12
Thanks for that...

This seems to be what the problem is but I'm afraid I still don't understand what I have to do to sort it out.

I tried the method suggested here: [http://www.linuxquestions.org/questions/linux-kernel-70/removal-of-includelinuxconfig.h-file-in-2.6.19-kernel-506363/](http://www.linuxquestions.org/questions/linux-kernel-70/removal-of-includelinuxconfig.h-file-in-2.6.19-kernel-506363/)

touch /usr/src/linux/include/linux/config.h

tried make on the pwc module and same problem again.

Thanks for the help, I'm trying to understand all of this but there is a lot of technical jargon unfortunately.

---

### Post by abhiroopb on 2007-11-12
for one thing where is the file located?

---

### Post by Paul820 on 2007-11-12
I don't know if you are on gutsy, but the correct source for your webcam is in the repos, found that out by reading this saying the code got accepted. Read here: [https://lists.ubuntu.com/archives/gutsy-changes/2007-October/009650.html]("https://lists.ubuntu.com/archives/gutsy-changes/2007-October/009650.html")
So far so good, :) Now do a search in synaptic for **pwc-source** and download it. I don't know where it throws all the source but the package gets put in **/usr/source/linux-headers-2.6.22-14-generic/include** or whatever your kernel version is. There will be a compressed file there called pwc-source.tar.bz2. Right click on it and select copy then right click on your desktop and paste. Extract it and build it with make. The build works fine, i tested it on my machine but i never installed it as obviously i don't need it. :) Anyway, let us know if it works for you.

EDIT: Heres the top of the changelog where the ubuntu developers have fixed the part you were having trouble with
```

pwc (10.0.12-rc1+final-2ubuntu1) gutsy; urgency=low

  * Removed `struct pt_regs *regs' from pwc_isoc_handler's signature
    in `pwc-if.c' (throws a warning about an incompatible pointer type).
  * Removed `#include <linux/config.h>' from `pwc.h' (fixes a
    compilation error when module-assistant is invoked on the module).
    (LP: #46956)
  * Modify Maintainer value to match the DebianMaintainerField
    specification.
  * Do not ignore failures on clean.

 -- Philipp Kern <pkern@debian.org>  Mon, 08 Oct 2007 22:38:31 +0200
```

---

### Post by abhiroopb on 2007-11-12
amazing that worked great thanks (unfortunately my camera is still not working - but I guess thats for another thread)!

still anything I can do to solve the make command problem?

---

### Post by Paul820 on 2007-11-12
There is another program in synaptic called **setpwc** to configure the settings for the webcam.

---

### Post by Paul820 on 2007-11-12
> **abhiroopb said:**
> amazing that worked great thanks (unfortunately my camera is still not working - but I guess thats for another thread)!

still anything I can do to solve the make command problem?

I don't understand :confused: That what i posted above sorts out the make command problem.

---

### Post by abhiroopb on 2007-11-12
sorry what i meant was that by using the pwc-source file in synaptic I can compile the pwc driver without a problem but I guess this is beacause the make file has been changed to work with gutsy.

if i download some other program will i be able to compile it? or will it show up the error again.

I have setpwc installed and a gui for it, unfortunately it just says device not found...

---

