---
title: "Mac on Linux... What's going on?"
date: 2006-11-11
forum: Apple PPC Users
---

### Post by Torrance on 2006-11-11
Does anyone know the state of "[Mac on Linux]("http://www.maconlinux.org/")"? I've never used it, or heard of anyone else using it, and it seems as though it hasn't been updated in quite a while. But if I were to switch entirely to Linux as my main operating system, I'd really like to know if I could use MoL to view pages with flash and still use InDesign (Scribus still isn't quite there for my needs yet).

Does it work on Ubuntu? Does it work well? And does it work with OSX 10.4.8?

---

### Post by Torrance on 2006-11-11
Hmm.. [Sourceforge]("http://sourceforge.net/projects/mac-on-linux/") is reporting builds as little as a month old.. but one of the feature requests is for PPC64 support. So can anyone confirm then that MoL will not work on a G5?

---

### Post by leafw on 2006-11-11
Yes: I run mol every other day, mainly for InDesign (right on target, your post: Scribus is not up for the task yet). MOL runs just fine on edgy with 10.3.9. I have not tested with 10.4.8 because I don't have it (and I don't want it).

Albert.

---

### Post by Torrance on 2006-11-11
Cheers for the feedback. :D Are you using a G4 or G5?

---

### Post by magnolia fan on 2006-12-17
My OSX is 10.3.9 so I can't comment on newer versions, but MOL is running flawlessy for me.

Here's the instructions I followed for the setup
[https://help.ubuntu.com/community/MacOnLinuxHowto](https://help.ubuntu.com/community/MacOnLinuxHowto)

Everything went five-by-five except for the networking set-up which stated that the new one would be en3 but it was en2.  What ever it comes up as, just roll with it.  It's a killer bonus feature that I didn't even know Linux was capable of.

---

### Post by robyinno on 2007-01-05
yes mol run even with Mac os X 10.4.8, but you need to download and compile the 0.9.71.1 version that you can found in [www.sourceforge.net](www.sourceforge.net) searching mac on linux.

bye

---

### Post by dpny on 2007-01-06
> **robyinno said:**
> yes mol run even with Mac os X 10.4.8, but you need to download and compile the 0.9.71.1 version that you can found in [www.sourceforge.net](www.sourceforge.net) searching mac on linux.

bye

Have you been able to complile 0.9.71.1? I have downloaded the source and done ./configure. Doing make first gave me an error: it was expecting to see the linux source code in /usr/src/linux. I tried to apt-get linux-source, but it was an older version than the latest kernel, so I downloaded the source for 2.6.15 from [here](http://packages.ubuntu.com/dapper/source/linux-source-2.6.15). Running make gave me another error, so I tried with KERNEL_SOURCE=/path to my source. That didn't work, so I just copied the contents into a directory where make expected to see it, /usr/src/linux. Running make gave me this error:

```
Makefile:490: .config: No such file or directory

  WARNING: Symbol version dump /usr/src/linux/Module.symvers
           is missing; modules will have no dependencies and modversions.

cc1: error: include/linux/autoconf.h: No such file or directory
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:17:27: error: linux/version.h: No such file or directory
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:19:5: warning: "LINUX_VERSION_CODE" is not defined
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:19:27: warning: "KERNEL_VERSION" is not defined
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:19:41: error: missing binary operator before token "("
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:23:5: warning: "LINUX_VERSION_CODE" is not defined
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:23:27: warning: "KERNEL_VERSION" is not defined
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:23:41: error: missing binary operator before token "("
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:26:28: error: linux/autoconf.h: No such file or directory
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:29:5: warning: "LINUX_VERSION_CODE" is not defined
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:29:26: warning: "KERNEL_VERSION" is not defined
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:29:40: error: missing binary operator before token "("
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:48: error: syntax error before ‘UTS_RELEASE’
make[5]: *** [/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.o] Error 1
make[4]: *** [_module_/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod] Error 2
nm: '../../../obj-ppc/build/src/kmod/Linux/..//mol.ko': No such file
nm: '../../../obj-ppc/build/src/kmod/Linux/..//mol.ko': No such file
checker.pl failed
rm: cannot remove `../../../obj-ppc/build/src/kmod/Linux/..//mol.ko': No such file or directory
make[3]: *** [all-local] Error 1
make[2]: *** [sub-Linux-all] Error 2
make[1]: *** [sub-kmod-all] Error 2
make: *** [sub-src-all] Error 2
```

Am I missing something else?

---

