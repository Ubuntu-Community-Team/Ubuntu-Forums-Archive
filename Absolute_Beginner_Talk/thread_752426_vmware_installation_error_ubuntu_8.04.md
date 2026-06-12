---
title: "vmware installation error ubuntu 8.04"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by DanFlo on 2008-04-11
i am trying to install VMware-server-1.0.5 on ubuntu 8.04
please advice.
thank you
```

Thank you.

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config5/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config5/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config5/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config5/vmmon-only/linux/driver.c:48:
/tmp/vmware-config5/vmmon-only/./include/vm_basic_types.h:161: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config5/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config5/vmmon-only/linux/driver.c:49:
/tmp/vmware-config5/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config5/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config5/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config5/vmmon-only/linux/driver.c:49:
/tmp/vmware-config5/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config5/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config5/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config5/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config5/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config5/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config5/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config5/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


```

---

### Post by Gulyan on 2008-04-11
are you using the package manager? :confused:

---

### Post by saj0577 on 2008-04-11
In the future try to use the development forum for the projects still in beta/alpha. :)

What did you use to install it?

---

### Post by DanFlo on 2008-04-11
sorry i am new around here!
i used the archive provided by vmware official site!
i unpacked it and gave the command :  sudo ./vmware-install.pl

---

### Post by saj0577 on 2008-04-11
No problem about being new we all where once m8
You thought about VirtualBox its the same and its in the repos(big database of programs that are easy to install :))

Saj

---

### Post by DanFlo on 2008-04-11
> **saj0577 said:**
> No problem about being new we all where once m8
You thought about VirtualBox its the same and its in the repos(big database of programs that are easy to install :))

Saj

thanks for the welcome.
i actually installed virtualbox with usb support but i didn't manage to get my printer working via usb.
i followed this guide [http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html]("http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html")

---

### Post by bradwilliamson on 2008-04-11
you will probably need the vmware-any-any patch applied to the vmware-server-distrib directory, I just posted nearly the same thing yesterday [here]("http://ubuntuforums.org/showthread.php?t=751468") so I won't copy and paste it again.

Newer kernels typically need the any-any patch to get past some rudimentary version testing that vmware does during the install.

Since it is blowing up building the vmmon module, this is my recollection of where it died on Edgy.

If you're past that, then I'll say that I've also had issues with gcc3.4-base and gcc4, and/or multiple sets of kernel-header source code in /usr/src and the wrong one is linked to /usr/src/linux.

I haven't tried 8.04 for VMWare though, I stick with Dapper for servers and don't run vmware on desktops, so there may be something else afoot here.

If you've already done the above, post back and I'll dig out my notes on this.

Brad

---

### Post by Soundman2 on 2008-04-11
DanFlo,

I believe there is more to getting VMware Server 1.x to install on Ubuntu 8.04 than just the any-any patch.  I read several issues on the VMware forums about it some changes in kernel driver interfaces that were made for Linux Kernels versions above 2.6.22  (Ubuntu 8.04 uses 2.6.25).

A few people had some experimental patches out on the VMware forums that you could search for.  However, VMware Server 2.0 Beta 2 already has what it needs to install with Ubuntu 8.04.  So, rather than trying to get VMware 1.05 working, I just installed VMware 2.0 Beta 2, and it is working fine for me.   YMMV.

The installation went OK except that the new vmsock module failed to build.  But that is not essential - it just means that you don't get the new sockets interface that VMware added in Server 2.0 for communication between Guest & Host.  That feature was not present in VMware Server 1.x anyway, so it is not a loss at this point.

Be aware, however, that some users really dislike VMware Server 2.0 Beta's new web-based management interface.  I'm not real fond of it myself, but it isn't too bad.

So, choose for yourself..... You can probably get 1.05 working if you search for "Ubuntu 8.04" or "hardy" or "2.6.25" on the VMware Community Forums.

Regards,
Soundman2

---

