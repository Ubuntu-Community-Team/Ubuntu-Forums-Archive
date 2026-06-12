---
title: "Kqemu won't load"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by GerryH on 2007-12-01
I am in the process of installing first Qemu, and not being able to get the kqemu accelerator to run with it, and then installing Win4Lin and still no joy on Kqemu---

I have run this code:
sudo apt-get -y install linux-headers-$(uname -r) gcc

Then this code:
/opt/win4linpro/bin/build_kqemu.sh

The error log says:

big/little test failed
Could not find kernel includes in /lib/modules or /usr/src/linux - cannot build the kqemu module
Source path       /tmp/.build_kqemu-7822/kqemu
C compiler        /opt/win4linpro/bin/host-gcc
Host C compiler   /opt/win4linpro/bin/host-gcc
make              make
host CPU          i386
test: 347: yes: unexpected operator
make -C common all
make[1]: Entering directory `/tmp/.build_kqemu-7822/kqemu/common'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/tmp/.build_kqemu-7822/kqemu/common'
make -C /usr/src/linux SUBDIRS=`pwd` modules
make: *** /usr/src/linux: No such file or directory.  Stop.
make: *** [kqemu.o] Error 2

So....I tried:
 wget [http://oui.com.br/n/e107_files/downloads/insQEMU.sh](http://oui.com.br/n/e107_files/downloads/insQEMU.sh)

downloaded and installed 28 files and then it says----
Finding out whether your kernel is i386 or i686.
Downloading Linux headers for i686...

E: Couldn't find package linux-headers-686

The Win4lin works fine, way better than qemu does, but it pops up a warning saying it will be slow because kqemu failed to install.

Does anyone know what I did wrong?

Thanks all

---

