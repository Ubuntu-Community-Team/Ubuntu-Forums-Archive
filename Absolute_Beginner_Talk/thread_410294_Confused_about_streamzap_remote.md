---
title: "Confused about streamzap remote"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by ddover on 2007-04-15
I recently bought the streamzap remote control. I plan to use it to replace a Hauppauge remote which is broken. I found directions at [http://www.kdegraaf.net/streamzap/](http://www.kdegraaf.net/streamzap/) for installing it but I think it is having installation problems because of the old remotes drivers. Could someone please tell me how to uninstall LIRC? Also how do you see what is being detected by usb. I thought it was dmesg but I didn't see any relevent information about the Streamzap USB receiver. Thanks

Danny

---

### Post by ddover on 2007-04-15
also how do i edit my profile on my these forums???  :oops:

---

### Post by ddover on 2007-04-15
here is the output from ./configure after it automatically creates all of the folders

You will have to use the lirc_streamzap kernel module.

Now enter 'make' and 'make install' to compile and install the package.

make  all-recursive
make[1]: Entering directory `/home/mythtv/lirc-0.7.2'
Making all in drivers
make[2]: Entering directory `/home/mythtv/lirc-0.7.2/drivers'
Making all in lirc_dev
make[3]: Entering directory `/home/mythtv/lirc-0.7.2/drivers/lirc_dev'
mv Makefile Makefile.automake
mv: overwrite `Makefile.automake', overriding mode 0644? 
cp ../Makefile.kernel Makefile
cp: cannot create regular file `Makefile': Permission denied
make[3]: *** [lirc_dev.o] Error 1
make[3]: Leaving directory `/home/mythtv/lirc-0.7.2/drivers/lirc_dev'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mythtv/lirc-0.7.2/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mythtv/lirc-0.7.2'
make: *** [all] Error 2
$ sudo make
make  all-recursive
make[1]: Entering directory `/home/mythtv/lirc-0.7.2'
Making all in drivers
make[2]: Entering directory `/home/mythtv/lirc-0.7.2/drivers'
Making all in lirc_dev
make[3]: Entering directory `/home/mythtv/lirc-0.7.2/drivers/lirc_dev'
mv Makefile Makefile.automake
cp ../Makefile.kernel Makefile
make -C /lib/modules/2.6.20-13-generic/build/ SUBDIRS=/home/mythtv/lirc-0.7.2/drivers/lirc_dev modules \
                KBUILD_VERBOSE=1
make[4]: Entering directory `/usr/src/linux-headers-2.6.20-13-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (           \
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";      \
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \
        echo;                                                           \
        /bin/false)
mkdir -p /home/mythtv/lirc-0.7.2/drivers/lirc_dev/.tmp_versions
rm -f /home/mythtv/lirc-0.7.2/drivers/lirc_dev/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/mythtv/lirc-0.7.2/drivers/lirc_dev
  gcc -m32 -Wp,-MD,/home/mythtv/lirc-0.7.2/drivers/lirc_dev/.lirc_dev.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=3 -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign -DIRCTL_DEV_MAJOR=61 -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I. -I../.. -I /home/mythtv/lirc-0.7.2/drivers/lirc_dev/../.. -I /lib/modules/2.6.20-13-generic/build//include/  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_dev)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_dev)" -c -o /home/mythtv/lirc-0.7.2/drivers/lirc_dev/.tmp_lirc_dev.o /home/mythtv/lirc-0.7.2/drivers/lirc_dev/lirc_dev.c
/home/mythtv/lirc-0.7.2/drivers/lirc_dev/lirc_dev.c:35:26: error: linux/config.h: No such file or directory
/home/mythtv/lirc-0.7.2/drivers/lirc_dev/lirc_dev.c:54:35: error: linux/devfs_fs_kernel.h: No such file or directory
/home/mythtv/lirc-0.7.2/drivers/lirc_dev/lirc_dev.c: In function ‘cleanup’:
/home/mythtv/lirc-0.7.2/drivers/lirc_dev/lirc_dev.c:132: warning: implicit declaration of function ‘devfs_remove’
/home/mythtv/lirc-0.7.2/drivers/lirc_dev/lirc_dev.c: In function ‘lirc_register_plugin’:
/home/mythtv/lirc-0.7.2/drivers/lirc_dev/lirc_dev.c:381: warning: implicit declaration of function ‘devfs_mk_cdev’
/home/mythtv/lirc-0.7.2/drivers/lirc_dev/lirc_dev.c:386: warning: passing argument 2 of ‘class_device_create’ makes pointer from integer without a cast
/home/mythtv/lirc-0.7.2/drivers/lirc_dev/lirc_dev.c:386: warning: passing argument 3 of ‘class_device_create’ makes integer from pointer without a cast
/home/mythtv/lirc-0.7.2/drivers/lirc_dev/lirc_dev.c:386: warning: passing argument 4 of ‘class_device_create’ from incompatible pointer type
/home/mythtv/lirc-0.7.2/drivers/lirc_dev/lirc_dev.c:386: warning: passing argument 5 of ‘class_device_create’ makes pointer from integer without a cast
make[5]: *** [/home/mythtv/lirc-0.7.2/drivers/lirc_dev/lirc_dev.o] Error 1
make[4]: *** [_module_/home/mythtv/lirc-0.7.2/drivers/lirc_dev] Error 2
make[4]: Leaving directory `/usr/src/linux-headers-2.6.20-13-generic'
make[3]: *** [lirc_dev.o] Error 2
make[3]: Leaving directory `/home/mythtv/lirc-0.7.2/drivers/lirc_dev'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mythtv/lirc-0.7.2/drivers'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mythtv/lirc-0.7.2'
make: *** [all] Error 2

---

### Post by majoridiot on 2007-04-15
assuming you are using edgy, go here: [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)

at the first step, select to build the module "streamzap"
your hardware.conf settings will likely be: LOAD_MODULES=true  MODULES="lirc_streamzap"

your lircd is probably: [http://lirc.sourceforge.net/remotes/streamzap/lircd.conf.streamzap](http://lirc.sourceforge.net/remotes/streamzap/lircd.conf.streamzap)

---

### Post by ddover on 2007-04-16
thanks very much for your help!!! it works perfectly:D

---

### Post by majoridiot on 2007-04-16
glad it's working! :)

---

