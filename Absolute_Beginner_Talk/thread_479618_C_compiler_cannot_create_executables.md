---
title: "C compiler cannot create executables"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by technomaniac on 2007-06-20
Why do I get this message when I try to compile anything from sources

C compiler cannot create executables.

How to set it right?

Actually I was trying to install Canon i255 drivers for Linux. Thats when I got this error

---

### Post by taurus on 2007-06-20
Because you need to install the build-essential package first before you can compile anything from source.

```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by meatpan on 2007-06-20
This an important error and it typically means that the autoconfig process was unable to build a simple test program.

Fortunately, autoconfig logs *everything*, so debugging should be straightforward if you know where to look.

Here is my recommendation:

Try to find the error in config.log.  This file has detailed output of all test programs compiled by autoconfig.  You can open up a terminal and try to replicate the problem.  The config.log file can be failry large, so it might take a while to find the section related to your build problems.  Try doing a search on some proper nouns that were output right before the failure, then scrolling to the compile error.

In my experience, this error is most frequently caused by incorrect formats of CFLAGS and LDFLAGS environment variables.    For example, a mistake in CFLAGS might to forget to prepend an include path with '-I'.  
Perhaps you can inspect these variables by running 'env | grep FLAGS' immediately prior to running './configure'


EDIT: most definitely install the packages recommended by taurus in the post above.  The suggestions in this post should be a last resort.

---

### Post by sanguis on 2007-06-21
> **taurus said:**
> Because you need to install the build-essential package first before you can compile anything from source.

```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

this worked great for me thanx

---

### Post by technomaniac on 2007-06-22
Thank you guys for the reply. That solved everything. I downloaded those packages and updates everything, everything is working fine now.

:p

---

### Post by jollyr0ger on 2007-06-23
hi to all!

i've got the same problem:
```
jollyr0ger@icecube:/usr/src/alsa/alsa-driver-1.0.14$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

and looking into the config.log, i've found these:
```
configure:2049: checking for gcc
configure:2065: found /usr/bin/gcc
configure:2076: result: gcc
configure:2314: checking for C compiler version
configure:2321: gcc --version >&5
Unable to exec gcc.real: No such file or directory
configure:2324: $? = 2
configure:2331: gcc -v >&5
Unable to exec gcc.real: No such file or directory
configure:2334: $? = 2
configure:2341: gcc -V >&5
Unable to exec gcc.real: No such file or directory
configure:2344: $? = 2
configure:2367: checking for C compiler default output file name
configure:2394: gcc    conftest.c  >&5
Unable to exec gcc.real: No such file or directory
```

i've the build-essential installed yet, but the problem persist...

trying gcc -v, these is the result:
```
Unable to exec gcc.real: No such file or directory

```

what can i do??

tnx

---

