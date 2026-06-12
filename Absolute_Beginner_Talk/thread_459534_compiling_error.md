---
title: "compiling error"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by stonerrob420 on 2007-05-30
Hi! I was trying to compile slax module kreator from source so I can convert ubuntu debian packakes to slax modules to help me make a custom distro. I had to install a few packages with sysnaptic to complete dependencies. ./configure went great but when I got to the  "make" part things went wrong. Here is the terminal output:

rob@rob-desktop:~/Desktop$ cd modulekreator
rob@rob-desktop:~/Desktop/modulekreator$ make
Makefile:863: warning: overriding commands for target `clean-bcheck'
Makefile:826: warning: ignoring old commands for target `clean-bcheck'
Makefile:868: warning: overriding commands for target `bcheck-am'
Makefile:831: warning: ignoring old commands for target `bcheck-am'
cd . && rm -f configure
cd . && make -f admin/Makefile.common configure
make[1]: Entering directory `/home/rob/Desktop/modulekreator'
Can't open configure: No such file or directory.
make[1]: Leaving directory `/home/rob/Desktop/modulekreator'
/bin/sh ./config.status --recheck
running CONFIG_SHELL=/bin/sh /bin/sh ./configure   --no-create --no-recursion
/bin/sh: ./configure: No such file or directory
make: *** [config.status] Error 127
rob@rob-desktop:~/Desktop/modulekreator$

Does anybody know how to fix this error? :confused: Any help would be much apperciated. :p

I'm suprised that there not a forum listing called "COMPILING" listed in the forum.

---

### Post by Pragmatist on 2007-05-30
Did you use sudo?

---

### Post by stonerrob420 on 2007-05-31
well it looks like I didn't use sudo......foolish me..lol...anyway here it is using sudo and the results are the same:

rob@rob-desktop:~/Desktop/modulekreator$ sudo make
Makefile:863: warning: overriding commands for target `clean-bcheck'
Makefile:826: warning: ignoring old commands for target `clean-bcheck'
Makefile:868: warning: overriding commands for target `bcheck-am'
Makefile:831: warning: ignoring old commands for target `bcheck-am'
cd . && rm -f configure
cd . && make -f admin/Makefile.common configure
make[1]: Entering directory `/home/rob/Desktop/modulekreator'
Can't open configure: No such file or directory.
make[1]: Leaving directory `/home/rob/Desktop/modulekreator'
/bin/sh ./config.status --recheck
running CONFIG_SHELL=/bin/sh /bin/sh ./configure   --no-create --no-recursion
/bin/sh: ./configure: No such file or directory
make: *** [config.status] Error 127
rob@rob-desktop:~/Desktop/modulekreator$

It's still got the same error........ :p

---

### Post by Pragmatist on 2007-05-31
Please attach the **config.log** and **config.status** files.

---

### Post by stonerrob420 on 2007-05-31
ok..... here are config.log file and config.status. I had to compress them into a .zip file. I hope that I done it right.... :p

---

### Post by sessine on 2007-05-31
ok, I'm not that familiar with the details of make/Makefiles but these two lines:
```
cd . && rm -f configure
cd . && make -f admin/Makefile.common configure
```
worry me.  It seems to be removing the configure file and then trying to use it as an argument to the next command, which results in the error
```
Can't open configure: No such file or directory.
```

maybe something is not quite right with the Makefile ??

---

