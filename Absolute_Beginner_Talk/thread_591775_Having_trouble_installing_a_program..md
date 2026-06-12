---
title: "Having trouble installing a program."
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by dljesse on 2007-10-25
I'm having trouble trying to install lolifox on my computer (altered firefox). Whenever I try to run ./configure I get this error message:

jesse@jesse-desktop:~/lolifox-0.3.2-source/mozilla$ ./configure
Adding configure options from ./.mozconfig:
  --enable-application=browser
  --enable-optimize
  --enable-strip
  --enable-strip-libs
  --disable-debug
  --disable-tests
  --enable-static
  --disable-shared
  --enable-svg
  --enable-canvas
  --enable-update-packaging
loading cache ./config.cache
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking build system type... i686-pc-linux-gnulibc1
checking for gawk... no
checking for mawk... mawk
checking for nsinstall... no
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.
jesse@jesse-desktop:~/lolifox-0.3.2-source/mozilla$       

Anyone help me please?

---

### Post by Maestro23 on 2007-10-25
Do you have** build-essential installed**?

> sudo apt-get install build-essential

---

### Post by dljesse on 2007-10-25
I've gotta say, I feel pretty damn stupid not having that installed. I just reinstalled feisty because gutsy didn't work for me, and that should have been the first thing I installed. Thank you.

---

### Post by Maestro23 on 2007-10-25
> **dljesse said:**
> I've gotta say, I feel pretty damn stupid not having that installed. I just reinstalled feisty because gutsy didn't work for me, and that should have been the first thing I installed. Thank you.

No prob man.  Don't forget to mark this SOLVED using Thread Tools.

Thanks.:)

---

