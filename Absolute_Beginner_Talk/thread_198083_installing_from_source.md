---
title: "installing from source"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by nwas on 2006-06-16
Hi,

[COLOR="Red"]I am a KDE user and trying to make NetworkManager work for KDE[/COLOR]

I'm trying to install NetworkManager which is originally a Gnome program but also works for KDE. 

It came as:
NetworkManager-0.6.0.tar.gz

I extracted to my home folder using ark.  I cd to it from the shell and typed this:
nick@nick-laptop:~/NetworkManager-0.6.0$ ./configure
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

nick@nick-laptop:~/NetworkManager-0.6.0$ make
make: *** No targets specified and no makefile found.  Stop.

what is the problem?

in the folder is a Makefile.in and a Makefile.an so i'm not sure what it wants


Thanks

---

### Post by bruce89 on 2006-06-16
KNetworkManager is in the repos, just install that.  Anyway, the build failed, as the compiler is not installed by default.

---

### Post by mscman on 2006-06-16
You don't have any compilers or build tools.  To build files from source, at the very least you need the apps found in the package 'build-essential'  You can get this package via apt using the command:
```
sudo apt-get install build-essential
```

---

### Post by nwas on 2006-06-16
[QUOTE=bruce89]KNetworkManager is in the repos, just install that.  Anyway, the build failed, as the compiler is not installed by default.[/QUOTE]



do I need to install a compiler package?


also Knetworkmanager did not work for me, do you know of any good network managers that you could switch to different wireless networks with out having to edit the /etc/network/interfaces

thanks again

---

