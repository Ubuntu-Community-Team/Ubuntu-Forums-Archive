---
title: "Make: Command Not Found"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by gamezealot on 2005-12-18
I'm trying to install softMAC on my iBook. I'm following some instructions I got, i'm trying to get my airport card working, so I'm following this website.

[http://forums.gentoo.org/viewtopic-t-409194.html](http://forums.gentoo.org/viewtopic-t-409194.html)

I do this

hg clone [http://softmac.sipsolutions.net/source](http://softmac.sipsolutions.net/source) 
cd source

it goes to the source folder. but then I try to make and I get this...

gamezealot@ubuntu:~/source$ make
bash: make: command not found

I've tried, gmake, ive installed a bunch of different packages... such as glibc-devel, binutils, cpp, and gcc

I'm a relative newb to the linux world, any help guys?

---

### Post by estel on 2005-12-18
Have you installed build-essential ?

---

### Post by gamezealot on 2005-12-18
Ok awesome, got me one step closer... I installed what you said, but now I get this...

gamezealot@ubuntu:~/source$ make
make: Warning: File `Makefile' has modification time 1.5e+04 s in the future
make -C /lib/modules/2.6.12-9-powerpc/build M=/home/gamezealot/source modules
make: *** /lib/modules/2.6.12-9-powerpc/build: No such file or directory.  Stop.make: *** [modules] Error 2

---

### Post by estel on 2005-12-18
:s.

Look at the properties of source/MAKEFILE. What's it's last modified time?

---

### Post by gamezealot on 2005-12-18
I fixed that error, I just deleted the source folder, then downloaded it again.... the reas of that error message is still coming up though...

root@ubuntu:/home/gamezealot/source# make
make -C /lib/modules/2.6.12-9-powerpc/build M=/home/gamezealot/source modules
make: *** /lib/modules/2.6.12-9-powerpc/build: No such file or directory.  Stop.make: *** [modules] Error 2

No such file or directory...? Is there somethign else I need to install? Or do I need to change something in the source?

---

### Post by gamezealot on 2005-12-18
Ok, so I fixed that problem. Just installed linux-headers-2.6.12-9-powerpc.

But now it still won't compile...

This is what happens now.... heres the end part...

/home/gamezealot/source/ieee80211softmac_io.c: At top level:
/home/gamezealot/source/ieee80211softmac_io.c:429: warning: "struct ieee80211_hdr_2addr" declared inside parameter list
/home/gamezealot/source/ieee80211softmac_io.c: In function `ieee80211softmac_rts_cts':
/home/gamezealot/source/ieee80211softmac_io.c:432: error: `IEEE80211_2ADDR_LEN' undeclared (first usein this function)
/home/gamezealot/source/ieee80211softmac_io.c: In function `ieee80211softmac_send_ctl_frame':
/home/gamezealot/source/ieee80211softmac_io.c:450: error: `IEEE80211_STYPE_RTS' undeclared (first usein this function)
/home/gamezealot/source/ieee80211softmac_io.c:451: error: `IEEE80211_STYPE_CTS' undeclared (first usein this function)
/home/gamezealot/source/ieee80211softmac_io.c:452: warning: passing arg 1 of `ieee80211softmac_rts_cts' from incompatible pointer type
/home/gamezealot/source/ieee80211softmac_io.c: At top level:
/home/gamezealot/source/ieee80211softmac_io.c:445: warning: 'ieee80211softmac_send_ctl_frame' definedbut not used
make[2]: *** [/home/gamezealot/source/ieee80211softmac_io.o] Error 1
make[1]: *** [_module_/home/gamezealot/source] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-powerpc'
make: *** [modules] Error 2

---

### Post by estel on 2005-12-18
That's beyond me, sorry :s

---

### Post by paulmilliken on 2005-12-18
[QUOTE=gamezealot]I fixed that error, I just deleted the source folder, then downloaded it again.... the reas of that error message is still coming up though...

root@ubuntu:/home/gamezealot/source# make
make -C /lib/modules/2.6.12-9-powerpc/build M=/home/gamezealot/source modules
make: *** /lib/modules/2.6.12-9-powerpc/build: No such file or directory.  Stop.make: *** [modules] Error 2

No such file or directory...? Is there somethign else I need to install? Or do I need to change something in the source?[/QUOTE]
There was an error with your ./compile.  It looked for /lib/modules/2.6.12-9-powerpc/build but it couldn't find it.  You may be missing one of the packages or libraries that the program depends on.  If your package is in the repositories then I recommend installing with synaptic package manager as it will automatically install all the packages required to meet the dependencies.

Paul

---

### Post by gamezealot on 2005-12-18
Anybody have any more advice. I'm so close, yet so far...

Still at same spot...

/home/gamezealot/source/ieee80211softmac_io.c: At top level:
/home/gamezealot/source/ieee80211softmac_io.c:429: warning: "struct ieee80211_hdr_2addr" declared inside parameter list
/home/gamezealot/source/ieee80211softmac_io.c: In function `ieee80211softmac_rts_cts':
/home/gamezealot/source/ieee80211softmac_io.c:432: error: `IEEE80211_2ADDR_LEN' undeclared (first usein this function)
/home/gamezealot/source/ieee80211softmac_io.c: In function `ieee80211softmac_send_ctl_frame':
/home/gamezealot/source/ieee80211softmac_io.c:450: error: `IEEE80211_STYPE_RTS' undeclared (first usein this function)
/home/gamezealot/source/ieee80211softmac_io.c:451: error: `IEEE80211_STYPE_CTS' undeclared (first usein this function)
/home/gamezealot/source/ieee80211softmac_io.c:452: warning: passing arg 1 of `ieee80211softmac_rts_cts' from incompatible pointer type
/home/gamezealot/source/ieee80211softmac_io.c: At top level:
/home/gamezealot/source/ieee80211softmac_io.c:445: warning: 'ieee80211softmac_send_ctl_frame' definedbut not used
make[2]: *** [/home/gamezealot/source/ieee80211softmac_io.o] Error 1
make[1]: *** [_module_/home/gamezealot/source] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-powerpc'
make: *** [modules] Error 2

---

