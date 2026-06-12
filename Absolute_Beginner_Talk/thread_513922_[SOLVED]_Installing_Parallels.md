---
title: "[SOLVED] Installing Parallels"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by Frak on 2007-07-31
I have some time ago purchased Parallels from SWSoft, and installed just fine, but when I run
```
parallels-config
```
I get the error
```
[: 141: ==: unexpected operator
     Compiling Parallels Workstation 2.2 drivers...

Can not compile and/or link drivers. Read /usr/lib/parallels/doc/INSTALL
and follow instructions specified in this document.

Compilation log is available at /usr/lib/parallels/comp.log.7005.error
frak@frak-desktop:~$ sudo parallels-config


[: 141: ==: unexpected operator
     Compiling Parallels Workstation 2.2 drivers...

Can not compile and/or link drivers. Read /usr/lib/parallels/doc/INSTALL
and follow instructions specified in this document.
```

And the error file reads
```
cd drivers && make clean && cd ../
make[1]: Entering directory `/usr/lib/parallels/drivers'
cd drv_main/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_main'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
cd common; rm -rf *.o .*.cmd .tmp_versions; cd ..
cd mm; rm -rf *.o .*.cmd .tmp_versions; cd ..
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_main'
cd hypervisor/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/hypervisor'
/bin/sh: [[: not found
/bin/sh: [[: not found
make[2]: Leaving directory `/usr/lib/parallels/drivers/hypervisor'
cd drv_net/linux/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_net/linux'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_net/linux'
cd drv_virtualnic/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_virtualnic'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_virtualnic'
make[1]: Leaving directory `/usr/lib/parallels/drivers'
cd drivers && make all && cd ../
make[1]: Entering directory `/usr/lib/parallels/drivers'
cd drv_main/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_main'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
cd common; rm -rf *.o .*.cmd .tmp_versions; cd ..
cd mm; rm -rf *.o .*.cmd .tmp_versions; cd ..
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_main'
cd hypervisor/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/hypervisor'
/bin/sh: [[: not found
/bin/sh: [[: not found
make[2]: Leaving directory `/usr/lib/parallels/drivers/hypervisor'
cd drv_net/linux/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_net/linux'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_net/linux'
cd drv_virtualnic/ && make clean && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_virtualnic'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_virtualnic'
cd drv_main/ && make && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_main'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/usr/lib/parallels/drivers/drv_main SRCROOT=/usr/lib/parallels/drivers/drv_main modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/lib/parallels/drivers/drv_main/vmmain.o
In file included from /usr/lib/parallels/drivers/drv_main/vmmain.c:29:
/usr/lib/parallels/drivers/drv_main/vmmain.h:196: warning: ‘kmem_cache_t’ is deprecated
  CC [M]  /usr/lib/parallels/drivers/drv_main/vmproc.o
In file included from /usr/lib/parallels/drivers/drv_main/vmproc.c:24:
/usr/lib/parallels/drivers/drv_main/vmmain.h:196: warning: ‘kmem_cache_t’ is deprecated
  CC [M]  /usr/lib/parallels/drivers/drv_main/device.o
In file included from /usr/lib/parallels/drivers/drv_main/device.c:27:
/usr/lib/parallels/drivers/drv_main/vmmain.h:196: warning: ‘kmem_cache_t’ is deprecated
  CC [M]  /usr/lib/parallels/drivers/drv_main/dwrap.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/intgate.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/ioctls.o
In file included from /usr/lib/parallels/drivers/drv_main/ioctls.c:29:
/usr/lib/parallels/drivers/drv_main/vmmain.h:196: warning: ‘kmem_cache_t’ is deprecated
/usr/lib/parallels/drivers/drv_main/ioctls.c: In function ‘vmMainIoctl’:
/usr/lib/parallels/drivers/drv_main/ioctls.c:170: warning: assignment makes integer from pointer without a cast
  CC [M]  /usr/lib/parallels/drivers/drv_main/monexport.o
In file included from /usr/lib/parallels/drivers/drv_main/monexport.c:23:
/usr/lib/parallels/drivers/drv_main/vmmain.h:196: warning: ‘kmem_cache_t’ is deprecated
  CC [M]  /usr/lib/parallels/drivers/drv_main/mm/manager.o
In file included from /usr/lib/parallels/drivers/drv_main/mm/manager.c:26:
/usr/lib/parallels/drivers/drv_main/vmmain.h:196: warning: ‘kmem_cache_t’ is deprecated
  CC [M]  /usr/lib/parallels/drivers/drv_main/mm/pages.o
In file included from /usr/lib/parallels/drivers/drv_main/mm/pages.c:26:
/usr/lib/parallels/drivers/drv_main/vmmain.h:196: warning: ‘kmem_cache_t’ is deprecated
  CC [M]  /usr/lib/parallels/drivers/drv_main/mm/collector.o
In file included from /usr/lib/parallels/drivers/drv_main/mm/collector.c:27:
/usr/lib/parallels/drivers/drv_main/vmmain.h:196: warning: ‘kmem_cache_t’ is deprecated
  CC [M]  /usr/lib/parallels/drivers/drv_main/mm/monmem.o
In file included from /usr/lib/parallels/drivers/drv_main/mm/monmem.c:26:
/usr/lib/parallels/drivers/drv_main/vmmain.h:196: warning: ‘kmem_cache_t’ is deprecated
  CC [M]  /usr/lib/parallels/drivers/drv_main/mm/wset.o
In file included from /usr/lib/parallels/drivers/drv_main/mm/wset.c:23:
/usr/lib/parallels/drivers/drv_main/vmmain.h:196: warning: ‘kmem_cache_t’ is deprecated
  CC [M]  /usr/lib/parallels/drivers/drv_main/common/bma.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/common/logging.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/common/timer.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/common/idata.o
In file included from /usr/lib/parallels/drivers/drv_main/common/idata.c:24:
/usr/lib/parallels/drivers/drv_main/vmmain.h:196: warning: ‘kmem_cache_t’ is deprecated
  CC [M]  /usr/lib/parallels/drivers/drv_main/common/utils.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/common/md5.o
In file included from /usr/lib/parallels/drivers/drv_main/common/md5.c:28:
/usr/lib/parallels/drivers/drv_main/vmmain.h:196: warning: ‘kmem_cache_t’ is deprecated
  LD [M]  /usr/lib/parallels/drivers/drv_main/vm-main.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "hypervisorPresentInSystem" [/usr/lib/parallels/drivers/drv_main/vm-main.ko] undefined!
WARNING: "appDecCounter" [/usr/lib/parallels/drivers/drv_main/vm-main.ko] undefined!
WARNING: "appIncCounter" [/usr/lib/parallels/drivers/drv_main/vm-main.ko] undefined!
  CC      /usr/lib/parallels/drivers/drv_main/vm-main.mod.o
  LD [M]  /usr/lib/parallels/drivers/drv_main/vm-main.ko
make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_main'
cd hypervisor/ && make && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/hypervisor'
/bin/sh: [[: not found
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/usr/lib/parallels/drivers/hypervisor SRCROOT=/usr/lib/parallels/drivers/hypervisor modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/lib/parallels/drivers/hypervisor/hypmain.o
In file included from /usr/lib/parallels/drivers/hypervisor/hypmain.c:28:
/usr/lib/parallels/drivers/hypervisor/hypervisor.h:130: warning: ‘kmem_cache_t’ is deprecated
  CC [M]  /usr/lib/parallels/drivers/hypervisor/hdevice.o
In file included from /usr/lib/parallels/drivers/hypervisor/hdevice.c:30:
/usr/lib/parallels/drivers/hypervisor/hypervisor.h:130: warning: ‘kmem_cache_t’ is deprecated
  CC [M]  /usr/lib/parallels/drivers/hypervisor/hioctls.o
In file included from /usr/lib/parallels/drivers/hypervisor/hioctls.c:32:
/usr/lib/parallels/drivers/hypervisor/hypervisor.h:130: warning: ‘kmem_cache_t’ is deprecated
/usr/lib/parallels/drivers/hypervisor/hioctls.c: In function ‘hypIoctl’:
/usr/lib/parallels/drivers/hypervisor/hioctls.c:59: warning: unused variable ‘iVtxSupport’
  CC [M]  /usr/lib/parallels/drivers/hypervisor/hypvmstate.o
In file included from /usr/lib/parallels/drivers/hypervisor/hypvmstate.c:26:
/usr/lib/parallels/drivers/hypervisor/hypervisor.h:130: warning: ‘kmem_cache_t’ is deprecated
/usr/lib/parallels/drivers/hypervisor/hypvmstate.c: In function ‘hypVMStateAllocate’:
/usr/lib/parallels/drivers/hypervisor/hypvmstate.c:81: warning: passing argument 1 of ‘mmEnableExecution’ makes integer from pointer without a cast
  CC [M]  /usr/lib/parallels/drivers/hypervisor/logging.o
  CC [M]  /usr/lib/parallels/drivers/hypervisor/pages.o
In file included from /usr/lib/parallels/drivers/hypervisor/pages.c:26:
/usr/lib/parallels/drivers/hypervisor/../drv_main/vmmain.h:196: warning: ‘kmem_cache_t’ is deprecated
  CC [M]  /usr/lib/parallels/drivers/hypervisor/utils.o
  CC [M]  /usr/lib/parallels/drivers/hypervisor/md5.o
In file included from /usr/lib/parallels/drivers/hypervisor/md5.c:28:
/usr/lib/parallels/drivers/hypervisor/../drv_main/vmmain.h:196: warning: ‘kmem_cache_t’ is deprecated
  CC [M]  /usr/lib/parallels/drivers/hypervisor/vtx_init.o
In file included from /usr/lib/parallels/drivers/hypervisor/vtx_init.c:25:
/usr/lib/parallels/drivers/hypervisor/hypervisor.h:130: warning: ‘kmem_cache_t’ is deprecated
  CC [M]  /usr/lib/parallels/drivers/hypervisor/svm_init.o
In file included from /usr/lib/parallels/drivers/hypervisor/svm_init.c:25:
/usr/lib/parallels/drivers/hypervisor/hypervisor.h:130: warning: ‘kmem_cache_t’ is deprecated
  LD [M]  /usr/lib/parallels/drivers/hypervisor/hypervisor.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /usr/lib/parallels/drivers/hypervisor/.interrupt.o.cmd for /usr/lib/parallels/drivers/hypervisor/interrupt.o
  CC      /usr/lib/parallels/drivers/hypervisor/hypervisor.mod.o
  LD [M]  /usr/lib/parallels/drivers/hypervisor/hypervisor.ko
make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[2]: Leaving directory `/usr/lib/parallels/drivers/hypervisor'
cd drv_net/linux/ && make && cd ..
make[2]: Entering directory `/usr/lib/parallels/drivers/drv_net/linux'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/usr/lib/parallels/drivers/drv_net/linux SRCROOT=/usr/lib/parallels/drivers/drv_net/linux modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/lib/parallels/drivers/drv_net/linux/prlnet.o
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c: In function ‘prlnet_recv’:
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c:884: error: ‘CHECKSUM_HW’ undeclared (first use in this function)
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c:884: error: (Each undeclared identifier is reported only once
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c:884: error: for each function it appears in.)
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c: In function ‘hw_bind’:
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c:1011: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c:1023: warning: assignment from incompatible pointer type
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c: In function ‘prlnet_nopage’:
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c:1169: error: dereferencing pointer to incomplete type
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c:1175: error: dereferencing pointer to incomplete type
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c:1177: error: dereferencing pointer to incomplete type
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c:1191: error: ‘VM_FAULT_MINOR’ undeclared (first use in this function)
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c:1202: warning: implicit declaration of function ‘vmalloc_to_page’
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c:1202: warning: assignment makes pointer from integer without a cast
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c:1204: warning: implicit declaration of function ‘get_page’
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c: At top level:
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c:1208: error: variable ‘prlnet_vmops’ has initializer but incomplete type
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c:1209: error: unknown field ‘nopage’ specified in initializer
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c:1210: warning: excess elements in struct initializer
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c:1210: warning: (near initialization for ‘prlnet_vmops’)
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c: In function ‘prlnet_mmap’:
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c:1219: error: dereferencing pointer to incomplete type
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c:1223: error: dereferencing pointer to incomplete type
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c:1223: error: dereferencing pointer to incomplete type
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c:1229: error: dereferencing pointer to incomplete type
/usr/lib/parallels/drivers/drv_net/linux/prlnet.c:1230: error: dereferencing pointer to incomplete type
make[4]: *** [/usr/lib/parallels/drivers/drv_net/linux/prlnet.o] Error 1
make[3]: *** [_module_/usr/lib/parallels/drivers/drv_net/linux] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/lib/parallels/drivers/drv_net/linux'
make[1]: *** [vmbridge] Error 2
make[1]: Leaving directory `/usr/lib/parallels/drivers'
make: *** [build] Error 2
```

Does anybody have any suggestions on how to successfully complete the installation of this program?
Thanks.

---

### Post by Frak on 2007-07-31
I fixed it and have writien a Howto, just waiting for confirmation from Administration.
[http://ubuntuforums.org/showthread.php?t=513953](http://ubuntuforums.org/showthread.php?t=513953)

---

### Post by Trosky on 2007-08-16
Hello, I follow your instructions in the post, but I got a problem, I am using the kernel 2.6.22-9 

 ```
cd drivers && make clean && cd ../
make[1]: se ingresa al directorio `/usr/lib/parallels/drivers'
cd drv_main/ && make clean && cd ..
make[2]: se ingresa al directorio `/usr/lib/parallels/drivers/drv_main'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
cd common; rm -rf *.o .*.cmd .tmp_versions; cd ..
cd mm; rm -rf *.o .*.cmd .tmp_versions; cd ..
make[2]: se sale del directorio `/usr/lib/parallels/drivers/drv_main'
cd hypervisor/ && make clean && cd ..
make[2]: se ingresa al directorio `/usr/lib/parallels/drivers/hypervisor'
/bin/sh: [[: not found
/bin/sh: [[: not found
make[2]: se sale del directorio `/usr/lib/parallels/drivers/hypervisor'
cd drv_net/linux/ && make clean && cd ..
make[2]: se ingresa al directorio `/usr/lib/parallels/drivers/drv_net/linux'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
make[2]: se sale del directorio `/usr/lib/parallels/drivers/drv_net/linux'
cd drv_virtualnic/ && make clean && cd ..
make[2]: se ingresa al directorio `/usr/lib/parallels/drivers/drv_virtualnic'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
make[2]: se sale del directorio `/usr/lib/parallels/drivers/drv_virtualnic'
make[1]: se sale del directorio `/usr/lib/parallels/drivers'
cd drivers && make all && cd ../
make[1]: se ingresa al directorio `/usr/lib/parallels/drivers'
cd drv_main/ && make clean && cd ..
make[2]: se ingresa al directorio `/usr/lib/parallels/drivers/drv_main'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
cd common; rm -rf *.o .*.cmd .tmp_versions; cd ..
cd mm; rm -rf *.o .*.cmd .tmp_versions; cd ..
make[2]: se sale del directorio `/usr/lib/parallels/drivers/drv_main'
cd hypervisor/ && make clean && cd ..
make[2]: se ingresa al directorio `/usr/lib/parallels/drivers/hypervisor'
/bin/sh: [[: not found
/bin/sh: [[: not found
make[2]: se sale del directorio `/usr/lib/parallels/drivers/hypervisor'
cd drv_net/linux/ && make clean && cd ..
make[2]: se ingresa al directorio `/usr/lib/parallels/drivers/drv_net/linux'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
make[2]: se sale del directorio `/usr/lib/parallels/drivers/drv_net/linux'
cd drv_virtualnic/ && make clean && cd ..
make[2]: se ingresa al directorio `/usr/lib/parallels/drivers/drv_virtualnic'
rm -rf *.o *.ko .*.cmd *.mod.c .tmp_versions
make[2]: se sale del directorio `/usr/lib/parallels/drivers/drv_virtualnic'
cd drv_main/ && make && cd ..
make[2]: se ingresa al directorio `/usr/lib/parallels/drivers/drv_main'
make -C /lib/modules/2.6.22-9-generic/build SUBDIRS=/usr/lib/parallels/drivers/drv_main SRCROOT=/usr/lib/parallels/drivers/drv_main modules
make[3]: se ingresa al directorio `/usr/src/linux-headers-2.6.22-9-generic'
  CC [M]  /usr/lib/parallels/drivers/drv_main/vmmain.o
In file included from /usr/lib/parallels/drivers/drv_main/vmmain.c:29:
/usr/lib/parallels/drivers/drv_main/vmmain.h:196: aviso: ‘kmem_cache_t’ es obsoleto
  CC [M]  /usr/lib/parallels/drivers/drv_main/vmproc.o
In file included from /usr/lib/parallels/drivers/drv_main/vmproc.c:24:
/usr/lib/parallels/drivers/drv_main/vmmain.h:196: aviso: ‘kmem_cache_t’ es obsoleto
  CC [M]  /usr/lib/parallels/drivers/drv_main/device.o
In file included from /usr/lib/parallels/drivers/drv_main/device.c:27:
/usr/lib/parallels/drivers/drv_main/vmmain.h:196: aviso: ‘kmem_cache_t’ es obsoleto
  CC [M]  /usr/lib/parallels/drivers/drv_main/dwrap.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/intgate.o
  CC [M]  /usr/lib/parallels/drivers/drv_main/ioctls.o
In file included from /usr/lib/parallels/drivers/drv_main/ioctls.c:29:
/usr/lib/parallels/drivers/drv_main/vmmain.h:196: aviso: ‘kmem_cache_t’ es obsoleto
/usr/lib/parallels/drivers/drv_main/ioctls.c: En la función ‘vmMainIoctl’:
/usr/lib/parallels/drivers/drv_main/ioctls.c:170: aviso: la asignación crea un entero desde un puntero sin una conversión
  CC [M]  /usr/lib/parallels/drivers/drv_main/monexport.o
In file included from /usr/lib/parallels/drivers/drv_main/monexport.c:23:
/usr/lib/parallels/drivers/drv_main/vmmain.h:196: aviso: ‘kmem_cache_t’ es obsoleto
  CC [M]  /usr/lib/parallels/drivers/drv_main/mm/manager.o
In file included from /usr/lib/parallels/drivers/drv_main/mm/manager.c:26:
/usr/lib/parallels/drivers/drv_main/vmmain.h:196: aviso: ‘kmem_cache_t’ es obsoleto
/usr/lib/parallels/drivers/drv_main/mm/manager.c: En la función ‘mmInitPMM’:
/usr/lib/parallels/drivers/drv_main/mm/manager.c:233: error: puntero deferenciado a tipo de dato incompleto
make[4]: *** [/usr/lib/parallels/drivers/drv_main/mm/manager.o] Error 1
make[3]: *** [_module_/usr/lib/parallels/drivers/drv_main] Error 2
make[3]: se sale del directorio `/usr/src/linux-headers-2.6.22-9-generic'
make[2]: *** [all] Error 2
make[2]: se sale del directorio `/usr/lib/parallels/drivers/drv_main'
make[1]: *** [vmmain] Error 2
make[1]: se sale del directorio `/usr/lib/parallels/drivers'
make: *** [build] Error 2
```

---

### Post by Frak on 2007-08-16
Are you running Feisty or Gutsy?

---

### Post by Trosky on 2007-08-16
Feisty, but I installed the kernel 2.6.22-9 from Gutsy repositories

---

