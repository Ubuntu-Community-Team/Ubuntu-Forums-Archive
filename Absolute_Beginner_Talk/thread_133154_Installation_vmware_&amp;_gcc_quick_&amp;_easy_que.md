---
title: "Installation vmware &amp; gcc: quick &amp; easy question: where is the problem ?"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-02-19
Hi, 

I installed vmware.
I do: 
vmware-config.pl 
and get:
   
```
# vmware-config.pl
Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.12-9-386/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.12-9-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/hostif.o
In file included from /tmp/vmware-config2/vmmon-only/linux/hostif.c:68:
/tmp/vmware-config2/vmmon-only/./include/pgtbl.h: In function `PgtblVa2PTELocked':
/tmp/vmware-config2/vmmon-only/./include/pgtbl.h:81: warning: passing arg 1 of `pmd_offset' from incompatible pointer type
  CC [M]  /tmp/vmware-config2/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/vmx86.o
  LD [M]  /tmp/vmware-config2/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config2/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config2/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
The module loads perfectly in the running kernel.

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmnet-only'
make -C /lib/modules/2.6.12-9-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /tmp/vmware-config2/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config2/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config2/vmnet-only/userif.o
In file included from /tmp/vmware-config2/vmnet-only/userif.c:45:
/tmp/vmware-config2/vmnet-only/pgtbl.h: In function `PgtblVa2PTELocked':
/tmp/vmware-config2/vmnet-only/pgtbl.h:81: warning: passing arg 1 of `pmd_offset' from incompatible pointer type
/tmp/vmware-config2/vmnet-only/userif.c: In function `VNetUserIfMapUint32Ptr':
/tmp/vmware-config2/vmnet-only/userif.c:156: warning: `verify_area' is deprecated (declared at include/asm/uaccess.h:105)
/tmp/vmware-config2/vmnet-only/userif.c:157: warning: `verify_area' is deprecated (declared at include/asm/uaccess.h:105)
/tmp/vmware-config2/vmnet-only/userif.c: In function `VNetCopyDatagramToUser':
/tmp/vmware-config2/vmnet-only/userif.c:563: warning: implicit declaration of function `skb_copy_datagram'
  CC [M]  /tmp/vmware-config2/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config2/vmnet-only/bridge.o
/tmp/vmware-config2/vmnet-only/bridge.c: In function `VNetBridgeUp':
/tmp/vmware-config2/vmnet-only/bridge.c:586: warning: passing arg 3 of `sk_alloc' makes pointer from integer without a cast
/tmp/vmware-config2/vmnet-only/bridge.c:586: warning: passing arg 4 of `sk_alloc' makes integer from pointer without a cast
  CC [M]  /tmp/vmware-config2/vmnet-only/procfs.o
  LD [M]  /tmp/vmware-config2/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST
Warning: could not open /tmp/vmware-config2/vmnet-only/includeCheck.h: Invalid argument
*** Warning: "skb_copy_datagram" [/tmp/vmware-config2/vmnet-only/vmnet.ko] undefined!
  CC      /tmp/vmware-config2/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config2/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config2/vmnet-only'
Unable to make a vmnet module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config2/vmnet.o': -1 Unknown symbol in module
There is probably a slight difference in the kernel configuration between the
set of C header files you specified and your running kernel.  You may want to
rebuild a kernel based on that directory, or specify another directory.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```  
  
Where is the prob ? 
  What to do to fix it ?
  
Thank you very much, 

Patrick

---

### Post by patrick295767 on 2006-02-22
The error message is as follows:
[B]There is probably a slight difference in the kernel configuration between the
set of C header files you specified and your running kernel.[/B]

I followed this : [http://www.kubuntu.de/forum/forum.php?req=thread&id=360](http://www.kubuntu.de/forum/forum.php?req=thread&id=360)
  
  
I looked on the net and apparently this probleme is not soo easy
and still get the error ... 

Would some one has an idea ??
  
Thank you very much, 

Kind regards, 

Patrick

---

### Post by kaamos on 2006-02-22
> Using compiler "**/usr/bin/gcc**". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/**2.6.12-9-386**/build/include]

Ubuntu default kernel is compiled with 3.4, so the modules need that as well. Try again like this:
```
sudo su
apt-get install gcc-3.4
export CC=/usr/bin/gcc-3.4
./vmware-install.pl
exit
```

