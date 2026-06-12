---
title: "trouble installing VMware workstation"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by blop on 2007-07-22
Hey all im having trouble installing an application in ubuntu....

VMware Workstation v6.0.0.45731 to be specific, inside the package is a vmware-installer.pl file and from my limited experience with linux what i do is this "sudo ./vmware-installer". It prompts me for my password but then nothing happens....well thats a lie....the cursor drops down a line in the terminal but it does not do anything at all! very very very annoying :)


can anyone help?


cheers!

---

### Post by happy-and-lost on 2007-07-22
Try *sudo bash ./vmware-installer.pl*

Being more specific sometimes cures frozen Terminal woes.

---

### Post by blop on 2007-07-22
hey, cheers for the reply..

sadly that has not helped any either

matt@matt-laptop:/media/sda3/Temp/VM/vmlinux/vmware-distrib$ sudo bash ./vmware-installer.pl
Password:
bash: ./vmware-installer.pl: No such file or directory
matt@matt-laptop:/media/sda3/Temp/VM/vmlinux/vmware-distrib$ dir
bin  etc    installer  libvmci.so.0      man   system_etc  vmware-install.pl
doc  FILES  lib        libvmci.so.0.0.0  sbin  usr         vmware-vix
matt@matt-laptop:/media/sda3/Temp/VM/vmlinux/vmware-distrib$ sudo bash ./vmware-install.pl
matt@matt-laptop:/media/sda3/Temp/VM/vmlinux/vmware-distrib$ 



it just does not give any output and returns me to where i was...

---

### Post by testube_babies on 2007-07-22
Are you following any specific install guide?  The only reason I can think of that this wouldn't work is that it's missing linux-headers or build-essential:
```
sudo apt-get install build-essential linux-headers-`uname -r`
```

---

### Post by blop on 2007-07-22
hi...

no im not following any instructions wish i had some!

heres what i get...

matt@matt-laptop:/media/sda3/Temp/VM/vmlinux/vmware-distrib$ sudo apt-get install build-essential linux-headers-`uname -r`
Password:
Sorry, try again.
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.20-16-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev x11proto-xext-dev libatk1.0-dev x11proto-kb-dev
  libglib2.0-dev x11proto-xinerama-dev libpango1.0-dev x11proto-render-dev
  libxi-dev libxrender-dev libcairo2-dev libxdmcp-dev libpng12-dev
  libmono-cairo2.0-cil libfontconfig1-dev xtrans-dev x11proto-core-dev
  libxcursor-dev x11proto-randr-dev libgtk2.0-dev libxext-dev zlib1g-dev
  x11proto-input-dev libfreetype6-dev x11proto-fixes-dev libxau-dev
  libxrandr-dev libexpat1-dev libxft-dev libx11-dev libxfixes-dev
  libxinerama-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
matt@matt-laptop:/media/sda3/Temp/VM/vmlinux/vmware-distrib$ 


i guess that means im not missing anything....

---

### Post by tomcheng76 on 2007-07-22
if you just want to run a virtual machine
i would suggest Virtualbox
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by blop on 2007-07-22
sadly for work purposes i really need to use VM :(

---

### Post by Ansible on 2007-07-22
Isn't VMWare available on the Add/Remove applications window?  I installed vmware server the other day and at first I downloaded the package from vmware.  It had a bunch of dependencies and etc, it looked rather complicated.  I found the app under the add/remove thing, clicked the checkbox and hit apply, that was it.  I had to uninstall my partially installed vmware first though.

ps this was in 7.04

---

### Post by tomcheng76 on 2007-07-22
try this , good luck
[http://www.vmware.com/community/thread.jspa?messageID=567294&#567294](http://www.vmware.com/community/thread.jspa?messageID=567294&#567294)

---

### Post by testube_babies on 2007-07-22
> **Ansible said:**
> Isn't VMWare available on the Add/Remove applications window?  I installed vmware server the other day and at first I downloaded the package from vmware.  It had a bunch of dependencies and etc, it looked rather complicated.  I found the app under the add/remove thing, clicked the checkbox and hit apply, that was it.  I had to uninstall my partially installed vmware first though.

ps this was in 7.04

Here it is, but it's Server not Workstation:
[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

---

### Post by kenweill on 2007-07-27
I have the same problem here... I cant install VMware Workstation under 7.04. 
build-essentials and headers are installed.

This is the last message that I got before its aborted:


None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

---

### Post by kenweill on 2007-08-28
This is not double post... This is an update....

It works now... I've done a fresh install+updates....
Then I install the latest VMware Workstation 6... And it works now without any problem.. The problem i was experiencing before was installing Workstation 5.5.... But it works now with Workstation 6.

Thanx alot for all your replies... :D

---

### Post by mysticmatrix on 2007-08-28
> **kenweill said:**
> This is not double post... This is an update....

It works now... I've done a fresh install+updates....
Then I install the latest VMware Workstation 6... And it works now without any problem.. The problem i was experiencing before was installing Workstation 5.5.... But it works now with Workstation 6.

Thanx alot for all your replies... :D

Well I just downloaded the latest build for Linux the other day from vmware's website and was fine after I installed Linux Headers and Build-essentials. Guess one would need the latest version of there installer.

---

