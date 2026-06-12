---
title: "Problem with make and the fsam7440 driver on feisty fawn"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by pompos on 2007-04-08
Hey,..
I have got some problem with the installation of the fsam7440 driver :( fsam7440 is needed to activate my wireless card on my laptop.
For installation I usually just had to type in the konsole make && make install && modprobe fsam7440 and everything was okay. It worked in gentoo and edgy eft. However, I now installed Feisty Fawn and it somehow does not work :(

sudo make
> 
make -C /lib/modules/2.6.20-14-generic/build SUBDIRS=/home/vince/fsam7440-0.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-14-generic'
  CC [M]  /home/vince/fsam7440-0.3/fsam7440.o
/home/vince/fsam7440-0.3/fsam7440.c:35:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/vince/fsam7440-0.3/fsam7440.o] Error 1
make[1]: *** [_module_/home/vince/fsam7440-0.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-14-generic'
make: *** [default] Error 2


sudo make install
> su -c "install -d /lib/modules/2.6.20-14-generic/kernel/net/wireless/ && install -m 644 -c fsam7440.ko /lib/modules/2.6.20-14-generic/kernel/net/wireless/ && /sbin/depmod -a"
install: cannot stat `fsam7440.ko': No such file or directory
make: *** [install] Error 1


And of course, the driver cannot be found :(

---

### Post by r00tintheb0x on 2007-04-08
Have you tried "modprobe fsam7400"?

---

### Post by pompos on 2007-04-08
> **r00tintheb0x said:**
> Have you tried "modprobe fsam7400"?
I tried it just now... but I didn't work. Its not the right driver for my Fujitsu-Siemens Amilo M 7440G :(
But I don't think its an issue of this driver but more of *make*.

---

### Post by pompos on 2007-04-08
It works now. The new kernel is making the trouble since config.h is missing since 2.6.19. [[more information](http://www.linuxquestions.org/questions/showthread.php?t=506363)]

I just did *touch /usr/src/linux-headers-2.6.20-14-generic/include/linux/config.h* and then started the normal install procedure of the driver.

---

### Post by gibbsnich on 2007-04-20
Hi!
I also need that module but it seems like your trick doesn't work for me.
It seems like fsam7400 really needs something from linux/config.h: the check_signature method.
And if I just 'touch .../config.h' I get this warning [1] at compile-time and at load-time all I get is [2].

Does anyone know of a replacement for "check_signature"?

Thanks,
Michael

[1] WARNING: "check_signature" [/home/maw/src/driver/fsam7400-0.5.1/fsam7400
[2] fsam7400: Unknown symbol check_signature

---

### Post by Bachstelze on 2007-04-20
This can be worked around by making config.h a symlink to autoconf.h (and sending an email to the developpers so they fix this).

---

### Post by Klak on 2007-04-20
i still can't get it working,
can someonge give me some more hints? or commands?

never had a problem in edgy, but feisty is giving me a hard time

---

