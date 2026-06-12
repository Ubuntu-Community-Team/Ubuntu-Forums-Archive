---
title: "Posible to Develop iPhone Apps On Ubuntu?"
date: 2009-02-14
forum: Apple Hardware Users
---

### Post by MrFairladyz on 2009-02-14
Hi, i have Intrepid installed and want to know if it would be possible to run the iPhone SDK on ubuntu?

---

### Post by arepaking on 2009-09-27
I am wondering the same thing.. Any comments??

---

### Post by WindPower on 2009-09-28
I doubt it. You can't run the latest iTunes version, let alone mount an iPod Touch/iPhone running the version 3.x of the iPhone OS without jailbreaking it (and even then, most of the stuff is encrypted), so I doubt you could do any sort of iPhone development on Ubuntu easily.

---

### Post by the_squircle on 2009-09-29
> **MrFairladyz said:**
> Hi, i have Intrepid installed and want to know if it would be possible to run the iPhone SDK on ubuntu?

[SIZE="1"]The (unfortunate) answer is no.

For many (obvious) reasons, it is extremely hard (if not impossible) to run the iPhone SDK on Linux. You'd have to have the source of XCode to compile for Linux, and re-write all the libraries (cocoa, carbon) to be used under Linux. Apple just wants your money; you can only develop on a Mac. :([/size]

EDIT:**Maybe**, you may be able to. See post #12.

---

### Post by rjcalifornia on 2009-09-29
Sorry, NO....

---

### Post by UbFreak on 2009-10-04
There are some open source tools, But if you are thinking about objective-c, good luck.

---

### Post by NoBugs! on 2009-10-06
I would imagine it would be pretty easy to make a [web app]("http://www.apple.com/webapps/") for your iPhone/ipod touch. It looks like just javascript, html etc.
(Example code can be found [here]("http://developer.apple.com/safari/library/navigation/SampleCode.html"))

These apps are also available to use inside your browser, so many other mobile devices should also be able to use them (Maemo, Android, Eeepc, etc...)

---

### Post by alexmurray on 2009-10-06
@felixmartyr: what's your point? The iPAQ is pretty old now and Linux runs on many more recent devices (ie. the Nokia N900 just to name one). This is irrelevant to developing iPhone Apps on Ubuntu which I would say is next to impossible.

---

### Post by rafaelous on 2009-10-07
Not really gonna be easy. The best way to develop iphone apps is with xcode on a mac. That way you can debug etc. nicely. If you're desperate not to use a mac, there's the windows toolchain which will allow you to compile it on Windows, however I'm not aware of something similar for Linux.

---

### Post by luigi.viggiano on 2009-10-08
I saw some videos on youtube about developing "native" iphone apps using flash. But I don't know if flash sdk is available on linux.

---

### Post by ALLurGroceries on 2009-10-09
It is indeed possible.

[http://code.google.com/p/iphone-dev/wiki/Building]("http://code.google.com/p/iphone-dev/wiki/Building")

"iPhone Open Application Development" by O'Reilly:
[http://oreilly.com/catalog/9780596518561]("http://oreilly.com/catalog/9780596518561")

> Platforms currently supported by the tool chain are:

Mac OS X 10.4 Intel or PPC

Mac OS X 10.5 Intel

Ubuntu Feisty Fawn, Intel

Ubuntu Gusty Gibbon, Intel

Fedora Core, Intel

Gentoo Linux 2007.0, x86_64

Debian 2.6.18

CentOS 4

---

### Post by alexmurray on 2009-10-10
Wow, there you go. I retract my previous statement entirely. That's pretty awesome.

---

### Post by irohaphoto on 2009-10-10
Somehow I doubted it would be possible. It would be like zipping yourself up in a straightjacket because the code is all closed they like microsoft want your money....

---

### Post by uplink3r on 2009-12-27
ok, i tried to follow the instructions on [http://code.google.com/p/iphone-dev/wiki/Building](http://code.google.com/p/iphone-dev/wiki/Building)

first i got an error with
```
svn co http://llvm.org/svn/llvm-project/llvm/trunk llvm-svn -r 42498

```
so i did just ```
svn co http://llvm.org/svn/llvm-project/llvm/trunk llvm-svn
```
all went well until i got to
```

$ mkdir -p build/odcctools
$ pushd build/odcctools
$ ../../odcctools/configure --target=arm-apple-darwin --disable-ld64

```
I am 99.99% sure I got an error because i'm running a 64-bit OS (9.10 64-bit), but here is the error anyways.
```

ryan@ubuntu:~/iPhone/iphone-dev/build/odcctools$ make
cd libstuff && make
make[1]: Entering directory `/home/ryan/iPhone/iphone-dev/build/odcctools/libstuff'
gcc -Wall -Wno-long-double -Wno-import  -DHAVE_CONFIG_H -D__LITTLE_ENDIAN__=1   -I..//include -I../../../odcctools/include -include ../../../odcctools/include/extern.h -I../../../odcctools/include/foreign -g -O2 -fno-builtin-round -fno-builtin-trunc   -c -o allocate.o ../../../odcctools/libstuff/allocate.c
In file included from ../../../odcctools/include/mach/i386/vm_types.h:66,
                 from ../../../odcctools/include/mach/machine/vm_types.h:29,
                 from ../../../odcctools/include/mach/port.h:79,
                 from ../../../odcctools/include/mach/std_types.h:63,
                 from ../../../odcctools/include/mach/mach.h:60,
                 from ../../../odcctools/libstuff/allocate.c:26:
../../../odcctools/include/i386/_types.h:40: error: conflicting types for ‘__int64_t’
/usr/include/bits/types.h:44: note: previous declaration of ‘__int64_t’ was here
../../../odcctools/include/i386/_types.h:41: error: conflicting types for ‘__uint64_t’
/usr/include/bits/types.h:45: note: previous declaration of ‘__uint64_t’ was here
cc1: warning: unrecognized command line option "-Wno-long-double"
make[1]: *** [allocate.o] Error 1
make[1]: Leaving directory `/home/ryan/iPhone/iphone-dev/build/odcctools/libstuff'
make: *** [libstuff] Error 2

```

how can i fix this?

---

### Post by zine92 on 2010-01-09
i had the same error too though, not too sure how to fix it. On 64bit too. So troublesome to just develop for iphone

---

### Post by uplink3r on 2010-01-19
I'm posting to bump this up.  Should we file a bug report?

**Edit:**  What about using haXe?!  Correct me if I'm wrong you could use haXe to program applications for the iPhone!

[http://haxe.org/doc](http://haxe.org/doc)

---

### Post by Loronal on 2010-02-19
All you guys who say is impossible must be crazy theres and incredible thing called google. If you want to develop for 2.0 well heres a tutorial [http://pimpmiphone.info/howto/install-open-toolchain-on-ubuntu.html ]("http://pimpmiphone.info/howto/install-open-toolchain-on-ubuntu.html")
Also you can also develop java and python apps for the iphone but o course all ubuntu iphone development requires a jailbroken iphone. Search in cydia for python or java

---

### Post by Maheriano on 2010-02-19
What about Android?

---

### Post by casoft on 2013-01-09
To Android you  can use Eclipse and the android plugin. Work perfect!

---

### Post by howefield on 2013-01-09
Old thread closed.

---

