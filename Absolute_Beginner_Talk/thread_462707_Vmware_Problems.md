---
title: "Vmware Problems"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by mwacky on 2007-06-03
VMware Server was working fine before some recent upgrades, here is my output running vmware:

```
mwacker@Nelson:~$ sudo vmware
Password:
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

mwacker@Nelson:~$ sudo /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
/usr/share/applications/vmware-console-uri-handler.desktop: warning: The 'Application' category is not defined by the desktop entry specification.  Please use one of "AudioVideo", "Audio", "Video", "Development", "Education", "Game", "Graphics", "Network", "Office", "Settings", "System", "Utility" instead
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
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

```

Seems like the module is not liking the new version of the kernel.   Can't seem to find the fix I need from vmware.com or forums search.  Thanks!

---

### Post by zero244 on 2007-06-03
Yes the kernel update messed up vmware. I think the latest version of vmware 1.04 works with your current kernel.
I am done doing header upgrades.....it has a tendency to break things.
Im running 2.6.17.11 any kernel above 15 seems to break Vmware.
Be sure and unintall the old version of vmware before you try to install the new version. You can save OS virtual machines and copy them back so you dont have to reinstall the virtual machines again.
I keep a compressed copy of a XP virtual machine in case I need one.

---

### Post by Chayak on 2007-06-03
[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto]("http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto")

This worked on a fresh feisty install for me

---

### Post by Atomic Dog on 2007-06-03
Every kernel upgrade will break vmware.  That's why I don't update the kernel unless it is absolutly necessary -breaks too many things.

---

### Post by veloce on 2007-06-03
> **Atomic Dog said:**
> Every kernel upgrade will break vmware.  That's why I don't update the kernel unless it is absolutly necessary -breaks too many things.

Well, if by break you mean that you have to run the configuration utility (vmware-config) each time you upgrade the kernel, then yes (almost).

You may wish to try switching to using the version of vmware server in the repositories.  It will install the stuff appropriate for your kernel.  I am hoping that dependencies are set up so that kernel upgrades will also upgrade vmware server - however, will need to wait until the next kernel uprgrade to see if this is so.

---

### Post by HowardDrake on 2007-06-04
> **veloce said:**
> Well, if by break you mean that you have to run the configuration utility (vmware-config) each time you upgrade the kernel, then yes (almost).

You may wish to try switching to using the version of vmware server in the repositories.  It will install the stuff appropriate for your kernel.  I am hoping that dependencies are set up so that kernel upgrades will also upgrade vmware server - however, will need to wait until the next kernel uprgrade to see if this is so.

Thanks for reminding me, I forgot that I needed to run the update with my VMware workstatiion.

](*,)

---

### Post by mwacky on 2007-06-05
> [http://www.howtoforge.com/ubuntu_fei...e_server_howto](http://www.howtoforge.com/ubuntu_fei...e_server_howto)

This worked on a fresh feisty install for me
__________________
-Chayak

Thanks for your help!  this worked great

---

