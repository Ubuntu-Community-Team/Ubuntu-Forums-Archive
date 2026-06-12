---
title: "Intel 536EP: &quot;Failed To Build Driver&quot;"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by linux4me on 2006-12-16
I got past one problem installing the drivers for my Intel 536EP modem, but now I have another one I haven't been able to figure out.

Here is the output from my "make 536" command in Terminal:
>    Module precompile check
   Current running kernel is: 2.6.15-27-386
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
2.6.15-27-386
make[1]: Entering directory `/home/username/Intel-536/coredrv'
make -C /lib/modules/2.6.15-27-386/build SUBDIRS=/home/username/Intel-536/coredrv modules
/usr/src/linux-headers-2.6.15-27-386/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-headers-2.6.15-27-386/scripts/gcc-version.sh: line 12: gcc: command not found
make[2]: gcc: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.15-27-386'
  CC [M]  /home/username/Intel-536/coredrv/coredrv.o
/bin/sh: gcc: command not found
make[3]: *** [/home/username/Intel-536/coredrv/coredrv.o] Error 127
make[2]: *** [_module_/home/username/Intel-536/coredrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-27-386'
make[1]: *** [536core_26] Error 2
make[1]: Leaving directory `/home/username/Intel-536/coredrv'
2.6.15-27-386
Failed to build driver

I have no clue what I'm doing trying to read that output, but it looks like gcc may be the issue? I checked Synaptic and I have gcc-3.3-base and gcc-4.0-base installed. Plain-old gcc is not. 

Can someone please tell me what the problem is and how to fix this one? Thanks!

---

### Post by linux4me on 2006-12-17
The problem was that I didn't have the gcc package installed. Duh! I'm learning. I installed gcc and was able to build the driver. 

I hope this helps someone else.

---

