---
title: "wicrawl make failes with openssl/md5.h"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by dopamine5 on 2007-03-30
Trying to install wicrawl and running make generates this error:

> md5.c:25:25: error: openssl/md5.h: No such file or directory
md5.c: In function ‘md5_mac’:
md5.c:33: error: ‘MD5_CTX’ undeclared (first use in this function)
md5.c:33: error: (Each undeclared identifier is reported only once
md5.c:33: error: for each function it appears in.)
md5.c:33: error: syntax error before ‘context’
md5.c:34: warning: implicit declaration of function ‘MD5_Init’
md5.c:34: error: ‘context’ undeclared (first use in this function)
md5.c:35: warning: implicit declaration of function ‘MD5_Update’
md5.c:38: warning: implicit declaration of function ‘MD5_Final’
md5.c: In function ‘hmac_md5_vector’:
md5.c:45: error: ‘MD5_CTX’ undeclared (first use in this function)
md5.c:45: error: syntax error before ‘context’
md5.c:53: error: ‘context’ undeclared (first use in this function)
make[2]: *** [md5.o] Error 1
make[2]: Leaving directory `/home/dopamine/Desktop/wicrawl-0.3a/plugins/cowpatty-wpa-psk-bruteforce/cowpatty'
make[1]: *** [wicrawl] Error 2
make[1]: Leaving directory `/home/dopamine/Desktop/wicrawl-0.3a/plugins'
make: *** [wicrawl] Error 2


I've installed **openssl-0.9.8e**

What am I doing wrong?

---

### Post by Bachstelze on 2007-03-30
When you get a "file not found" error, the best thing to do is to search for the file on [http://packages.ubuntu.com](http://packages.ubuntu.com) and see which packages provides it. In your case, you need to install *libssl-dev*.

---

### Post by dopamine5 on 2007-03-30
alright,

When I use the Package Installer for libssl-dev, I receive this error, which I have no idea what it means:
[B]
Error: Dependancy is not satisfiable libssl0.9.8[/B]

---

### Post by dopamine5 on 2007-03-30
ok as a newb,

It seems I am continually installing dependancies, is there an easy way to just install, "everything"?

Using the package manager seems tedious to click and click.  I keep getting myself into wanting a program to run, and it wants something, which wants something, which wants something, until I hit a dead end error that I don't know how to solve.

I'm sure I am not going about this the right way but, don't know how else to do this.

---

### Post by Bachstelze on 2007-03-30
That's funny, apt should take care of all the dependencies. Are you using apt-get/synaptic or just manually installing the packages with dpkg ?

---

