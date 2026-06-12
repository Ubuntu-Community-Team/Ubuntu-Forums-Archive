---
title: "Compiling 2.6.18.1 on Edgy"
date: 2006-10-27
forum: Apple PPC Users
---

### Post by Torrance on 2006-10-27
This problem seems to be fairly common, and I was wondering if anyone knows how to get passed it? Basically, I'm trying to compile a 2.6.18.1 vanilla kernel and it's fine up until it tries to create bzipimage, and then it comes up with the following error, and dies:

```
arch/powerpc/boot/prom.o: In function `claim':
prom.c:(.text+0x764): undefined reference to `__stack_chk_fail'
arch/powerpc/boot/stdio.o: In function `number':
stdio.c:(.text+0x470): undefined reference to `__stack_chk_fail'
make[2]: *** [arch/powerpc/boot/zImage.vmode] Error 1
make[1]: *** [zImage] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.18.1'
make: *** [debian/stamp-build-kernel] Error 2
```
Apparently, this is something to do with Edgy, and stack-protection... any one else having this problem?

---

### Post by calum on 2006-10-27
> **Torrance said:**
> This problem seems to be fairly common, and I was wondering if anyone knows how to get passed it? Basically, I'm trying to compile a 2.6.18.1 vanilla kernel and it's fine up until it tries to create bzipimage, and then it comes up with the following error, and dies:

```
arch/powerpc/boot/prom.o: In function `claim':
prom.c:(.text+0x764): undefined reference to `__stack_chk_fail'
arch/powerpc/boot/stdio.o: In function `number':
stdio.c:(.text+0x470): undefined reference to `__stack_chk_fail'
make[2]: *** [arch/powerpc/boot/zImage.vmode] Error 1
make[1]: *** [zImage] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.18.1'
make: *** [debian/stamp-build-kernel] Error 2
```
Apparently, this is something to do with Edgy, and stack-protection... any one else having this problem?

Specifically for compiling MOL, I was able to fix this by adding -fno-stack-protector to the CFLAGS... note I have no idea what this does or whether it's generally applicable, I was just told to do it :)

---

### Post by Torrance on 2006-10-27
Hi Calum,

Yes, that is a fix I have tried. Specifically:

```
sudo gedit /usr/src/linux/Makefile

find line

CFLAGS := -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs \
-fno-strict-aliasing -fno-common

and change it to

CFLAGS := -fno-stack-protector -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs \
-fno-strict-aliasing -fno-common
```

Unfortunately, I still could not compile. The above hack was supposed to work with 2.6.17 - perhaps it no longer works with 2.6.18? Or perhaps there is something specific to building on the ppc platform that is causing this?

Has anyone successfully built a 2.6.18.1 vanilla kernel on a fresh Edgy install on the ppc architecture?

---

### Post by lowracer on 2006-10-27
I was able to compile a 2.6.18.1 kernel on edgy using a Rev B iMac G5 20" machine.  However I got the Error 1 and Error 2, but when I looked there was a fresh vmlinux there in the linux directory so I just copied it to /boot and it worked.  You might look and see if you got a vmlinux file anyway, despite the errors.

---

### Post by Torrance on 2006-11-08
This still isn't sorted, and I've failed to find a work-around so far, so I've posted this as a bug in Launchpad:
[https://launchpad.net/distros/ubuntu/+bug/71014](https://launchpad.net/distros/ubuntu/+bug/71014)

---

### Post by nkbj on 2006-11-09
It is fixed in linux-2.6.19-rc1. The fix is to add -fno-stack-protector to BOOTCFLAGS in arch/powerpc/boot/Makefile (I think - I don't have the code at hand).

Regards,
Niels Kristian

---

### Post by Torrance on 2006-11-10
Oh wicked - that worked. :-D :-D :-D :-D :-D 

Yay - now I have fan control built into the kernel as well as a pretty splash screen.

---

### Post by macintux on 2006-11-11
Yeah! I tried linux kernel 2.6.19 rc5 and it works great :)

---