---

### Post by patrick295767 on 2006-02-23
[QUOTE=kaamos]Ubuntu default kernel is compiled with 3.4, so the modules need that as well. Try again like this:
```
sudo su
apt-get install gcc-3.4
export CC=/usr/bin/gcc-3.4
./vmware-install.pl
exit
```[/QUOTE]

Hi, 

I did it and ... Not Working still ...

What could I do to solve this problem ?

Thanks a lot,

Patrick

Please find below the konsole results ... 
```

root@Laptop06:/opt/vmware-distrib/bin# ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
root@Laptop06:/opt/vmware-distrib/bin# export CC=/usr/bin/gcc-3.4
root@Laptop06:/opt/vmware-distrib/bin# ./vmware-config.pl
Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc-3.4". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.12-9-386/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.12-9-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/hostif.o
In file included from /tmp/vmware-config1/vmmon-only/linux/hostif.c:68:
/tmp/vmware-config1/vmmon-only/./include/pgtbl.h: In function `PgtblVa2PTELocked':
/tmp/vmware-config1/vmmon-only/./include/pgtbl.h:81: warning: passing arg 1 of `pmd_offset' from incompatible pointer type
  CC [M]  /tmp/vmware-config1/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmx86.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config1/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
The module loads perfectly in the running kernel.

This program previously created the file /dev/vmmon, and was about to remove it.
Somebody else apparently did it already.

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmnet-only'
make -C /lib/modules/2.6.12-9-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /tmp/vmware-config1/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config1/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config1/vmnet-only/userif.o
In file included from /tmp/vmware-config1/vmnet-only/userif.c:45:
/tmp/vmware-config1/vmnet-only/pgtbl.h: In function `PgtblVa2PTELocked':
/tmp/vmware-config1/vmnet-only/pgtbl.h:81: warning: passing arg 1 of `pmd_offset' from incompatible pointer type
/tmp/vmware-config1/vmnet-only/userif.c: In function `VNetUserIfMapUint32Ptr':
/tmp/vmware-config1/vmnet-only/userif.c:156: warning: `verify_area' is deprecated (declared at include/asm/uaccess.h:105)
/tmp/vmware-config1/vmnet-only/userif.c:157: warning: `verify_area' is deprecated (declared at include/asm/uaccess.h:105)
/tmp/vmware-config1/vmnet-only/userif.c: In function `VNetCopyDatagramToUser':
/tmp/vmware-config1/vmnet-only/userif.c:563: warning: implicit declaration of function `skb_copy_datagram'
  CC [M]  /tmp/vmware-config1/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config1/vmnet-only/bridge.o
/tmp/vmware-config1/vmnet-only/bridge.c: In function `VNetBridgeUp':
/tmp/vmware-config1/vmnet-only/bridge.c:586: warning: passing arg 3 of `sk_alloc' makes pointer from integer without a cast
/tmp/vmware-config1/vmnet-only/bridge.c:586: warning: passing arg 4 of `sk_alloc' makes integer from pointer without a cast
  CC [M]  /tmp/vmware-config1/vmnet-only/procfs.o
  LD [M]  /tmp/vmware-config1/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST
Warning: could not open /tmp/vmware-config1/vmnet-only/includeCheck.h: Invalid argument
*** Warning: "skb_copy_datagram" [/tmp/vmware-config1/vmnet-only/vmnet.ko] undefined!
  CC      /tmp/vmware-config1/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config1/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config1/vmnet-only'
Unable to make a vmnet module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config1/vmnet.o': -1 Unknown symbol in module
There is probably a slight difference in the kernel configuration between the
set of C header files you specified and your running kernel.  You may want to
rebuild a kernel based on that directory, or specify another directory.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

root@Laptop06:/opt/vmware-distrib/bin#   
```

and I installed :
>   	uname -r
Um nun die richtigen Kernelquellen zu instalieren führst Du den Befehl
1  	sudo apt-get install linux-headers-`uname -r`
aus.

Nun must Du noch die anderen benötigten Pakete installieren.
1  	sudo apt-get install kernel-package libdb3-dev libncurses5-dev debhelper html2text perl debconf-utils make gcc gcc-3.4 gcc-3.4-base g++-3.4 cpp

---

