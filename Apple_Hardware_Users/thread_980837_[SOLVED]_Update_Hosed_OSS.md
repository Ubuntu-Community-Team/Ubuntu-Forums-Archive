---
title: "[SOLVED] Update Hosed OSS"
date: 2008-11-13
forum: Apple Hardware Users
---

### Post by Mark76 on 2008-11-13
I have no idea what happened

>  sudo soundon
Relinking OSS kernel modules for "2.6.27-8-generic SMP mod_unload modversions 586 "
This may take few moments - please stand by...

OSS build environment set up for REGPARM kernels


Warning: Cannot locate the Linux kernel development package for
         Linux kernel version  2.6.27-8-generic
         Please install the kernel development package if linking the
         OSS modules fails.

The kernel development package may be called kernel-devel, kernel-smp-devel,
kernel-sources, kernel-headers or something like that. Please refer
to the documentation of your Linux distribution if there are any
difficulties in installing the kernel/driver development environment.

For your Linux distribution the right kernel source package
might be kernel-source.

Under Ubuntu you may need to prepare the kernel environment
after downloading the kernel sources using

  sudo apt-get install linux-headers-2.6.27-8-generic
  cd /usr/src/linux-headers-2.6.27-8-generic/
  sudo make prepare
  sudo make prepare scripts

Building module osscore
Failed to compile OSS
make -C /lib/modules/2.6.27-8-generic/build M=/usr/lib/oss/build modules
make: *** /lib/modules/2.6.27-8-generic/build: No such file or directory. Stop.
make: *** [default] Error 2

Relinking the OSS kernel modules failed


> mark@Archimedes:~$   cd /usr/src/linux-headers-2.6.27-8-generic/
mark@Archimedes:/usr/src/linux-headers-2.6.27-8-generic$   sudo make prepare
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function ‘conf_askvalue’:
scripts/kconfig/conf.c:104: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function ‘conf_choice’:
scripts/kconfig/conf.c:306: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/zconf.tab.o
In file included from scripts/kconfig/zconf.tab.c:2486:
scripts/kconfig/confdata.c: In function ‘conf_write’:
scripts/kconfig/confdata.c:501: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
scripts/kconfig/confdata.c: In function ‘conf_write_autoconf’:
scripts/kconfig/confdata.c:739: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
scripts/kconfig/confdata.c:740: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
In file included from scripts/kconfig/zconf.tab.c:2487:
scripts/kconfig/expr.c: In function ‘expr_print_file_helper’:
scripts/kconfig/expr.c:1090: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/x86/Kconfig
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
make[1]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'. Stop.
make: *** [prepare0] Error 2
mark@Archimedes:/usr/src/linux-headers-2.6.27-8-generic$   sudo make prepare scripts
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[1]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'. Stop.
make: *** [prepare0] Error 2
mark@Archimedes:/usr/src/linux-headers-2.6.27-8-generic$ 



---

### Post by Mark76 on 2008-11-13
Never mind. It came back.

I have no idea how, or why it stopped working in the first place.

---

