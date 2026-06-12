---
title: "Linux From Scratch - chown: Too many levels of symbolic links"
date: 2017-06-23
forum: Any Other OS
---

### Post by sosproject on 2017-06-23
hy i have build one os and when i use this command
        chown -v lfs $LFS/tools
 return 
        chown: cannot dereference '/tools': Too many levels of symbolic links
        failed to change ownership of '/tools' from 32765 to lfs

---

### Post by coffeecat on 2017-06-23
I assume by "lfs" you mean Linux From Scratch, which is not Ubuntu or Debian based. Therefore, I've moved this thread to ***Any Other OS**.*

I've also changed your title from "Help" to something more informative. It goes without saying that you need help if you are asking a question in a support area. You may find these two threads helpful to you in formulating questions that help others to help you:

[Suggestions on how to get your support questions answered as quickly as possible ](https://ubuntuforums.org/showthread.php?t=1422475)

[Posting Guidelines](https://ubuntuforums.org/showthread.php?t=2158945)

---

### Post by SeijiSensei on 2017-06-23
Some symbolic link in that directory does not point to a file or directory but rather to another link which leads to infinite recursion.

---

### Post by sosproject on 2017-06-26
Thanks, now:
lfs@sos-Intel-powered-classmate-PC:/mnt/lfs/sources/binutils-2.27/build$ make install
make[1]: Entering directory '/mnt/lfs/sources/binutils-2.27/build'
/bin/sh ../mkinstalldirs /tools /tools
make[2]: Entering directory '/mnt/lfs/sources/binutils-2.27/build/bfd'
make  install-recursive
make[3]: Entering directory '/mnt/lfs/sources/binutils-2.27/build/bfd'
Making install in doc
make[4]: Entering directory '/mnt/lfs/sources/binutils-2.27/build/bfd/doc'
 /bin/mkdir -p '/tools/share/info'
 /usr/bin/install -c -m 644 ../../../bfd/doc/bfd.info '/tools/share/info'
 install-info --info-dir='/tools/share/info' '/tools/share/info/bfd.info'
make[4]: Leaving directory '/mnt/lfs/sources/binutils-2.27/build/bfd/doc'
Making install in po
make[4]: Entering directory '/mnt/lfs/sources/binutils-2.27/build/bfd/po'
Makefile:518: *** missing separator.  Stop.
make[4]: Leaving directory '/mnt/lfs/sources/binutils-2.27/build/bfd/po'
Makefile:1711: recipe for target 'install-recursive' failed
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory '/mnt/lfs/sources/binutils-2.27/build/bfd'
Makefile:1848: recipe for target 'install' failed
make[2]: *** [install] Error 2
make[2]: Leaving directory '/mnt/lfs/sources/binutils-2.27/build/bfd'
Makefile:2792: recipe for target 'install-bfd' failed
make[1]: *** [install-bfd] Error 2
make[1]: Leaving directory '/mnt/lfs/sources/binutils-2.27/build'
Makefile:2255: recipe for target 'install' failed
make: *** [install] Error 2

---

