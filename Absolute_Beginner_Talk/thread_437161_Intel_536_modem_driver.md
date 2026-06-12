---
title: "Intel 536 modem driver"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by luvinit on 2007-05-08
Hi, I am trying to compile the Intel 536 modem driver in Feisty, which worked fine in Edgy. I am getting the following message, I would appreciate it if anyone's got advice on what it means, exactly?

mark@mark-desktop:~/faxdriver$ make 536
   Module precompile check
   Current running kernel is: 2.6.20-15-generic
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
uname -r|grep "2.6" && \
        cd coredrv && make 536core_26 && \
        cp Intel536.ko .. && cd .. && \
        strip --strip-debug Intel536.ko && \
        exit; \
        ls Intel536.ko >/dev/null 2>&1 ||  uname -r | grep "2.6" && echo "Failed to build driver" && exit; \
        if [  ]; then \
        cd coredrv; make TARGET=TARGET_SELAH KERNEL_SOURCE_PATH= "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        else \
        cd coredrv; make TARGET=TARGET_SELAH KERNEL_INCLUDES=/lib/modules/`uname -r`/build/include \
       "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        fi ; \
        cp Intel536.o .. ; \
        if [ -a /boot/vmlinuz.version.h ]; then \
        cp /boot/vmlinuz.version.h /lib/modules/`uname -r`/build/include/linux/version.h;\
        fi
2.6.20-15-generic
make[1]: Entering directory `/home/mark/faxdriver/coredrv'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/mark/faxdriver/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/mark/faxdriver/coredrv/coredrv.o
In file included from /home/mark/faxdriver/coredrv/hamcore.h:45,
                 from /home/mark/faxdriver/coredrv/coredrv.c:33:
/home/mark/faxdriver/coredrv/hamdefs.h:49:28: error: linux/config.h: No such file or directory
/home/mark/faxdriver/coredrv/coredrv.c:73: warning: data definition has no type or storage class
/home/mark/faxdriver/coredrv/coredrv.c:73: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL_NOVERS’
/home/mark/faxdriver/coredrv/coredrv.c:73: warning: parameter names (without types) in function declaration
/home/mark/faxdriver/coredrv/coredrv.c: In function ‘softcore_init_struct’:
/home/mark/faxdriver/coredrv/coredrv.c:339: warning: assignment from incompatible pointer type
/home/mark/faxdriver/coredrv/coredrv.c: In function ‘open’:
/home/mark/faxdriver/coredrv/coredrv.c:395: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/mark/faxdriver/coredrv/coredrv.c: In function ‘close’:
/home/mark/faxdriver/coredrv/coredrv.c:439: warning: implicit declaration of function ‘pm_unregister’
/home/mark/faxdriver/coredrv/coredrv.c: In function ‘send_data_to_user’:
/home/mark/faxdriver/coredrv/coredrv.c:587: error: ‘struct tty_struct’ has no member named ‘flip’
/home/mark/faxdriver/coredrv/coredrv.c:592: error: ‘struct tty_struct’ has no member named ‘flip’
/home/mark/faxdriver/coredrv/coredrv.c:593: error: ‘struct tty_struct’ has no member named ‘flip’
/home/mark/faxdriver/coredrv/coredrv.c:595: error: ‘struct tty_struct’ has no member named ‘flip’
/home/mark/faxdriver/coredrv/coredrv.c:596: error: ‘struct tty_struct’ has no member named ‘flip’
/home/mark/faxdriver/coredrv/coredrv.c:597: error: ‘struct tty_struct’ has no member named ‘flip’
/home/mark/faxdriver/coredrv/coredrv.c: At top level:
/home/mark/faxdriver/coredrv/coredrv.c:665: error: expected ‘)’ before string constant
/home/mark/faxdriver/coredrv/coredrv.c:778:39: error: macro "DECLARE_WORK" passed 3 arguments, but takes just 2
/home/mark/faxdriver/coredrv/coredrv.c:778: warning: data definition has no type or storage class
/home/mark/faxdriver/coredrv/coredrv.c:778: warning: type defaults to ‘int’ in declaration of ‘DECLARE_WORK’
/home/mark/faxdriver/coredrv/coredrv.c:779:37: error: macro "DECLARE_WORK" passed 3 arguments, but takes just 2
/home/mark/faxdriver/coredrv/coredrv.c:779: warning: data definition has no type or storage class
/home/mark/faxdriver/coredrv/coredrv.c:779: warning: type defaults to ‘int’ in declaration of ‘DECLARE_WORK’
/home/mark/faxdriver/coredrv/coredrv.c: In function ‘wake_up_interruptible_persistReadQ’:
/home/mark/faxdriver/coredrv/coredrv.c:793: error: ‘wait_wq’ undeclared (first use in this function)
/home/mark/faxdriver/coredrv/coredrv.c:793: error: (Each undeclared identifier is reported only once
/home/mark/faxdriver/coredrv/coredrv.c:793: error: for each function it appears in.)
/home/mark/faxdriver/coredrv/coredrv.c: In function ‘interruptible_sleep_on_timeout_persistReadQ’:
/home/mark/faxdriver/coredrv/coredrv.c:827: error: ‘wait_wq2’ undeclared (first use in this function)
/home/mark/faxdriver/coredrv/coredrv.c: At top level:
/home/mark/faxdriver/coredrv/coredrv.c:880: warning: initialization makes integer from pointer without a cast
make[3]: *** [/home/mark/faxdriver/coredrv/coredrv.o] Error 1
make[2]: *** [_module_/home/mark/faxdriver/coredrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: *** [536core_26] Error 2
make[1]: Leaving directory `/home/mark/faxdriver/coredrv'
2.6.20-15-generic
Failed to build driver
mark@mark-desktop:~/faxdriver$ 

Thanks.

---

### Post by Bachstelze on 2007-05-08
That driver is just not compatible with Feisty's 2.6.20 kernel. Either go back to Edgy or build a 2.6.17 kernel from source in Feisty.

---

### Post by luvinit on 2007-05-08
OK thanks. I haven't got a clue how to do that, so I guess I will just give it a miss. :popcorn:

---

### Post by luvinit on 2007-05-23
Working driver here

[http://linmodems.technion.ac.il/packages/intel/Philippe.Vouters/](http://linmodems.technion.ac.il/packages/intel/Philippe.Vouters/)

choose intel-536EP-2.56.76.0_23_02_2007.tgz

---

### Post by Sepero on 2007-06-12
I don't know if you're still having problems with this driver or not. If so, you may wish to check out the precompiled package for this driver I just released.
[http://ubuntuforums.org/showthread.php?t=471503](http://ubuntuforums.org/showthread.php?t=471503)

---

### Post by luvinit on 2007-06-12
Hi, I got it sorted with the driver I linked to, however it is good to have a deb and I will try it out next time I need to alter things e.g. if there is an upgrade etc. Thanks a lot.

---

