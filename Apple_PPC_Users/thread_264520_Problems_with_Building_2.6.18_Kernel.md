---
title: "Problems with Building 2.6.18 Kernel?"
date: 2006-09-24
forum: Apple PPC Users
---

### Post by Torrance on 2006-09-24
Has anyone tried building the latest 2.6.18 kernel with the standard g5_defconfig configuration? I was able to do it with the release candidates, but with the final version my build fails just as it tries to do a "ck_stack" (or something - I don't remember exactly) near the end of making the image.

Anyone know what's going on? I can still build other kernels...

---

### Post by Torrance on 2006-09-24
This is what it says at the end:
```
  BOOTLD  arch/powerpc/boot/zImage.vmode
arch/powerpc/boot/prom.o: In function `claim':
prom.c:(.text+0x764): undefined reference to `__stack_chk_fail'
arch/powerpc/boot/stdio.o: In function `number':
stdio.c:(.text+0x470): undefined reference to `__stack_chk_fail'
make[2]: *** [arch/powerpc/boot/zImage.vmode] Error 1
make[1]: *** [zImage] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.18'
make: *** [debian/stamp-build-kernel] Error 2
```

---

### Post by stmiller on 2006-09-25
Hm. It compiled fine for me. By that message it seems to be barfing on prom.c. 

Try the latest snapshot kernel and see if that compiles, perhaps.

---

### Post by stmiller on 2006-09-25
Ah, yes you need the lastest snapshot. I found this in the changelog, at the very bottom for 2.6.18-git3:

> commit fda7ffd25fc5bbe1b4209dfafb854c7ad7308c93 
tree 1611f33a11f6ecb9beef7999b4a261f4af14e75a 
parent 120bda20c6f64b32e8bfbdd7b34feafaa5f5332e 
author Niels Kristian Bech Jensen <nkbj@mail.tele.dk> Sun, 02 Jul 2006 13:02:27 +0200 
committer Paul Mackerras <paulus@samba.org> Fri, 07 Jul 2006 20:19:15 +1000 

    [POWERPC] Add -fno-stack-protector to BOOTCFLAGS in arch/powerpc/boot/Makefile.
    
    I got some undefined references to __stack_chk_fail in
    arch/powerpc/boot/stdio.o and arch/powerpc/boot/prom.o when I was trying
    to build a kernel on Ubuntu Edgy Eft - which includes Stack Smashing
    Protection.
    
    This patch adds -fno-stack-protector to BOOTCFLAGS in
    arch/powerpc/boot/Makefile (why does BOOTCFLAGS depend on HOSTCFLAGS and
    not CFLAGS?).
    
    Regards,
    Niels Kristian Bech Jensen
    
    Signed-off-by: Paul Mackerras <paulus@samba.org>

---

### Post by Torrance on 2006-09-25
Awesome, thanks for the help dude! :)

---

### Post by kounavi on 2006-10-09
It is really impressive, what you can find on ubuntuforums!
Help on anything!

Thanks mates, I was banging my head on the wall.](*,)

---

