---
title: "Error w/ ndiswrapper"
date: 2007-09-05
forum: Apple Intel Users
---

### Post by Remix_eyeballs on 2007-09-05
I have a macbook (white) and have put feisty fawn on it.  I ran 915resolution to get my 1280x800 resolution to work, and now I am installing ndiswrapper 1.47.

I have run:

install distclean

install make

istall build-essentials

And got this error:

oliver@Lexion:~$ cd Desktop/ndiswrapper-1.47
oliver@Lexion:~/Desktop/ndiswrapper-1.47$ make install
make -C driver install
make[1]: Entering directory `/home/oliver/Desktop/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/oliver/Desktop/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
echo /lib/modules/2.6.20-15-generic/misc
/lib/modules/2.6.20-15-generic/misc
mkdir -p /lib/modules/2.6.20-15-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.20-15-generic/misc
install: cannot remove `/lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/oliver/Desktop/ndiswrapper-1.47/driver'
make: *** [install] Error 2
oliver@Lexion:~/Desktop/ndiswrapper-1.47$ 


Anyone know how to fix this?

---

### Post by zekica on 2007-09-05
You are running: **make install** without root privileges (which it requires). You can type: **sudo make install** and then your password.

---

