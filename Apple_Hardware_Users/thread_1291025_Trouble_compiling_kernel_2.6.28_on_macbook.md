---
title: "Trouble compiling kernel 2.6.28 on macbook"
date: 2009-10-14
forum: Apple Hardware Users
---

### Post by Elguapo_85 on 2009-10-14
I was using the HOWTO: Compile a Kernel for your macbook guide from this forum and when I got to actually compiling the kernel I get this error.

first a bunch of unionfs/super.c warnings and errors
make[3]: *** [ubuntu/unionfs/super.o] Error 1
make[2]: *** [ubuntu/unionfs] Error 2
make[1]: *** [ubuntu] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.28'
make: *** [debian/stamp/build/kernel] Error 2
than it stops!
please help, I need to compile this kernel to be able to do my OS homework. Thanks guys!

---

### Post by ALLurGroceries on 2009-10-14
> **Elguapo_85 said:**
> I was using the HOWTO: Compile a Kernel for your macbook guide from this forum and when I got to actually compiling the kernel I get this error.

first a bunch of unionfs/super.c warnings and errors
make[3]: *** [ubuntu/unionfs/super.o] Error 1
make[2]: *** [ubuntu/unionfs] Error 2
make[1]: *** [ubuntu] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.28'
make: *** [debian/stamp/build/kernel] Error 2
than it stops!
please help, I need to compile this kernel to be able to do my OS homework. Thanks guys!

Do a make menuconfig and deselect unionfs under filesystems. Then make-kpkg clean and redo your build. Or if you need unionfs post whatever the errors are directly above what you pasted, since there are no compiler messages in your post. Try searching for the compiler errors or warnings and that should turn up a solution. Good luck.

Edit: Also that is a really old kernel you are building, if you're going for something newer than .28 *AND* you need unionfs, it got removed from the mainline kernel in .29, so you need patches from here for the appropriate kernel version:
[http://www.filesystems.org/project-unionfs.html]("http://www.filesystems.org/project-unionfs.html")

---

