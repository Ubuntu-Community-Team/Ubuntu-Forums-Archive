---
title: "MOL probs"
date: 2007-01-06
forum: Apple PPC Users
---

### Post by wanger123 on 2007-01-06
Hi all, I thought I'd install MOL just for a laugh (following instructions from here: [https://help.ubuntu.com/community/MacOnLinuxHowto](https://help.ubuntu.com/community/MacOnLinuxHowto)) and couldn't believe it when it just worked out of the box!

But then..........when I installed the mandatory desktop package it no longer boots and I get:

```
MacOS X Boot Loader 1.1.18
>> Candidate boot volume: /mol-blk@0/disk@0:0
>> /mol-blk@0/disk@0:0,\mach_kernel (4343332 bytes)
>> Old mkext timestamp (or safe-boot)
>> Loading from /mol-blk@0/disk@0:0,\System\Library\
Instruction Pointer not in ROM/RAM (nip FFF00700, nip_phys FFF00700)
cleaning up...
Terminating threads...
DONE
```

No amount of uninstalling reinstalling fixes it.

please help!!

wanger

---

### Post by trash on 2007-01-06
at the bottom of that howto it talks about another boot loader problem, perhaps trying that?
but i guess if you can wait a bit to see if anybody else has had these errors.

---

### Post by wanger123 on 2007-01-06
Thanks trash, I figured it out. After you install the desktop MOL package in osx (virtual) you need to reboot into osx (for real) and then back to linux and MOL then works.

Now another prob, I can run MOL but I can't get tun0 to appear in the ifconfig, but in osx I have 'en2'. Anyone know what I'm doing wrong?

I can modprobe tun to make the module available but I cant get it into ifconfig

cheers

wanger

---

### Post by dpny on 2007-01-06
Out of curiosity, what version of OS X are you running in MOL?

---

### Post by wanger123 on 2007-01-07
Hey dpny, sorry about that, I meant to put it in my original post.

I am using 10.4.8

cheers

wanger

---

### Post by dpny on 2007-01-07
> **wanger123 said:**
> Hey dpny, sorry about that, I meant to put it in my original post.

I am using 10.4.8

cheers

wanger

Hmm. You can run 10.4.8 using the version in the repositories? I thought you had to build from source to use Tiger.

---

### Post by wanger123 on 2007-01-07
I had to add these repos for the correct versions