### Post by MystaMax on 2006-03-07
I am in the same situation as the thread starter, only I haven't specified the path for the C header. I am following the tutorial available on the wikie titled, [Installing Vmware.]("https://wiki.ubuntu.com/InstallingVMWare?action=show&redirect=VmWare+guide%3A+How+to+install+VMware+in+Breezy")

The script asked, [I]"What is the location of the directory of C header files that match your running kernel? [/usr/src/linux/include]".

[/I]I tried the default which is what it is in the brackets (correct me if I'm wrong), but no luck. I also tried the directory for which Patrick tried, with no luck. I entered the string as follows:

1. /lib/modules/2.6.12-9-386/build/include/    **notice w/o brackets**
2. [/lib/modules/2.6.12-9-386/build/include/] ** notice w/ brckets**

I kinda understood the whole process up until this part. Anyone interested in discussing whats happening? Thanks in advance...

My goal is to get Vmware tools installed properly, and I'm assuming i'm going about this the correct way, if not someone let me know! :)

---

### Post by MystaMax on 2006-03-09
anyone have any ideas?  I'm quite lost on what my next step should be.  As stated above, I'm really trying to get Vmware tools installed to stop the mouse from stuttering and improve video quality.  Any tips, URLs, or hints that point me in the right direction would be of great help! thx

---

### Post by kaamos on 2006-03-09
Have you done
```
sudo apt-get install linux-headers-$(uname -r)
```
?

---

### Post by patrick295767 on 2006-04-02
I made a short script to prepare the ubuntu before starting : ```
./vmware-install.pl
```
   
script :
```
#!/bin/bash
## voor vmware
apt-get -f -y install make
apt-get -f -y install build-essential
apt-get -f -y install gcc-3.4
apt-get -f -y install build-essential 
apt-get -f -y install zenity
apt-get -f -y install linux-tree
apt-get -f -y install g++-3.4
export CXX=/usr/bin/g++-3.4
cat /proc/version
ls /usr/bin/gcc*
rm -rf /usr/src/linux
apt-get -f -y install linux-headers-$(uname -r)
ls /usr/bin/gcc*
ln -s /usr/src/linux-headers-$(uname -r) /usr/src/linux
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
rm /usr/bin/gccbug
ln -s /usr/bin/gccbug-3.4 /usr/bin/gccbug
CC=/usr/bin/gcc-3.4
export CC
```

---

### Post by patrick295767 on 2006-04-02
My script worked !!!
  
I have such error msg now : 
what 's the problem ??
  
```
What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.12-9-386/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.12-9-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/hostif.o
In file included from /tmp/vmware-config1/vmmon-only/linux/hostif.c:68:
/tmp/vmware-config1/vmmon-only/./include/pgtbl.h: In function `PgtblVa2PTELocked':
/tmp/vmware-config1/vmmon-only/./include/pgtbl.h:81: warning: passing arg 1 of `pmd_offset' from incompatible pointer type
  CC [M]  /tmp/vmware-config1/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmx86.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config1/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
The module loads perfectly in the running kernel.

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmnet-only'
make -C /lib/modules/2.6.12-9-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /tmp/vmware-config1/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config1/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config1/vmnet-only/userif.o
In file included from /tmp/vmware-config1/vmnet-only/userif.c:45:
/tmp/vmware-config1/vmnet-only/pgtbl.h: In function `PgtblVa2PTELocked':
/tmp/vmware-config1/vmnet-only/pgtbl.h:81: warning: passing arg 1 of `pmd_offset' from incompatible pointer type
/tmp/vmware-config1/vmnet-only/userif.c: In function `VNetUserIfMapUint32Ptr':
/tmp/vmware-config1/vmnet-only/userif.c:156: warning: `verify_area' is deprecated (declared at include/asm/uaccess.h:105)
/tmp/vmware-config1/vmnet-only/userif.c:157: warning: `verify_area' is deprecated (declared at include/asm/uaccess.h:105)
/tmp/vmware-config1/vmnet-only/userif.c: In function `VNetCopyDatagramToUser':
/tmp/vmware-config1/vmnet-only/userif.c:563: warning: implicit declaration of function `skb_copy_datagram'
  CC [M]  /tmp/vmware-config1/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config1/vmnet-only/bridge.o
