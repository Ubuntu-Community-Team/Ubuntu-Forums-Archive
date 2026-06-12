---
title: "Compiling CDemu"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by ace214 on 2007-10-25
Trying to compile CDemu and am getting this error:
```
me@ubuntustudio:~/Desktop/cdemu-0.8$ sudo make
/bin/sh: Syntax error: Bad fd number
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-rt'
/bin/sh: Syntax error: Bad fd number
  CC [M]  /home/jon/Desktop/cdemu-0.8/cdemu_mod.o
/home/jon/Desktop/cdemu-0.8/cdemu_mod.c: In function ‘cdemu_exit’:
/home/jon/Desktop/cdemu-0.8/cdemu_mod.c:198: error: too many arguments to function ‘invalidate_bdev’
make[2]: *** [/home/jon/Desktop/cdemu-0.8/cdemu_mod.o] Error 1
make[1]: *** [_module_/home/jon/Desktop/cdemu-0.8] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-rt'
make: *** [default] Error 2

```
I guess it's incompatibility with the newer kernel code. But there is a patch on the gentoo forums and I'm wondering if this will work? Any help?

[http://forums.gentoo.org/viewtopic-t-594407.html](http://forums.gentoo.org/viewtopic-t-594407.html)

---

### Post by Herm87 on 2007-10-30
Try this patch: [http://bugs.gentoo.org/attachment.cgi?id=127042&action=view](http://bugs.gentoo.org/attachment.cgi?id=127042&action=view)
Worked fine for me (being a linux-newbie) using ubuntu 7.10 gutsy x86_64 on an AMD64 with Kernel ver 2.6.22-14-generic.

---

