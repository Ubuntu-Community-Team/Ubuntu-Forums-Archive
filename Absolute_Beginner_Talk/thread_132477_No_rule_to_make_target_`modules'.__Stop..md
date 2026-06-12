---
title: "*** No rule to make target `modules'.  Stop."
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by xixer on 2006-02-18
Hi, this is my first time working with linux and I heard that ubuntu was pretty n00b friendly so I decided to check it out.

Im installing it on my 700m and trying to get the wireless working. I read that i need to upgrade the drivers and firmware. I just got "make" to work and now i get the following error:

**rohit@me:~/Desktop/intel_ipw2200/ipw2200-1.0.0$ make**

make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/rohit/Desktop/intel_ipw2200/ipw2200-1.0.0 MODVERDIR=/home/rohit/Desktop/intel_ipw2200/ipw2200-1.0.0 modules
make[1]: Entering directory `/lib/modules/2.6.12-9-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-9-386/build'
make: *** [modules] Error 2

Can someone please explain to me what that means? and how to fix this?

Thanks

---

### Post by cronholio on 2006-02-18
make is looking for a section called "modules" in /lib/modules/2.6.12-9-386/build/Makefile which isn't there.

---

### Post by dolhop on 2006-02-21
I figured this out....hopefully all with driver build problems will see my post.  I was trying to build the driver for my wireless card and was getting the same error as you: no rule to make target 'modules'.  If you look closely, you'll see that the make file is looking in  /lib/modules/<uname>/.  Most of us just install the kernel headers - which are installed in /usr/src/linux/<uname>/.

Modify the Makefile for the driver you are trying to build such that it looks at the latter instead of the former.  For example, in the driver I was trying to build, near the top was the line:

KVER := $(shell uname -r)

KSRC := /lib/modules/$(KVER)/build

and I changed it to:
KSRC := /usr/src/$(KVER)

Also, be sure you have the right kernel headers - linux-headers-2.6.12-10-386 has the right files, wheras linux-headers-2.6.12-10 doesn't (386 in my case).

Good luck.

---

### Post by jome on 2007-04-01
I have no /usr/src/'uname -r' directory. where would the modules be located then? I found some modules.<whatever> files hanging around in /lib/modules/'uname -r'/

---

### Post by dmjones500 on 2007-04-01
You will have a **/usr/src/linux-headers-`uname -r`** directory if you've installed the kernel headers from the respository.

---

### Post by jome on 2007-04-02
I tried *sudo apt-get install linux-headers-2.6.12-10-686* but the package can not be found.

---

### Post by dmjones500 on 2007-04-02
> **jome said:**
> I tried *sudo apt-get install linux-headers-2.6.12-10-686* but the package can not be found.

I would try:

```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by jome on 2007-04-03
that is the exact same command :confused: I specifically mentioned the name of the package because it does not exist.

---

### Post by dmjones500 on 2007-04-03
> **jome said:**
> that is the exact same command :confused: I specifically mentioned the name of the package because it does not exist.
Ah, I see, apologies.

Synaptic package manager suggests that the 686 package has been replaced by the generic package:

```
sudo apt-get install linux-headers-2.6.12-10-generic
```

should do it...

---

### Post by mravenca on 2008-06-19
Hello, I am trying to make a webcam driver and I get this:

root@ubuntu1:~/inst/webcam/spca5xx# make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/root/inst/webcam/spca5xx CC=cc modules
make[1]: Entering directory `/lib/modules/2.6.15-26-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-26-386/build'
make: *** [default] Error 2

I tried to copy Makefile to /lib/modules/2.6.15-26-386/build but it does not help.

Is my algorithm OK?

---