/tmp/vmware-config1/vmnet-only/bridge.c: In function `VNetBridgeUp':
/tmp/vmware-config1/vmnet-only/bridge.c:586: warning: passing arg 3 of `sk_alloc' makes pointer from integer without a cast
/tmp/vmware-config1/vmnet-only/bridge.c:586: warning: passing arg 4 of `sk_alloc' makes integer from pointer without a cast
  CC [M]  /tmp/vmware-config1/vmnet-only/procfs.o
  LD [M]  /tmp/vmware-config1/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST
Warning: could not open /tmp/vmware-config1/vmnet-only/includeCheck.h: Invalid argument
*** Warning: "skb_copy_datagram" [/tmp/vmware-config1/vmnet-only/vmnet.ko] undefined!
  CC      /tmp/vmware-config1/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config1/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config1/vmnet-only'
Unable to make a vmnet module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config1/vmnet.o': -1 Unknown symbol in module
There is probably a slight difference in the kernel configuration between the
set of C header files you specified and your running kernel.  You may want to
rebuild a kernel based on that directory, or specify another directory.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

---

### Post by patrick295767 on 2006-04-02
Gooood !!! It works !!
Vmware installed !
  
So, How to:
1/ start thsi script:
```
#!/bin/bash
## voor vmware
apt-get -f -y install make
apt-get -f -y install build-essential
apt-get -f -y install gcc-3.4
apt-get -f -y install build-essential 
apt-get -f -y install zenity
apt-get -f -y install linux-tree
apt-get -f -y install g++-3.4
export CXX=/usr/bin/g++-3.4
cat /proc/version
ls /usr/bin/gcc*
rm -rf /usr/src/linux
apt-get -f -y install linux-headers-$(uname -r)
ls /usr/bin/gcc*
ln -s /usr/src/linux-headers-$(uname -r) /usr/src/linux
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
rm /usr/bin/gccbug
ln -s /usr/bin/gccbug-3.4 /usr/bin/gccbug
CC=/usr/bin/gcc-3.4
export CC
```
  
2/
(let s be sure):
```
export CC=/usr/bin/gcc-3.4
```
  
3/ now, the VMware :
Forget about VMware-workstation-4.5.2  (I think it's working only with Hoary if i recall well)
  
You should have minimum : 
VMware-workstation 5.0.0 for linux
  ===> so, Unpack VMware-workstation 5.0.0 for linux   in your /root   (for instance)
  
4/ run:
```
./vmware-install.pl
```
  
5/ press Enter all time (once you'll have to reply and type YES)
  
6/ done !!
  
7/ Enjoy

---

### Post by pacc on 2006-06-12
This works for me too

unable to compile the VMware VmPerl Scripting API

now all sorted...and I didnt have to learn about kernel compilation to do it....thanks!


[QUOTE=patrick295767]Gooood !!! It works !!
Vmware installed !
  
So, How to:
1/ start thsi script:
```
#!/bin/bash
## voor vmware
apt-get -f -y install make
apt-get -f -y install build-essential
apt-get -f -y install gcc-3.4
apt-get -f -y install build-essential 
apt-get -f -y install zenity
apt-get -f -y install linux-tree
apt-get -f -y install g++-3.4
export CXX=/usr/bin/g++-3.4
cat /proc/version
ls /usr/bin/gcc*
rm -rf /usr/src/linux
apt-get -f -y install linux-headers-$(uname -r)
ls /usr/bin/gcc*
ln -s /usr/src/linux-headers-$(uname -r) /usr/src/linux
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
rm /usr/bin/gccbug
ln -s /usr/bin/gccbug-3.4 /usr/bin/gccbug
CC=/usr/bin/gcc-3.4
export CC
```
  
2/
(let s be sure):
```
export CC=/usr/bin/gcc-3.4
```
  
3/ now, the VMware :
Forget about VMware-workstation-4.5.2  (I think it's working only with Hoary if i recall well)
  
You should have minimum : 
VMware-workstation 5.0.0 for linux
  ===> so, Unpack VMware-workstation 5.0.0 for linux   in your /root   (for instance)
  
4/ run:
```
./vmware-install.pl
```
  
5/ press Enter all time (once you'll have to reply and type YES)
  
6/ done !!
  
7/ Enjoy[/QUOTE]

---

### Post by fakie_flip on 2006-08-22
Problem solved. After much research, I found that I should update my time and syncronize it with the ntp time servers on the internet. Looking in the errors gave let me know about that because I had a simliar problem when compiling something else in Linux. I hope this helps anyone having the same problem.

---

