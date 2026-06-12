---
title: "[SOLVED] 5100c LPT Scanner"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by Kralnor on 2007-09-22
I have been trying to get Ubuntu to recognize my HP 5100C scanner but haven't had any luck in doing so.

I've downloaded the drivers here [http://penguin-breeder.org/kernel/download](http://penguin-breeder.org/kernel/download) , unzipped them to a directory and ran make, but that gives the following error:

```

make -C /lib/modules/`uname -r`/build M=`pwd` modules
make[1]: Går til katalog '/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/kralnor/ppscsi-beta2/ppscsi.o
In file included from /home/kralnor/ppscsi-beta2/ppscsi.c:55:
/home/kralnor/ppscsi-beta2/ppscsi.h:16:30: error: linux/autoconfig.h: No such file or directory
make[2]: *** [/home/kralnor/ppscsi-beta2/ppscsi.o] Fejl 1
make[1]: *** [_module_/home/kralnor/ppscsi-beta2] Fejl 2
make[1]: Forlader katalog '/usr/src/linux-headers-2.6.20-16-generic'
make: *** [all] Fejl 2

```

Any help is greatly appreciated! Cheers!

---

### Post by linuxwizard on 2007-09-22
You need to install Sane. That scanner should work complete.
[http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD](http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD)

[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

---

### Post by Kralnor on 2007-09-22
> **linuxwizard said:**
> You need to install Sane. That scanner should work complete.
[http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD](http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD)

[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

I already have Sane installed but it still doesn't work. On the Sane project site it says that the 5100C needs ppscsi driver and epst module to work which are the ones I have been trying to install without success. None of them show up when I run -lsmod.

---

### Post by alienexplorers on 2007-09-22
Did you load
>  libsane
libsane-extras
sane
sane-utils
xsane
xsane-common

---

### Post by Kralnor on 2007-09-23
How do I make sure they are loaded? They all seem to be installed.

---

### Post by linuxwizard on 2007-09-23
Look through link and see if it may help. Not sure if you have seen it.

[http://www.sane-project.org/man/sane-hp.5.html](http://www.sane-project.org/man/sane-hp.5.html)

---

### Post by Kralnor on 2007-09-23
> **linuxwizard said:**
> Look through link and see if it may help. Not sure if you have seen it.

[http://www.sane-project.org/man/sane-hp.5.html](http://www.sane-project.org/man/sane-hp.5.html)

Cheers. I previously read the link until I ran into the following comment:

> 
 Support for models 5100C/5200C connected to the parallel port  requires
the    ppSCSI    driver   available   at   [http://cyberelk.net/tim/par-port/ppscsi.html](http://cyberelk.net/tim/par-port/ppscsi.html) and [http://penguin-breeder.org/kernel/download/](http://penguin-breeder.org/kernel/download/)


Which is where I am stuck - I cannot install the ppSCSI driver. It gives me an error when I run make in the directory where I unpack it.

---

### Post by Kralnor on 2007-09-23
By following the instructions in [this thread](http://ubuntuforums.org/showthread.php?t=441180) I was able to make the scanner work.

Stupid me had accidently misread the line where it said to change config.h to autoconf.h - I mistakingly renamed it autoconf**ig**.h.

:rolleyes:

Cheers for the help given.

---

### Post by linuxwizard on 2007-09-23
I think we all have done things like that get in a hurry didn't double check what we have just done. Later kicking ourself for knowing better. Glad you got it setup and working. Please mark thread solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Kralnor on 2007-09-24
> **linuxwizard said:**
> Please mark thread solved.


Done :)

Now off to scan images!

---

