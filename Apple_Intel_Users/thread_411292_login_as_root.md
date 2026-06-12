---
title: "login as root"
date: 2007-04-16
forum: Apple Intel Users
---

### Post by higgitron on 2007-04-16
THis is going to sound really stupid, but how do i login as root.  I'm trying to install my wireless card for my macbook and it errors out saying i don't have permission 

benhiggins@benhiggins-laptop:~/Desktop/ndiswrapper-1.41$ make install
make -C driver install
make[1]: Entering directory `/home/benhiggins/Desktop/ndiswrapper-1.41/driver'
make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/home/benhiggins/Desktop/ndiswrapper-1.41/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
echo /lib/modules/2.6.17-11-generic/misc
/lib/modules/2.6.17-11-generic/misc
mkdir -p /lib/modules/2.6.17-11-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.17-11-generic/misc
install: cannot remove `/lib/modules/2.6.17-11-generic/misc/ndiswrapper.ko': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/benhiggins/Desktop/ndiswrapper-1.41/driver'
make: *** [install] Error 2
benhiggins@benhiggins-laptop:~/Desktop/ndiswrapper-1.41$ 

can some one point me in the right direction

---

### Post by higgitron on 2007-04-16
ok i have the root thing, but still can't get my wireless up and going.  I can ndiswrapper from inside it's own dir, but from no dir below that.  What do i need to do.  I've been reading as much info as i can find, but still can't get it to work.  I am also having trouble getting wine to work?

---

### Post by ronocdh on 2007-04-16
Please post more info about your hardware. Include also which version of Ubuntu you're trying this on, and what you've tried so far, along with any errors. We'll go from there. =)

---

