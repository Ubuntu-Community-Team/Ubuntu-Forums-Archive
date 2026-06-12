---
title: "cant install vmware"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by cosmoshell on 2007-03-20
keep getting this error

Do you accept? (yes/no)          y

Thank you.

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-11-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.20-11-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-11-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-11-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

---

### Post by charles.g.moore on 2007-03-20
I followed this thread and it worked perfectly
[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware)

Make sure you have all of the dependent packages installed before moving forward

---

### Post by Stone123 on 2007-03-20
More info ?
Did  you fallow this link
[https://help.ubuntu.com/community/VMware/Workstation]("https://help.ubuntu.com/community/VMware/Workstation")

OR:

[https://help.ubuntu.com/community/VMware](https://help.ubuntu.com/community/VMware)[https://help.ubuntu.com/community/VMware]("https://help.ubuntu.com/community/VMware")

---

### Post by mills on 2007-03-20
did you install the dependencies?
what guide are you using?

---

### Post by cosmoshell on 2007-03-20
im dident try using a guid but i just tried acouple of them from obuve comments still doesent work

---

### Post by mills on 2007-03-20
this is the guide i use to install [vmware]("http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware")
do you have a c compiler? if your not sure, try;

```
sudo aptitude install build-essential
``` 

then try installing again

---

### Post by hnqla on 2007-03-27
I had this same problem, same error message.

This is how I solved it, so I could run the vmware-config.pl file:

First, I made sure I was at the latest version of vmware's server software.

Second - and most important, there is a patch to the vmware software found here: 
[http://platan.vc.cvut.cz/ftp/pub/vmware/](http://platan.vc.cvut.cz/ftp/pub/vmware/)

Get the latest one called vmware-any-any-update patch.

save that somewhere (like your desktop) and extract it (in gnome, I can right-click an then click 'extract here' from the popup menu).  

From a terminal window, go into your new folder and run the file called 'runme.pl' like this
**sudo ~/wherever_you_put_your_file/vmware-any-any-update108/runme.pl**

That will patch vmware to work with Feisy and automatically can run the vmware-config.pl file to get your virtual machine going.  Everything will compile now.   :)

---

