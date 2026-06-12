---
title: "installing kxdocker for gnome?"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by weezerisrock on 2006-09-18
ok I tried installing kxdocker from gnome with the newest stable download from their website.

The ./configure gave me this error:

```
ryan@gandalf:~/temp/software/kxdocker-1.1.4a$ ./configure
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking target system type... i686-pc-linux-gnuoldld
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for kde-config... not found
configure: error: The important program kde-config was not found!
Please check whether you installed KDE correctly.

```

The KXDocker website says it has supported gnome since version 0.37 and I downlaoded 1.1.4.  Any insight would be most helpful!

Thanks

---

### Post by Najand on 2006-09-18
It is one of the depencencies. Use the following command to install it through repositories:
```

sudo aptitude install kxdocker

```

---

