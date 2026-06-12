---
title: "cannot 'make'. Files not found"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by foppeh on 2007-12-22
I need to install Madwifi, but I get these errors during 'make':
```
foppe@foppe-laptop:~/madwifi-ng-r2756+ar5007$ sudo make
[sudo] password for foppe:
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/foppe/madwifi-ng-r2756+ar5007 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  HOSTCC  /home/foppe/madwifi-ng-r2756+ar5007/ath_hal/uudecode
/home/foppe/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/foppe/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/foppe/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory

[..snip..]

make[3]: *** [/home/foppe/madwifi-ng-r2756+ar5007/ath_hal/uudecode] Error 1
make[2]: *** [/home/foppe/madwifi-ng-r2756+ar5007/ath_hal] Error 2
make[1]: *** [_module_/home/foppe/madwifi-ng-r2756+ar5007] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Fout 2


```
I downloaded (Synaptic) each and every header file and source file I could find. This is the content of the /usr/src/linux-headers-2.6.22-14-generic folder:
```
arch    Documentation  include  Kbuild  Makefile        net       sound
block   drivers        init     kernel  mm              scripts   usr
crypto  fs             ipc      lib     Module.symvers  security

```
Not many files, but directories.

What is going wrong and more important: what can I do about it?

Thanks

---

### Post by hyper_ch on 2007-12-22
(1) don't "make" with sudo

(2) do you have the linux header files installed?

---

### Post by foppeh on 2007-12-22
It wouldn let me make without sudo.
I have approx ten linux-headers installed through Synaptic. Among them is linux-headers-2.6.22-14-generic I believe the most important.

---

### Post by hyper_ch on 2007-12-22
what are the permissions on the files and the directory that the files are in? I guess you are not the owner of it - hence no rights do do make...

And the problems with make are that it errors here:

> 
/home/foppe/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/foppe/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/foppe/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory


---

### Post by foppeh on 2007-12-22
Suddenly it made sense. The files stdio.h, errno.h, getopt.h are C++ files. I installed the G++ libraries and I finally could compile.

Thanks for your replies.

---

### Post by hyper_ch on 2007-12-22
You can, if you want, press that button: [IMG]http://ubuntuforums.org/images/uf/buttons/post_thanks.gif[/IMG]

---

