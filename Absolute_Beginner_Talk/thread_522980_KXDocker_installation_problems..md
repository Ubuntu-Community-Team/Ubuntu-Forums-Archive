---
title: "KXDocker installation problems."
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by BuffaloBeagle on 2007-08-11
When i try to ./configure  KXDocker i get this error

```

god@Xubuntu-Box:~/Programs/kxdocker-1.1.4a$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... no
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... no
checking whether g++ supports -Wno-long-long... no
checking whether g++ supports -Wno-non-virtual-dtor... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

```

What can I do that will fix this C++ Error?

---

### Post by SOULRiDER on 2007-08-12
Youll need to install the build-essential package:
```
sudo aptitude install build-essential
```

You might also be interested in creating deb packages so you can uninstall it without trouble
```
sudo aptitude install checkinstall
```

Heres a guide you should read before compiling something. 
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

I would also suggets looking for apckages for KXDocker, theres probably one around. And if you use GNOME and NOT KDE i suggest you use Avant Window Navigator.
[https://launchpad.net/awn](https://launchpad.net/awn)

---

### Post by aysiu on 2007-08-12
Why don't you [enable extra repositories](http://www.psychocats.net/ubuntu/sources) and then install KXDocker from the repositories? ```
sudo apt-get update
sudo apt-get install kxdocker
```

---

