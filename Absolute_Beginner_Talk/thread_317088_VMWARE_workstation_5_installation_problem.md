---
title: "VMWARE workstation 5 installation problem"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by lucaslucas on 2006-12-11
Hi everibody. I am trying to install VMWARE 5 on ubuntu 6.02. I follow previous threads but at the end I got all this errors. I am newbie and I really need vmware for my work. Any help is welcome.

Lucas


Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel?
[/lib/modules/2.6.15-27-amd64-generic/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.15-27-amd64-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-amd64-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
/tmp/vmware-config1/vmmon-only/linux/driver.c:33:25: error: asm/ioctl32.h: No such file or directory
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:24,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:44:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_defs.h:208:5: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config1/vmmon-only/./include/vcpuset.h:56,
                 from /tmp/vmware-config1/vmmon-only/./include/modulecall.h:23,
                 from /tmp/vmware-config1/vmmon-only/./common/vmx86.h:18,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:45:
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:54:5: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config1/vmmon-only/./include/vm_asm.h:23,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:48:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_asm.h:48:5: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function ‘register_ioctl32_handlers’:
/tmp/vmware-config1/vmmon-only/linux/driver.c:222: warning: implicit declaration of function ‘register_ioctl32_conversion’
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function ‘unregister_ioctl32_handlers’:
/tmp/vmware-config1/vmmon-only/linux/driver.c:248: warning: implicit declaration of function ‘unregister_ioctl32_conversion’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-amd64-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

---

### Post by chalex on 2006-12-11
What do you mean by Ubuntu 6.02?  

I wrote this post when I was installing VMWare, perhaps it will help: [http://yalb.net/wp/?p=60](http://yalb.net/wp/?p=60)

---

### Post by lucaslucas on 2006-12-12
Sorry, wrong typing, I meant ubuntu 6.06 LTS.

It did not solve the problem anyway, I have follow your suggestions.

Thanks

Adrian

---

### Post by hyper_ch on 2006-12-12
```

sudo apt-get install linux-headers-`uname -r` build-essential xinetd

```

This will install all needed dependencies! If there are still some problems install gcc-3.4.

```

sudo apt-get install gcc-3.4

```

---

### Post by lucaslucas on 2006-12-18
Thanks, I have done what said, as it was already suggested by others, but I still get the same  problems I posted last week.

Adrian

---

### Post by ture_atlantis on 2006-12-19
i got this same error, i had to do a

sudo apt-get install ia32-libs

and it worked fine after that.  i got that clue from this web page.... 

[http://users.piuha.net/martti/comp/ubuntu/server.html#6](http://users.piuha.net/martti/comp/ubuntu/server.html#6)


hope that helps

---

### Post by lucaslucas on 2006-12-19
Thanks, I had already done that too.
By now I installed the Reader, that is free and is working.

But I can only read not generate new things or improved, etc..

Thanks anyway

Adrian

---

