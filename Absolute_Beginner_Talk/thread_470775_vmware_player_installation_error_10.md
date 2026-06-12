---
title: "vmware player installation error 10"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-06-11
I tried to install vmplayer using synaptics.

I get error exit status 10:

E: /var/cache/apt/archives/vmware-player_1.0.2-2_i386.deb:  subprocess pre-installation script returned error exit status 10


Any ideas appreciated.

Carl

---

### Post by taurus on 2007-06-11
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get clean
sudo apt-get update
```

---

### Post by cwmoser on 2007-06-11
I did the apt-get clean and then install, but now I get the following error:

E: vmware-player: subprocess post-installation script returned error exit status 1


Any insight?

Carl

---

### Post by skibum58 on 2007-06-11
I am having the same problem with VMWare, getting the exact same error as your follow up post.

I've managed to get the player version 1.0 working but this script keeps trying to force a reinstall.

My score so far:  noob>geek.  
I get depressed when my inner noob wins.  
Not good, help appreciated.

---

### Post by CyberCr33p on 2007-06-12
I have the same problem. If you find a solution please post here.

EDIT:
sudo apt-get clean
sudo apt-get update

solved the problem.

Thanks for the solution.

---

### Post by cwmoser on 2007-06-12
PRESTO:  Got vmware server  installed and built my first virtual machine using a Windows 2000 Professional CDROM.

I got rid of vmware player.  Uninstall and then you have to sudo rm -r /etc/vmware

Then install vmware server.

If you get the "error exit status 1", then do this:

edit /var/lib/dpkg/info/vmware-player.postinst and add a line "exit 0" to the top. The next time, apt-get runs, it will skip the buggy postinst script, believe that VMWare is successfully installed, and update its database.

vmware is worth the trouble so don't give up on it.  I like it.

Carl

---

### Post by burt_57 on 2007-06-12
> **cwmoser said:**
> PRESTO:  Got vmware server  installed and built my first virtual machine using a Windows 2000 Professional CDROM.

I got rid of vmware player.  Uninstall and then you have to sudo rm -r /etc/vmware

Then install vmware server.

If you get the "error exit status 1", then do this:

edit /var/lib/dpkg/info/vmware-player.postinst and add a line "exit 0" to the top. The next time, apt-get runs, it will skip the buggy postinst script, believe that VMWare is successfully installed, and update its database.

vmware is worth the trouble so don't give up on it.  I like it.

Carl
What about Windows Xp?
will it work with it ?

---

### Post by burt_57 on 2007-06-12
Ok i have downloaded VMware.... do I go to install folder?
Then what?
I have reinstall Ubuntu so many time that I want to do it right for once :)

---

### Post by cwmoser on 2007-06-14
The file I downloaded was vmware-server-distrib.

If I recall correctly, when you download and then unpack vmware it gets deposited in /tmp.
If it is not in /tmp, you might have rebooted your PC and it got deleted - just unpack it again.

Look for vmware-install.pl and then execute it per instructions.

Carl

---

### Post by jamaas on 2007-06-14
Carl,

I'm trying this but get the following ... suggestions?  Thanks

Jim 

================

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmmon-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config3/vmmon-only/linux/driver.c:80:
/tmp/vmware-config3/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config3/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config3/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config3/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.


> **cwmoser said:**
> The file I downloaded was vmware-server-distrib.

If I recall correctly, when you download and then unpack vmware it gets deposited in /tmp.
If it is not in /tmp, you might have rebooted your PC and it got deleted - just unpack it again.

Look for vmware-install.pl and then execute it per instructions.

Carl

---

### Post by cwmoser on 2007-06-14
Jim,

I remember now that you need this patch:

"Just an update: I applied the patch [http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz) and was able to successfully install vmware."

I remember installing it now.  Here is the URL mentioning the need for it:

[http://www.vmware.com/community/thread.jspa?threadID=87377&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=87377&tstart=0)

Carl

---

