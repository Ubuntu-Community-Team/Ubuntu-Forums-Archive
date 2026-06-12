---
title: "Trouble 'make-ing' ndiswrapper package"
date: 2008-04-26
forum: Apple Hardware Users
---

### Post by arseniy on 2008-04-26
I downloaded ndiswrapper-1.38.tar.gz, and extracted it to the Desktop. Then I tried 'make' in Terminal, and I got this/these error(s):

```
arseniy@Arseniy-MacBook:~/Desktop/ndiswrapper-1.38$ sudo make
make -C driver
make[1]: Entering directory `/home/arseniy/Desktop/ndiswrapper-1.38/driver'
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/arseniy/Desktop/ndiswrapper-1.38/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/arseniy/Desktop/ndiswrapper-1.38/driver/ndis.o
/home/arseniy/Desktop/ndiswrapper-1.38/driver/ndis.c:40:47: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/arseniy/Desktop/ndiswrapper-1.38/driver/ndis.c: In function ‘ndis_init’:
/home/arseniy/Desktop/ndiswrapper-1.38/driver/ndis.c:40: error: ‘INIT_WORK’ undeclared (first use in this function)
/home/arseniy/Desktop/ndiswrapper-1.38/driver/ndis.c:40: error: (Each undeclared identifier is reported only once
/home/arseniy/Desktop/ndiswrapper-1.38/driver/ndis.c:40: error: for each function it appears in.)
/home/arseniy/Desktop/ndiswrapper-1.38/driver/ndis.c: In function ‘NdisMIndicateStatus’:
/home/arseniy/Desktop/ndiswrapper-1.38/driver/ndis.c:1936: warning: unused variable ‘radio_status’
make[3]: *** [/home/arseniy/Desktop/ndiswrapper-1.38/driver/ndis.o] Error 1
make[2]: *** [_module_/home/arseniy/Desktop/ndiswrapper-1.38/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/arseniy/Desktop/ndiswrapper-1.38/driver'
make: *** [all] Error 2
```

Anyone have any ideas on what to do? Just some info, I just installed Ubuntu on a MacBook 13" Black, Core 2 Duo 2.0GHz, 2.0GB RAM, and I completely removed traces of OS X from the hard drive.

---

### Post by arseniy on 2008-04-26
Never mind, I used madwifi instead, and after updating my repositories, I was able to get wifi working.

---

### Post by russo.mic on 2008-04-27
> **arseniy said:**
> Never mind, I used madwifi instead, and after updating my repositories, I was able to get wifi working.

Just for your and others info, I think all you needed to do is install the build-essentials package.  It's available on the CD if a network connection can't be established.

Russo

---

### Post by wlamia on 2011-11-01
FWIW, I had the same build problem. I moved the tar package to a different directory, re-extracted, and cd'ed to the fresh extraction. The make process then worked.

---