deb [http://people.debian.org/~jensen](http://people.debian.org/~jensen) sid/
deb [http://people.debian.org/~jensen](http://people.debian.org/~jensen) woody/
deb-src [http://people.debian.org/~jensen](http://people.debian.org/~jensen) source/

cheers

wayne

---

### Post by wanger123 on 2007-01-07
OK, just a quick update to let everyone know that I am now on the net with MOL and osx 10.4.8 :mrgreen: :mrgreen: :mrgreen: 

Don't ask me exactly what I did during the last 24 hrs or so (lol) but the thing that finally did it was manually running: 

```
sudo /etc/init.d/dnsmasq restart
sudo /etc/init.d/ipmasq restart
```

after I had a connection in Linux (although I seem to have probs getting a connection on boot up now unless I ifconfig or iwconfig and sometimes run those same scripts above???? :-k

Anyway, after I ran these scripts I had an 'en3' interface in MOL and I configured to use DHCP and I was up and running. Before this was working, I had an 'en2' interface???

Now I'm too scared to turn the laptop off in case it doesn't work again (lol).

Hope those suspend scripts work well in dapper!

ciao

wanger

---

### Post by dpny on 2007-01-07
Can someone help me? Following that HowTo it tells me I need to compile mol 0.9.7.71 from source. Have you been able to complile 0.9.71.1? I have downloaded the source and done ./configure. Doing make first gave me an error: it was expecting to see the linux source code in /usr/src/linux. I tried to apt-get linux-source, but it was an older version than the latest kernel, so I downloaded the source for 2.6.15 from [here](http://packages.ubuntu.com/dapper/source/linux-source-2.6.15). Running make gave me another error, so I tried with KERNEL_SOURCE=/path to my source. That didn't work, so I just copied the contents into a directory where make expected to see it, /usr/src/linux. Running make gave me this error:

```
Makefile:490: .config: No such file or directory

  WARNING: Symbol version dump /usr/src/linux/Module.symvers
           is missing; modules will have no dependencies and modversions.

cc1: error: include/linux/autoconf.h: No such file or directory
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:17:27: error: linux/version.h: No such file or directory
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:19:5: warning: "LINUX_VERSION_CODE" is not defined
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:19:27: warning: "KERNEL_VERSION" is not defined
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:19:41: error: missing binary operator before token "("
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:23:5: warning: "LINUX_VERSION_CODE" is not defined
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:23:27: warning: "KERNEL_VERSION" is not defined
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:23:41: error: missing binary operator before token "("
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:26:28: error: linux/autoconf.h: No such file or directory
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:29:5: warning: "LINUX_VERSION_CODE" is not defined
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:29:26: warning: "KERNEL_VERSION" is not defined
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:29:40: error: missing binary operator before token "("
/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.c:48: error: syntax error before ‘UTS_RELEASE’
make[5]: *** [/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod/_kuname.o] Error 1
make[4]: *** [_module_/opt/src/mol-0.9.71.1/obj-ppc/build/src/kmod] Error 2
nm: '../../../obj-ppc/build/src/kmod/Linux/..//mol.ko': No such file
nm: '../../../obj-ppc/build/src/kmod/Linux/..//mol.ko': No such file
checker.pl failed
rm: cannot remove `../../../obj-ppc/build/src/kmod/Linux/..//mol.ko': No such file or directory
make[3]: *** [all-local] Error 1
make[2]: *** [sub-Linux-all] Error 2
make[1]: *** [sub-kmod-all] Error 2
make: *** [sub-src-all] Error 2
```

Am I missing something else?

---

### Post by calum on 2007-01-09
> **wanger123 said:**
> 
after I had a connection in Linux (although I seem to have probs getting a connection on boot up now unless I ifconfig or iwconfig and sometimes run those same scripts above???? :-k


That sounds normal (if annoying), I always have to manually restart ipmasq after bringing up/configuring my network interfaces too.

---

### Post by wanger123 on 2007-01-09
Hi calum and dpny, I just installed debian testing (etch) and then installed MOL (0.9.71.dsfg-4), mol-os (0.9.71-1), mol-osx (0.9.71-1), mol-linux (0.9.70+1-2) and mol-modules-2.6.18-3-powerpc (2.6.18-3 + 0.9.71.dsfg-4)  from synaptic. Everything just worked first time. 

No extra drivers or compiling required.

I started MOL and even the network connection worked (wireless and ethernet).

Simply amazing!!!!!!!!!! Yeeee Haaaaa!!!

cheers

wanger

---

### Post by dpny on 2007-01-10
> **wanger123 said:**
> Hi calum and dpny, I just installed debian testing (etch) and then installed MOL (0.9.71.dsfg-4), mol-os (0.9.71-1), mol-osx (0.9.71-1), mol-linux (0.9.70+1-2) and mol-modules-2.6.18-3-powerpc (2.6.18-3 + 0.9.71.dsfg-4)  from synaptic. Everything just worked first time. 

No extra drivers or compiling required.

I started MOL and even the network connection worked (wireless and ethernet).

Simply amazing!!!!!!!!!! Yeeee Haaaaa!!!

cheers

wanger

Can I use that stuff? I know Ubuntu is based on Debian, but I am not sure what to do with that information. Can I download the associated .deb files and use them?

edit: I may  have answered my own (dumb) question. Maybe.

---

### Post by dpny on 2007-01-10
I can't seem to get the right kernel module. I have built mol from the latest source and sucessfully installed it. But. . .

```
startmol -X
Mac-on-Linux 0.9.71-pre9 [Jan 9 2007 21:49]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 1
====================================================================
  No mol-0.9.71 kernel modules corresponding to the running
  2.6.15-27-powerpc kernel were found ('startmol --list' displays
  installed version). Recompile the mol kernel modules (recommended)
  or try starting MOL as root using the '-a' switch. The '-a'
  flag can be made default by the 'allow_kver_mismatch: yes' setting.
====================================================================
```

Following their instructions gives me:

```
startmol --list
--------------------------------------------------------------
  Running kernel:         2.6.15-27-powerpc
--------------------------------------------------------------
  Available modules:
    2.6.15.7-ubuntu1      in /usr/local/lib/mol/0.9.71
--------------------------------------------------------------
```

And

```
 sudo startmol -a -X
Mac-on-Linux 0.9.71-pre9 [Jan 9 2007 21:49]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 1
Loading Mac-on-Linux kernel module:
   /usr/local/lib/mol/0.9.71/modules/2.6.15.7-ubuntu1/mol.ko
insmod: error inserting '/usr/local/lib/mol/0.9.71/modules/2.6.15.7-ubuntu1/mol.ko': -1 Invalid module format
====================================================================
  Failed to load the module - try recompiling the MOL kernel
  module. Instructions (and information about common problems)
  are available at <http://www.maconlinux.org>.
====================================================================
```

So I'm confused. I built mol from the source for my kernel. Apparently, though, I did not build the kernel module but only the binary. Following a lead on the mol website to try to build the modules from the source gives:

```
sudo make modules
if [ "$KERNEL_TREES" ] ; then make -s multi_modules ; else make -s modules_ ; fi
+ Entering Linux
  Building modules, stage 2.
Warning: could not find /opt/src/mol-0.9.71_pre9/obj-ppc/build/src/kmod/.traps.o.cmd for /opt/src/mol-0.9.71_pre9/obj-ppc/build/src/kmod/traps.o
    Kernel source                 : /usr/src/linux
    Module compiled for           : 2.6.15.7-ubuntu1
    Running kernel                : 2.6.15-27-powerpc
  Building modules, stage 2.
```

Which still seems a mismatch. I assume this means that the kernel module built into Dapper is for an older kernel. Is there some way to remove it and replace it with one built for my kernel? Any ideas?

---

### Post by dpny on 2007-01-18
With the help of a friend, I figured out the problem. Somehow my sources.list got messed up and I was pulling from pre-Dapper repositories. I fixed my sources.list and was able to get the right source and kernel headers and compile with no probs.

---

