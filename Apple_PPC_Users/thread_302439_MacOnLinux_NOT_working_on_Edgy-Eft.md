---
title: "MacOnLinux *NOT* working on Edgy-Eft"
date: 2006-11-18
forum: Apple PPC Users
---

### Post by bawalker on 2006-11-18
Hello all,

I'm writing on here as a last resort to get MacOnLinux working on my dual 450mhz "sawtooth" G4 PPC system.  Before diving into the problem, I do want to say that previously somehow MoL was working.  I was using 5.10 at one point, tried 6.06, and somehow by just using synaptic, everything worked and I was able to install OS9.  However that was at 4am three nights ago and I can't remember what I did to get things working.

Here is the current issue.  I installed Ubuntu 6.10 on a clean drive.  I immediately let the system update itself with the critical updates that it found upon the first reboot.  After that, I went to the following Ubuntu page ([https://help.ubuntu.com/community/MacOnLinuxHowto](https://help.ubuntu.com/community/MacOnLinuxHowto)) to follow the wiki instructions on installing MoL.

I added the correct deb path settings to the package manager.  I downloaded M4, debhelper, build-essentials, and all the correct needed utilities to make this work.  The next step is to either use apt-get or synaptic and I download all of the mol files.  The drivers, source, etc.  I get them all.  

After that says it's successful I then run the command "molvconfig" which steps me through the monitor configuration.  That part works great.  However when I run either "startmol" or "startmol -X" I get the following:

******************************************
root@UbuntuPPC6:/usr/src# startmol
cat: /proc/ksyms: No such file or directory
grep: /proc/ksyms: No such file or directory
grep: /proc/ksyms: No such file or directory
grep: /proc/ksyms: No such file or directory
grep: /proc/ksyms: No such file or directory
grep: /proc/ksyms: No such file or directory
grep: /proc/ksyms: No such file or directory
Certain kernel symbols are missing. Trying to find a valid System.map file
The file '/lib/modules/2.6.17-10-powerpc/build/System.map' is missing
Examining '/var/tmp/System.map-2.6.17-10-powerpc'
cat: /proc/ksyms: No such file or directory
**** Symbol file matches ****
cat: /proc/ksyms: No such file or directory
ERROR: The kernel symbol 'handle_mm_fault' could not be found
ERROR: The kernel symbol 'flush_hash_page' could not be found
cat: /proc/ksyms: No such file or directory
Loading MOL molsymglue kernel module
   /usr/lib/mol/modules/2.6.17-10-powerpc/molsymglue.o
insmod: can't read '/usr/lib/mol/modules/2.6.17-10-powerpc/molsymglue.o': No such file or directory
root@UbuntuPPC6:/usr/src# 
******************************************

I did some research and found that this is referencing having the kernel module compiled against the current kernel headers on the system.  Ok no biggie I thought.  I followed the instructions on the Wiki page to build the modules against the kernel headers.  I got as far as the command:

"debian/rules build"  

But I got the following error output from that:

****************************************
root@UbuntuPPC6:/usr/src/modules/mol# debian/rules build
dh_testdir
/usr/bin/make
make[1]: Entering directory `/usr/src/modules/mol'
/usr/bin/make -C kmod
make[2]: Entering directory `/usr/src/modules/mol/kmod'
cc -E -D__ASSEMBLY__ -D__KERNEL__ -DMODULE -I. -Iinclude -I../shared -I/usr/src/linux-headers-2.6.17-10-powerpc/include -Wp,-MD,traps.pp traps.S | m4 -s | tr ';' '\n' > traps.o.s
as traps.o.s  -o traps.o
emulation.S: Assembler messages:
emulation.S:731: Error: too many positional arguments
emulation.S:735: Error: too many positional arguments
emulation.S:739: Error: too many positional arguments
emulation.S:743: Error: too many positional arguments
emulation.S:747: Error: too many positional arguments
emulation.S:751: Error: too many positional arguments
emulation.S:755: Error: too many positional arguments
emulation.S:759: Error: too many positional arguments
emulation.S:763: Error: too many positional arguments
emulation.S:767: Error: too many positional arguments
emulation.S:771: Error: too many positional arguments
emulation.S:775: Error: too many positional arguments
emulation.S:779: Error: too many positional arguments
emulation.S:783: Error: too many positional arguments
emulation.S:787: Error: too many positional arguments
emulation.S:791: Error: too many positional arguments
make[2]: *** [traps.o] Error 1
make[2]: Leaving directory `/usr/src/modules/mol/kmod'
make[1]: *** [kmod] Error 2
make[1]: Leaving directory `/usr/src/modules/mol'
make: *** [build-stamp] Error 2
****************************************


At this point I am getting VERY VERY frustrated.  I have found that sourceforge has the latest 0.971.1 and 0.9.72 builds as of 11/2006, but even when I try to run the make / make install commands I get the following error output below.

********************************
root@UbuntuPPC6:/media/data/mol-0.9.72_pre1# make
test: 9: ==: unexpected operator
./autogen.sh
==================================================
 Invoking autoheader and autoconf.
./autogen.sh: 20: autoheader: not found
autoheader failed
*********************************


As I said, I am really frustrated.  Even at one point I was getting told that xlibs >4.1.0 needed to be installed, but that I couldn't install it.  WTF is going on here?  I just want to run my OS9 and OSX software successfully.


*sigh*


Brad

---

### Post by Brian Smith on 2006-11-18
> **bawalker said:**
> Hello all,

I'm writing on here as a last resort to get MacOnLinux working on my dual 450mhz "sawtooth" G4 PPC system.  Before diving into the problem, I do want to say that previously somehow MoL was working.  I was using 5.10 at one point, tried 6.06, and somehow by just using synaptic, everything worked and I was able to install OS9.  However that was at 4am three nights ago and I can't remember what I did to get things working.




As I said, I am really frustrated.  Even at one point I was getting told that xlibs >4.1.0 needed to be installed, but that I couldn't install it.  WTF is going on here?  I just want to run my OS9 and OSX software successfully.


*sigh*


Brad

Hi Brad.
I haven't used MOL, though it sounds like a nice idea, but I'm just wondering...assuming that you have a bit of disk space, why not simply dual(or triple) boot?  That seems like the advantage of keeping your existing hardware - being able to run Mac OS natively.  Sorry if that isn't what you need; I do understand that meeting the challenge of doing it all on one GUI is appealing.

---

### Post by stmiller on 2006-11-18
> **bawalker said:**
>  but even when I try to run the make / make install commands I get the following error output below.

********************************
root@UbuntuPPC6:/media/data/mol-0.9.72_pre1# make
test: 9: ==: unexpected operator
./autogen.sh
==================================================
 Invoking autoheader and autoconf.
./autogen.sh: 20: autoheader: not found
autoheader failed


You are missing the m4 package, and also the autoconf package. Perhaps more. Looks like you are on the right track to get it compiled.

And for Brian (above): MOL requires a dual boot system. You are simply booting the other partition, inside Linux. With no emulation. It's quite good for most things that aren't too CPU intensive.

---

### Post by bawalker on 2006-11-23
Well I wanted to drop a note in here that after several days of work, research, and hard work, I was able to get MacOnLinux 0.9.70-2 installed on a copy of Ubuntu 6.06 by using the default MOL version on the repository servers. However I was still unable to compile it from source.

Today I reinstalled Ubuntu 6.10 and proceeded to do the critical updates first. From there I got the appropriate packages I was missing, namely M4, autoconf, xlibs and many others. This time around, when I do a 'make' command in the MOL 0.9.72_pre1 (AND) 0.9.71.1 versions, everything compiles except I get an error at the very end of the compile regarding the USBDEV.o file. For the life of me I can't figure out if I'm missing another package or if this regards something in the kernel that needs to be recompiled...??

<much more above this>
cc1: note: obsolete option -I- used, please use -iquote instead
Compiling console.o
cc1: note: obsolete option -I- used, please use -iquote instead
Compiling usbdev.o
cc1: note: obsolete option -I- used, please use -iquote instead
usbdev.c:26:75: error: linux/compiler.h: No such file or directory
make[2]: *** [../../obj-ppc/build/src/drivers/usbdev.o] Error 1
make[1]: *** [sub-drivers-all] Error 2
make: *** [sub-src-all] Error 2
root@UbuntuPPC:/home/bawalker/Desktop/mol-0.9.72_pre1#


Does anyone have any ideas as to what is causing the USBDEV.o file to throw out that error? When doing the initial make command, I got a menuconfig screen that I could disable Generic USB support, but when I do that, I get the following:


<more above this>
cc1: note: obsolete option -I- used, please use -iquote instead
Linking libxkeyremap.a
Compiling init.o
cc1: note: obsolete option -I- used, please use -iquote instead
cc1: note: obsolete option -I- used, please use -iquote instead
../../obj-ppc/build/src/molelf/libxselftest.a(selftest.o): In function `entry':
/home/bawalker/Desktop/mol-0.9.72_pre1/src/molelf/selftest.c:115: undefined reference to `__stack_chk_fail'
../../obj-ppc/build/src/molelf/libxselftest.a(vsprintf.o): In function `number':
/home/bawalker/Desktop/mol-0.9.72_pre1/src/molelf/vsprintf.c:120: undefined reference to `__stack_chk_fail'
../../obj-ppc/build/src/molelf/libxselftest.a(vsprintf.o): In function `printm':
/home/bawalker/Desktop/mol-0.9.72_pre1/src/molelf/vsprintf.c:334: undefined reference to `__stack_chk_fail'
make[2]: *** [../../obj-ppc/build/src/molelf/selftest] Error 1
make[1]: *** [sub-molelf-all] Error 2
make: *** [sub-src-all] Error 2
root@UbuntuPPC:/home/bawalker/Desktop/mol-0.9.72_pre1#


Does anyone have any remote idea what is causing this??

Brad

---

### Post by phidia on 2006-11-26
I don't know if you're aware of this: [https://launchpad.net/distros/ubuntu/+source/mol/+bug/72084](https://launchpad.net/distros/ubuntu/+source/mol/+bug/72084)
it seems relevent to what you're posting.

---

### Post by bawalker on 2006-11-26
Thanks, that solved it!!!

---

