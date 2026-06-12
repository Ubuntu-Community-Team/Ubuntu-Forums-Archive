---
title: "Problems with GCC"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by ibnuariff on 2007-08-22
Hello guys, I'm having problem with GCC. It compiles and links fine but have problem executing. I think there's some redundant libraries in my installation

```

ibnuariff@dark-knight-vm:~$ gcc -c fork.c
ibnuariff@dark-knight-vm:~$ gcc -o fork.out fork.c
ibnuariff@dark-knight-vm:~$ gcc fork.out
fork.out:(.rodata+0x0): multiple definition of `_fp_hw'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crt1.o:../sysdeps/i386/elf/start.S:65: first defined here
fork.out: In function `__data_start': multiple definition of `__dso_handle'
/usr/lib/gcc/i486-linux-gnu/4.0.3/crtbegin.o:(.data+0x0): first defined here
fork.out: In function `_init':/build/buildd/glibc-2.3.6/build-tree/i386-libc/csu/crti.S:32: multiple definition of `_init'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crti.o:/build/buildd/glibc-2.3.6/build-tree/i386-libc/csu/crti.S:11: first defined here
fork.out: In function `_start':../sysdeps/i386/elf/start.S:65: multiple definition of `_start'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crt1.o:../sysdeps/i386/elf/start.S:65: first defined here
fork.out: In function `_fini':/build/buildd/glibc-2.3.6/build-tree/i386-libc/csu/crti.S:47: multiple definition of `_fini'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crti.o:/build/buildd/glibc-2.3.6/build-tree/i386-libc/csu/crti.S:11: first defined here
fork.out: In function `__i686.get_pc_thunk.bx':/build/buildd/glibc-2.3.6/build-tree/i386-libc/csu/crtn.S:34: multiple definition of `__i686.get_pc_thunk.bx'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crti.o:/build/buildd/glibc-2.3.6/build-tree/i386-libc/csu/crti.S:11: first defined here
fork.out:(.rodata+0x4): multiple definition of `_IO_stdin_used'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crt1.o:../sysdeps/i386/elf/start.S:71: first defined here
fork.out: In function `__data_start': multiple definition of `__data_start'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crt1.o:../sysdeps/i386/elf/start.S:65: first defined here
collect2: ld returned 1 exit status
```

---

### Post by russell.h on 2007-08-22
Are you sure you're an absolute beginner? :)

---

### Post by stchman on 2007-08-22
> **ibnuariff said:**
> Hello guys, I'm having problem with GCC. It compiles and links fine but have problem executing. I think there's some redundant libraries in my installation

```

ibnuariff@dark-knight-vm:~$ gcc -c fork.c
ibnuariff@dark-knight-vm:~$ gcc -o fork.out fork.c
ibnuariff@dark-knight-vm:~$ gcc fork.out
fork.out:(.rodata+0x0): multiple definition of `_fp_hw'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crt1.o:../sysdeps/i386/elf/start.S:65: first defined here
fork.out: In function `__data_start': multiple definition of `__dso_handle'
/usr/lib/gcc/i486-linux-gnu/4.0.3/crtbegin.o:(.data+0x0): first defined here
fork.out: In function `_init':/build/buildd/glibc-2.3.6/build-tree/i386-libc/csu/crti.S:32: multiple definition of `_init'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crti.o:/build/buildd/glibc-2.3.6/build-tree/i386-libc/csu/crti.S:11: first defined here
fork.out: In function `_start':../sysdeps/i386/elf/start.S:65: multiple definition of `_start'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crt1.o:../sysdeps/i386/elf/start.S:65: first defined here
fork.out: In function `_fini':/build/buildd/glibc-2.3.6/build-tree/i386-libc/csu/crti.S:47: multiple definition of `_fini'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crti.o:/build/buildd/glibc-2.3.6/build-tree/i386-libc/csu/crti.S:11: first defined here
fork.out: In function `__i686.get_pc_thunk.bx':/build/buildd/glibc-2.3.6/build-tree/i386-libc/csu/crtn.S:34: multiple definition of `__i686.get_pc_thunk.bx'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crti.o:/build/buildd/glibc-2.3.6/build-tree/i386-libc/csu/crti.S:11: first defined here
fork.out:(.rodata+0x4): multiple definition of `_IO_stdin_used'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crt1.o:../sysdeps/i386/elf/start.S:71: first defined here
fork.out: In function `__data_start': multiple definition of `__data_start'
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../lib/crt1.o:../sysdeps/i386/elf/start.S:65: first defined here
collect2: ld returned 1 exit status
```

Once you have compiled the program youi don't need to gcc anymore.  Try this:

```

ibnuariff@dark-knight-vm:~$ gcc -c fork.c
ibnuariff@dark-knight-vm:~$ gcc -o fork.out fork.c
ibnuariff@dark-knight-vm:~$ ./fork.out
```

You need the ./ in front of the .out file.

---

### Post by asmoore82 on 2007-08-22
Ahhaaa!!

```
~ $ gcc -o fork.out fork.c
**~ $ ./fork.out**
```

'gcc fork.out' means you are trying to get gcc to compile the already binary code... That doesn't work.

EDIT: I'm waaay late \\:D/

---

### Post by russell.h on 2007-08-22
Doh, I can't believe I looked at that and didn't see that.
</useless>

---

