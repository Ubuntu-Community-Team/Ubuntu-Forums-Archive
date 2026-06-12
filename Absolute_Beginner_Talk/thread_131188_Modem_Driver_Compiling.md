---
title: "Modem Driver Compiling"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by ladyeldawen on 2006-02-15
By some rare chance, I found the exact linux drivers for my modem, but I can't seem to install them. I'm completely new to Ubuntu and Linux. I extracted the archive, cd'd into the directory by command prompt and typed the following:

make clean
make all
 (result) usage: make [536] 
or [clean] or [install]
make 536

I need somebody to make sense of the output following "make 536""

Module precompile check
   Current running kernel is: 2.6.12-10-386
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
ls Intel536.ko >/dev/null 2>&1 ||  uname -r | grep "2.6" && echo "Failed to buil d driver" && exit; \
if [  ]; then \
cd coredrv; make TARGET=TARGET_SELAH KERNEL_SOURCE_PATH= "PSTN_DEF=-DTARGET_SELA H -DTARGET_LINUX -DLINUX" 536core; \
else \
cd coredrv; make TARGET=TARGET_SELAH KERNEL_INCLUDES=/lib/modules/`uname -r`/bui ld/include \
       "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        fi ; \
cp Intel536.o .. ; \
if [ -a /boot/vmlinuz.version.h ]; then \
        cp /boot/vmlinuz.version.h /lib/modules/`uname -r`/build/include/linux/v ersion.h;\
        fi
2.6.12-10-386
make[1]: Entering directory `/home/lauren/Desktop/Intel-536/coredrv'
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/home/lauren/Desktop/Intel-536/ coredrv modules
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 11: gcc-3.4: c ommand not found
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 12: gcc-3.4: c ommand not found
make[2]: gcc-3.4: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /home/lauren/Desktop/Intel-536/coredrv/coredrv.o
/bin/sh: gcc-3.4: command not found
make[3]: *** [/home/lauren/Desktop/Intel-536/coredrv/coredrv.o] Error 127
make[2]: *** [_module_/home/lauren/Desktop/Intel-536/coredrv] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make[1]: *** [536core_26] Error 2
make[1]: Leaving directory `/home/lauren/Desktop/Intel-536/coredrv'
2.6.12-10-386
Failed to build driver

 If somebody was able to read through this all, could you kindly tell me what went wrong, and suggest how to resolve the problem(s)? Thank you much.

---

### Post by towsonu2003 on 2006-02-15
check out the instructions here: 
[https://wiki.ubuntu.com/DialupModemHowto#head-068a426acfdc8518889ea095253c50b665bce5d4](https://wiki.ubuntu.com/DialupModemHowto#head-068a426acfdc8518889ea095253c50b665bce5d4)

and this one is having the same problem, so you might wanna subscribe to that thread for any new posts (other problems s/he'll have, successes or failures etc.) [http://ubuntuforums.org/showthread.php?p=739392#post739392](http://ubuntuforums.org/showthread.php?p=739392#post739392)

The important error in your output is this part:
> 
make[2]: gcc-3.4: Command not foundwhich probably is causing other errors. it means you need gcc-3.4 and the instructions are in the first link above

---

### Post by ladyeldawen on 2006-02-15
[QUOTE=towsonu2003]check out the instructions here: 
[https://wiki.ubuntu.com/DialupModemHowto#head-068a426acfdc8518889ea095253c50b665bce5d4](https://wiki.ubuntu.com/DialupModemHowto#head-068a426acfdc8518889ea095253c50b665bce5d4)

and this one is having the same problem, so you might wanna subscribe to that thread for any new posts (other problems s/he'll have, successes or failures etc.) [http://ubuntuforums.org/showthread.php?p=739392#post739392](http://ubuntuforums.org/showthread.php?p=739392#post739392)

The important error in your output is this part:
which probably is causing other errors. it means you need gcc-3.4 and the instructions are in the first link above[/QUOTE]


 Thank you for the information. I'll be sure to check those out and get gcc-3.4. I edited the post in the other part of the forum, and will be more careful to read the rules next time.

---

