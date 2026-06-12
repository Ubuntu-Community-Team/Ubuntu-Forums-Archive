---
title: "gcc flags for powerpc?"
date: 2007-06-18
forum: Apple PPC Users
---

### Post by webaake on 2007-06-18
Is it possible to use optimization flags for GCC when configuring/building for example Transmission source? As far as I understand it's written in C.

I have a powerpc 7400 with altivec and would like to try to optimize the build. I've succesfully built several SVN versions without any options at build time.

If there are flags, how do one use them?

I have Ubuntu 7.04, with GCC 4.xx I think.

 I've used this as a test;

./configure --verbose CFLAGS="-mcpu=7400 -O2 -pipe -maltivec -mabi=altivec -mpowerpc-gfxopt"

Does this look OK? Is the syntax OK? Output of the verbose flag doesn't reveal anything about the CFLAGS.

The build works but I have no way of determining if it is useful. Transmission feels as before, no more no less.

Although there are some nice changes in revision 2153 !!!

---

### Post by yabbadabbadont on 2007-06-18
[http://gentoo-wiki.com/Safe_Cflags](http://gentoo-wiki.com/Safe_Cflags)

You might find that an interesting read.

---

### Post by ssam on 2007-06-19
the gentoo guys are the experts at this.

i have build a gentoo system on a powerbook G4 with the following flags

```
CFLAGS="-mcpu=7450 -mtune=7450 -O2 -pipe -maltivec -mabi=altivec -fno-strict-aliasing -frename-registers -fivopts -ftree-vectorize

```

the above flags were found on the gentoo wiki and forum. be aware that some flags are on by default and some imply others. eg '-O2' is a short hand for many optimisation flags. somtimes you see people who have hundreds of flags, and most of them would still be on if not explicitly stated. (that said i may have made this mistake :-) )

use
```
cat /proc/cpuinfo
```
to check which 74xx revision of the G4 you have, and then lookup in
```
man gcc
```
for the closest revision that it recognises.

--
if you have the time, and are familiar with linux, then i recommend that you have a go installing gentoo. its very intersting (if you like that sort of thing). if you do the installation from a chroot in ubuntu, then you can stay logged in to you existing system while things take hours to compile.

---

### Post by webaake on 2007-06-19
Thx for all replies!

Ill try your CFLAGS settings with alteration of the mcpu and mtune to 7400. I have the first generation G4 so it should work.

As I understand it; these build options will certainely improve performance on a kernel but might it also be better for a common application?

---

### Post by webaake on 2007-06-20
I just used this on the latest Transmission SVN revision and it seems to really rock!

./configure CFLAGS="-mcpu=7400 -mtune=7400 -O2 -pipe -maltivec -mabi=altivec -fno-strict-aliasing -frename-registers -fivopts -ftree-vectorize

Or am I just imagening ?

---

### Post by Gen2ly on 2007-06-21
Yes builds the are custom are absolutly perfect.  Plus transmission is pretty cool.

---

