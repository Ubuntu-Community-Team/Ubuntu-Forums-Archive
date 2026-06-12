---
title: "make modules error"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by krolion on 2006-11-10
Hi everybody!

I have just installed an ubuntu 5.10 
I am trying to install zxdsl 852 modem.
I am using the following howto:
[http://doc.ubuntu-fr.org/materiel/zxdsl852](http://doc.ubuntu-fr.org/materiel/zxdsl852)
(its french I know but I haven't found anything better)

I have stopped on 'make modules' command

I've got the following output:

piorek@urwis:~firmware/accessrunner/usbatm$ make modules
make -C /lib/modules/2.6.12-9-386/build M=/home/piotrek/firmware/accessrunner/usbatm modules EXTRA_CFLAGS=-DDEBUG
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/piotrek/firmware/accessrunner/usbatm/speedtch.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/piotrek/firmware/accessrunner/usbatm/speedtch.o] Error 127
make[1]: *** [_module_/home/piotrek/firmware/accessrunner/usbatm] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [modules] Error 2


I don't have any idea whats wrong. pls help!!!

---

### Post by po0f on 2006-11-10
krolion,

Do you have [gcc-3.4](http://packages.ubuntu.com/breezy/devel/gcc-3.4) installed?  Search Synaptic for it.  Better yet, install build-essential as well:
```
$ sudo aptitude update
$ sudo aptitude install build-essential gcc-3.4
```

---

