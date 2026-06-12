---
title: "error when using make command"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by S1NGH on 2006-09-09
i was having a configuration problem at first but i managed to figure it out, but know the make problem presists and i am not too sure how i can get rid of this error, log is below:

```
Good - your configure finished. Start make now

ravjeet@cyber-linux:~/Desktop/kports-0.6.0/kports-0.6.0$ make && make install
make  all-recursive
make[1]: Entering directory `/home/ravjeet/Desktop/kports-0.6.0/kports-0.6.0'
Making all in src
make[2]: Entering directory `/home/ravjeet/Desktop/kports-0.6.0/kports-0.6.0/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common  -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.cpp; \
        then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
In file included from kportsview.h:63,
                 from kports.h:31,
                 from main.cpp:22:
bsdport.h:912:2: warning: "/*" within comment
bsdport.h: In constructor ‘QMyEvent::QMyEvent(int, QString)’:
bsdport.h:195: warning: ‘QMyEvent::s’ will be initialized after
bsdport.h:200: warning:   base ‘QObject’
bsdport.h:199: warning:   when initialized here
bsdport.h: In constructor ‘QMyEvent::QMyEvent(int, int)’:
bsdport.h:203: warning: base ‘QCustomEvent’ will be initialized after
bsdport.h:203: warning:   base ‘QObject’
bsdport.h:202: warning:   when initialized here
bsdport.h: In constructor ‘QMyEvent::QMyEvent(int, QPtrList<QBsdPort>)’:
bsdport.h:196: warning: ‘QMyEvent::l’ will be initialized after
bsdport.h:206: warning:   base ‘QObject’
bsdport.h:205: warning:   when initialized here
installwizard.h: At global scope:
installwizard.h:89: error: default argument missing for parameter 3 of ‘InstallWizard::InstallWizard(QWidget*, const char*, int)’
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/ravjeet/Desktop/kports-0.6.0/kports-0.6.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ravjeet/Desktop/kports-0.6.0/kports-0.6.0'
make: *** [all] Error 2
```

do i need to install some more stuff or just fix something in the system? i am really stuck over here.

---

### Post by taurus on 2006-09-09
Looks like there is something wrong with the bsdport.h!!!  You can't find a binary for Linux with that app?

---

### Post by S1NGH on 2006-09-10
> **taurus said:**
> Looks like there is something wrong with the bsdport.h!!!  You can't find a binary for Linux with that app?

nope, either i am not looking hard or i just can't get it :S do you have any idea to what i can do?

---

### Post by bodhi.zazen on 2006-09-10
contact the software developers.

---

### Post by jordanmthomas on 2006-09-10
You can also try checking their site to see if there is a patch for bsdport.h

---

### Post by S1NGH on 2006-09-10
thanks, i will try compiling other source codes and see if its the same with all

---

### Post by bodhi.zazen on 2006-09-10
> **S1NGH said:**
> thanks, i will try compiling other source codes and see if its the same with all

You should use checkinstall after ./configure and make (rather then make install)

thus:
[indent]./configure[/indent]
[indent]make[/indent]
[indent]sudo checkinstall[/indent]

---

### Post by S1NGH on 2006-09-10
> **bodhi.zazen said:**
> You should use checkinstall after ./configure and make (rather then make install)

thus:[INDENT]./configure[/INDENT][INDENT]make[/INDENT][INDENT]sudo checkinstall[/INDENT]
works like a charm! ;) so i guess its the bsdport.h which needs patching, my adsl was down earlier so i couldn't post back my feeback.
i am trying to find a paatch, if anyone finds it, please be kind enough and post a link.

---

### Post by S1NGH on 2006-09-10
i got these links, but not too sure:
[http://orbital.wiretapped.net/~technion/technion-ftpd-bsd-0.3.3-9.diff](http://orbital.wiretapped.net/~technion/technion-ftpd-bsd-0.3.3-9.diff)
[http://www.hadrons.org/~guillem/debian/pool/main/inetutils/inetutils_1.4.2+20040207-3_i386.build](http://www.hadrons.org/~guillem/debian/pool/main/inetutils/inetutils_1.4.2+20040207-3_i386.build)
[http://www.hadrons.org/~guillem/debian/pool/main/inetutils/inetutils_1.4.2+20030703-8_i386.build](http://www.hadrons.org/~guillem/debian/pool/main/inetutils/inetutils_1.4.2+20030703-8_i386.build)

---

