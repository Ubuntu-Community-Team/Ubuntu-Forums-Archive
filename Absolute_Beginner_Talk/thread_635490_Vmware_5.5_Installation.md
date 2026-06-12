---
title: "Vmware 5.5 Installation"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by austinderrick2 on 2007-12-08
SIGH.... I ALWAYS have trouble with VMware installation... You'd figure I'd know how to do it by now but...

```

root@Samwise:/home/zug/Desktop/vmware-any-any-update115# uname -r
2.6.22-14-generic

```
```

root@Samwise:/home/zug/Desktop/vmware-any-any-update115# perl runme.pl
Updating /usr/bin/vmware-config.pl ... corrupted
Updating /usr/bin/vmware ... No patch needed/available
Updating /usr/bin/vmnet-bridge ... No patch needed/available
Updating /usr/lib/vmware/bin/vmware-vmx ... No patch needed/available
Updating /usr/lib/vmware/bin-debug/vmware-vmx ... No patch needed/available
VMware modules in "/usr/lib/vmware/modules/source" has been updated.

Before running VMware for the first time after update, you need to configure it 
for your running kernel by invoking the following command: 
"/usr/bin/vmware-config.pl". Do you want this script to invoke the command for 
you now? [yes] 

Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

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
kernel? [/lib/modules/2.6.22-14-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Building for VMware Workstation 5.5.2 or 5.5.3.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config7/vmmon-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config7/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config7/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config7/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config7/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config7/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config7/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config7/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config7/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config7/vmmon-only/common/task.o
cc1plus: warning: command line option "-Wdeclaration-after-statement" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wno-pointer-sign" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-ffreestanding" is valid for C/ObjC but not for C++
/tmp/vmware-config7/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageV321]’:
/tmp/vmware-config7/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageV3]’:
/tmp/vmware-config7/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageGSX1]’:
/tmp/vmware-config7/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageV2]’:
/tmp/vmware-config7/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM_V4(VMDriver*, Vcpuid) [with VMCrossPage = VMCrossPageV4]’:
/tmp/vmware-config7/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMDriver*, Vcpuid)’:
/tmp/vmware-config7/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h: In function ‘void Task_Switch_V45(VMDriver*, Vcpuid)’:
/tmp/vmware-config7/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config7/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function
  CC [M]  /tmp/vmware-config7/vmmon-only/common/vmciContext.o
  CC [M]  /tmp/vmware-config7/vmmon-only/common/vmciDatagram.o
  CC [M]  /tmp/vmware-config7/vmmon-only/common/vmciDriver.o
  CC [M]  /tmp/vmware-config7/vmmon-only/common/vmciDs.o
  CC [M]  /tmp/vmware-config7/vmmon-only/common/vmciGroup.o
  CC [M]  /tmp/vmware-config7/vmmon-only/common/vmciHashtable.o
  CC [M]  /tmp/vmware-config7/vmmon-only/common/vmciProcess.o
  CC [M]  /tmp/vmware-config7/vmmon-only/common/vmciResource.o
  CC [M]  /tmp/vmware-config7/vmmon-only/common/vmciSharedMem.o
  CC [M]  /tmp/vmware-config7/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config7/vmmon-only/vmcore/compat.o
  CC [M]  /tmp/vmware-config7/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config7/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config7/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config7/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config7/vmmon-only'
Unable to make a vmmon module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config7/vmmon.o': -1 Cannot allocate memory
There is probably a slight difference in the kernel configuration between the 
set of C header files you specified and your running kernel.  You may want to 
rebuild a kernel based on that directory, or specify another directory.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

---

### Post by austinderrick2 on 2007-12-11
Bump!


Still broken... and doing the same thing lol... I've tryed the any update patch and I've uninstalled and reinstalled like a billion times... Still no luck :(

---

