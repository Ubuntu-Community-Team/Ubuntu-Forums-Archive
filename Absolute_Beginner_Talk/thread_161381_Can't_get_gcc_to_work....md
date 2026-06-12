---
title: "Can't get gcc to work..."
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by rfeng on 2006-04-16
Hello,

I just installed ubuntu and am trying to setup my ipod by installing libgpod and gtkpod... BUT when I try to run ./configure I get this error:

rfeng@klutz:~/apps/libgpod-0.3.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

it seems that my gcc is not properly installed...
if I run 
$ which gcc 
it returns nothing but 
$which gcc-4.0
gives:
/usr/bin/gcc-4.0

Can another help? Thanks

---

### Post by cwaldbieser on 2006-04-16
[QUOTE=rfeng]Hello,

I just installed ubuntu and am trying to setup my ipod by installing libgpod and gtkpod... BUT when I try to run ./configure I get this error:

rfeng@klutz:~/apps/libgpod-0.3.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

it seems that my gcc is not properly installed...
if I run 
$ which gcc 
it returns nothing but 
$which gcc-4.0
gives:
/usr/bin/gcc-4.0

Can another help? Thanks[/QUOTE]

If you haven't already:
```

$ sudo apt-get install build-essential

```

If you have, just make a symbolic link from gcc-4.0 to gcc:
```

$ sudo ln -s /usr/bin/gcc-4.0 /usr/bin/gcc

```

---

### Post by gerbman on 2006-04-16
[QUOTE=rfeng]Hello,

I just installed ubuntu and am trying to setup my ipod by installing libgpod and gtkpod... BUT when I try to run ./configure I get this error:

rfeng@klutz:~/apps/libgpod-0.3.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

it seems that my gcc is not properly installed...
if I run 
$ which gcc 
it returns nothing but 
$which gcc-4.0
gives:
/usr/bin/gcc-4.0

Can another help? Thanks[/QUOTE]
Try installing the build-essential package:```
sudo apt-get install build-essential
```

---

### Post by rfeng on 2006-04-17
Wow thanks guys, works like a charm

---

