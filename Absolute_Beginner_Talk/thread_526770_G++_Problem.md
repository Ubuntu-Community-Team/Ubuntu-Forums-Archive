---
title: "G++ Problem"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by ibnuariff on 2007-08-15
Hello guys, have some problem with my g++ compiler. I can compile and link just fine but have problem running the compiled code as follows:

```
test:(.rodata+0x0): multiple definition of `_fp_hw'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crt1.o:../sysdeps/i386/elf/start.S:65: first defined here
test: In function `__data_start': multiple definition of `__dso_handle'
/usr/lib/gcc/i486-linux-gnu/4.0.3/crtbegin.o:(.data+0x0): first defined here
test: In function `_init':/build/buildd/glibc-2.3.6/build-tree/i386-libc/csu/crti.S:32: multiple definition of `_init'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crti.o:/build/buildd/glibc-2.3.6/build-tree/i386-libc/csu/crti.S:11: first defined here
test: In function `_start':../sysdeps/i386/elf/start.S:65: multiple definition of `_start'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crt1.o:../sysdeps/i386/elf/start.S:65: first defined here
test: In function `_fini':/build/buildd/glibc-2.3.6/build-tree/i386-libc/csu/crti.S:47: multiple definition of `_fini'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crti.o:/build/buildd/glibc-2.3.6/build-tree/i386-libc/csu/crti.S:11: first defined here
test: In function `__i686.get_pc_thunk.bx':/build/buildd/glibc-2.3.6/build-tree/i386-libc/csu/crtn.S:34: multiple definition of `__i686.get_pc_thunk.bx'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crti.o:/build/buildd/glibc-2.3.6/build-tree/i386-libc/csu/crti.S:11: first defined here
test:(.rodata+0x4): multiple definition of `_IO_stdin_used'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crt1.o:../sysdeps/i386/elf/start.S:71: first defined here
test: In function `__data_start': multiple definition of `__data_start'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crt1.o:../sysdeps/i386/elf/start.S:65: first defined here
collect2: ld returned 1 exit status
```

Help is much appreciated!

---

### Post by PaulFr on 2007-08-15
What is your compilation command ? For example, if you have a C++ program called sample.cpp, the compilation commands I would use are ```
g++ -c sample.cpp -o sample.o
g++ -o sample sample.o -lm
```Did you miss the **-c** in the compile step ? (-lm is just an example of the math library being linked in)

Just a suggestion, try not to use **test** as an output binary name, because there is already a standard utility called **test** available at /usr/bin/test used in shell scripts. If you do need to use test, please make sure to always run the resulting binary as **./test** or **<path>/test**.

---

