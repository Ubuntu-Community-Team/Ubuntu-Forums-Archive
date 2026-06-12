---
title: "Succesful GRUB2 EFI 32-bit build?"
date: 2015-12-07
forum: Apple Hardware Users
---

### Post by Mario_C. on 2015-12-07
I'm following the instructions from [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting) to build a 32-bit (i386) grub.efi file to load Ubuntu Server 14.04.3 onto an XServe1,1.

I'm using a 32-bit version of Ubuntu 14.04.3 Desktop to compile this 32-bit grub.efi file because the instructions recommend that "that the processor architecture of both the kernel and UEFI firmware match." I downloaded all the build dependencies as instructed. I have used both GRUB source 1.99 and 2.00, and on both I get stuck at the "make" stage.

I'd like to know if anyone here has successfully built a 32-bit grub.efi that can give some advice.

In the configure stage, it seems to successfully prepare all the files:

```
*******************************************************
GRUB2 will be compiled with following components:
Platform: i386-efi
With devmapper support: Yes
With memory debugging: No
efiemu runtime: No (not available on efi)
grub-mkfont: Yes
*******************************************************
```

When I type "make" command, after it goes through a long line of checks, I get this output at the end:

```
make  all-recursive
make[3]: Entering directory `/home/it/Desktop/grub-1.99/grub-core/gnulib'
make[4]: Entering directory `/home/it/Desktop/grub-1.99/grub-core/gnulib'
gcc -DHAVE_CONFIG_H -I. -I../..  -I../../intl    -MT argp-ba.o -MD -MP -MF .deps/argp-ba.Tpo -c -o argp-ba.o argp-ba.c
mv -f .deps/argp-ba.Tpo .deps/argp-ba.Po
gcc -DHAVE_CONFIG_H -I. -I../..  -I../../intl    -MT argp-eexst.o -MD -MP -MF .deps/argp-eexst.Tpo -c -o argp-eexst.o argp-eexst.c
In file included from argp.h:22:0,
                 from argp-eexst.c:25:
./stdio.h:456:1: error: 'gets' undeclared here (not in a function)
 _GL_WARN_ON_USE (gets, "gets is a security hole - use fgets instead");
 ^
make[4]: *** [argp-eexst.o] Error 1
make[4]: Leaving directory `/home/it/Desktop/grub-1.99/grub-core/gnulib'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/it/Desktop/grub-1.99/grub-core/gnulib'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/it/Desktop/grub-1.99/grub-core/gnulib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/it/Desktop/grub-1.99'
make: *** [all] Error 2
```

I don't know what to do from here. I'd love some advice.

Thank you, in advance.

---

