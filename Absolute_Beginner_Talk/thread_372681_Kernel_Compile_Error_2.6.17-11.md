---
title: "Kernel Compile Error 2.6.17-11"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by EJeanmaire on 2007-02-28
Okay here goes:

A few days ago I figured I would give linux a try once again; picked Ubuntu.  Manage to install from the CD and everything is working great.... except the internet.  It appears that my onboard ethernet is not being recognized correctly, so I get drivers and create a patch from the script they provided, applied the patch, ran menuconfig, added the driver as a module and now I want to recompile and so when typing 'make-kpkg clean' I get this:

--------------------------------------------------------------------------------

root@eric-desktop:/usr/src/linux# make-kpkg clean
exec debian/rules  DEBIAN_REVISION=5:10.Custom  clean 

====== making target CLN-common [new prereqs: testdir]======

====== making target CLN-common [new prereqs: ]======
/usr/bin/make -f ./debian/rules real_stamp_clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11'
====== making target real_stamp_clean [new prereqs: ]======
running clean
test ! -f .config  || cp -pf .config config.precious
test ! -f Makefile || \
            /usr/bin/make    ARCH=i386 distclean
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-11'
scripts/Makefile.clean:17: /usr/src/linux-headers-2.6.17-11/drivers/infiniband/ulp/srp/Makefile: No such file or directory
make[5]: *** No rule to make target `/usr/src/linux-headers-2.6.17-11/drivers/infiniband/ulp/srp/Makefile'.  Stop.
make[4]: *** [drivers/infiniband/ulp/srp] Error 2
make[3]: *** [drivers/infiniband] Error 2
make[2]: *** [_clean_drivers] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-11'
make[1]: *** [real_stamp_clean] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11'
make: *** [CLN-common] Error 2
root@eric-desktop:/usr/src/linux# cd ..
root@eric-desktop:/usr/src# ls
linux                            linux-headers-2.6.17-11
linux-headers-2.6.17-10          linux-headers-2.6.17-11-generic
linux-headers-2.6.17-10-generic  share
root@eric-desktop:/usr/src# 

-------------------------------------------------------------------

I have searched a bunch and have no idea what I am doing wrong at this point, any suggestions would be appreciated.  

I might be missing a step that is very obvious to some of you, but remind you I have never compiled a kernel before, so it is far from obvious to me.

---

### Post by FyreBrand on 2007-02-28
I'm not an expert about this stuff so I could be way off base but it looks like you don't have your kernel headers installed.  Make sure they are installed.

---

### Post by jvc26 on 2007-02-28
For more info on kernel compiling: [http://www.ubuntuforums.org/showthread.php?t=311158](http://www.ubuntuforums.org/showthread.php?t=311158) but more simply it looks like you are missing the header files?
Il

---

### Post by EJeanmaire on 2007-02-28
I have been following the Master Kernel thread, but I am not compiling the new version so i am only following it as much as I can.

Secondly, when looking in synaptic package manager I have 

linux-headers-2.6.17-11
linux-headers-2.6.17-11-386
linux-headers-2.6.17-11-generic

installed (as they have a grey box next to them).  Perhaps this isn't all of them that I need?

Can I install a module and load it without recompilnig the kernel?  Ideally I want to get the internet up any way possible at this point so I don't have to keep rebooting back into windows.

-Eric

---

### Post by FyreBrand on 2007-03-01
> **EJeanmaire said:**
> I have been following the Master Kernel thread, but I am not compiling the new version so i am only following it as much as I can.

Secondly, when looking in synaptic package manager I have 

linux-headers-2.6.17-11
linux-headers-2.6.17-11-386
linux-headers-2.6.17-11-generic

installed (as they have a grey box next to them).  Perhaps this isn't all of them that I need?

Can I install a module and load it without recompilnig the kernel?  Ideally I want to get the internet up any way possible at this point so I don't have to keep rebooting back into windows.

-Eric
First make sure your repositories (restricted, universe, and multiverse) are enabled before you try and add these packages.  Some of the kernel headers might be in a "restricted" or non-free category.

You don't have to recompile the kernel everytime you install a module.  You need to install that appropriate kernel module though.  For example I have an Nvidia video card and use the proprietary nvidia-glx driver from the repositories.  In order for that driver to work I must install the linux restricted kernel modules and the configure xorg to use the driver.

I would do a forum search for your specific networking card and problem and see if someone hasn't already gone through this and found a solution.

Sometimes the vendor provides good drivers and a solution and sometimes they don't.  For example, in addition to my ethernet, I have an intel integrated modem.  It is a software modem and needs the right drivers for it.  The problem is that Intel stopped writing linux drivers for it a long time ago (many kernel versions) and even though they provide drivers and source code to compile I couldn't make it work because their source code wanted an old kernel version and headers.  I would have forever been stuck at this really old kernel if I wanted to use the modem.  In this case my solution was to upgrade to DSL and use the broadcom ethernet card as it is recognized by default.

I would recommend finding out what other people have experienced with this hardware (and there will be others) and what conclusions they came to.  Did they compile their own, did they use a wrapper program of some sort, or did they have to just use different hardware.

If this is a networking problem I would recommend PMing a moderator and asking them to move this thread to the Networking sub-forum.  Then I would try and supply as much detail about my card and setup and see if someone could point you in a better direction.  I just have a feeling that this driver compile might not be the right direction to head.  Better to get some solid advice about this before you spend a bunch of time and effort.

So there are several things to check out in addition to your driver compile.  Maybe there's an easier solution.

---

### Post by jwt48 on 2007-03-03
> **EJeanmaire said:**
> Okay here goes:

A few days ago I figured I would give linux a try once again; picked Ubuntu.  Manage to install from the CD and everything is working great.... except the internet.  It appears that my onboard ethernet is not being recognized correctly, so I get drivers and create a patch from the script they provided, applied the patch, ran menuconfig, added the driver as a module and now I want to recompile and so when typing 'make-kpkg clean' I get this:

--------------------------------------------------------------------------------

root@eric-desktop:/usr/src/linux# make-kpkg clean
exec debian/rules  DEBIAN_REVISION=5:10.Custom  clean 

====== making target CLN-common [new prereqs: testdir]======

====== making target CLN-common [new prereqs: ]======
/usr/bin/make -f ./debian/rules real_stamp_clean
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11'
====== making target real_stamp_clean [new prereqs: ]======
running clean
test ! -f .config  || cp -pf .config config.precious
test ! -f Makefile || \
            /usr/bin/make    ARCH=i386 distclean
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-11'
scripts/Makefile.clean:17: /usr/src/linux-headers-2.6.17-11/drivers/infiniband/ulp/srp/Makefile: No such file or directory
make[5]: *** No rule to make target `/usr/src/linux-headers-2.6.17-11/drivers/infiniband/ulp/srp/Makefile'.  Stop.
make[4]: *** [drivers/infiniband/ulp/srp] Error 2
make[3]: *** [drivers/infiniband] Error 2
make[2]: *** [_clean_drivers] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-11'
make[1]: *** [real_stamp_clean] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11'
make: *** [CLN-common] Error 2
root@eric-desktop:/usr/src/linux# cd ..
root@eric-desktop:/usr/src# ls
linux                            linux-headers-2.6.17-11
linux-headers-2.6.17-10          linux-headers-2.6.17-11-generic
linux-headers-2.6.17-10-generic  share
root@eric-desktop:/usr/src# 

-------------------------------------------------------------------

I have searched a bunch and have no idea what I am doing wrong at this point, any suggestions would be appreciated.  

I might be missing a step that is very obvious to some of you, but remind you I have never compiled a kernel before, so it is far from obvious to me.
I have run into the same problem 3 times. I solve the problem by Installing Ubuntu using the altenate install disk. This always picks up my ethos and everything works fine. I guess it is because I have AMD Ath 64x2 and must use the alternate install disk.

Jerry

---

