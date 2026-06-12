---
title: "[SOLVED] A bunch of Warnings when using make.."
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by orionstar on 2008-04-14
For a school homework, all we had to do was copy down some code and make it.

```
root@dan-desktop:/tmp/simple_dummy# make -C /usr/src/linux-2.6.20/ M=`pwd` modules
make: Entering directory `/usr/src/linux-2.6.20'
  CC [M]  /tmp/simple_dummy/sdummy.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: vmlinux - Section mismatch: reference to .init.data:boot_params from .text between '_text' (at offset 0xc0100036) and 'startup_32_smp'
WARNING: vmlinux - Section mismatch: reference to .init.data:boot_params from .text between '_text' (at offset 0xc0100044) and 'startup_32_smp'
WARNING: vmlinux - Section mismatch: reference to .init.data:init_pg_tables_end from .text between '_text' (at offset 0xc01000a6) and 'startup_32_smp'
WARNING: vmlinux - Section mismatch: reference to .init.text:start_kernel from .text between 'is386' (at offset 0xc0100221) and 'check_x87'
WARNING: vmlinux - Section mismatch: reference to .init.text:smp_prepare_cpus from .text between 'init' (at offset 0xc0100437) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:migration_init from .text between 'init' (at offset 0xc010043c) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:spawn_ksoftirqd from .text between 'init' (at offset 0xc0100441) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:spawn_softlockup_task from .text between 'init' (at offset 0xc0100446) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:smp_cpus_done from .text between 'init' (at offset 0xc01004c2) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:sched_init_smp from .text between 'init' (at offset 0xc01004c7) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:cpuset_init_smp from .text between 'init' (at offset 0xc01004cc) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:usermodehelper_init from .text between 'init' (at offset 0xc01004d6) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:driver_init from .text between 'init' (at offset 0xc01004db) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:sysctl_init from .text between 'init' (at offset 0xc01004e1) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.data: from .text between 'init' (at offset 0xc0100503) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.data: from .text between 'init' (at offset 0xc010051c) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:prepare_namespace from .text between 'init' (at offset 0xc01006ff) and 'rest_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:__alloc_bootmem from .text between 'init_gdt' (at offset 0xc010a05b) and 'cpu_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:__alloc_bootmem from .text between 'init_gdt' (at offset 0xc010a071) and 'cpu_init'
WARNING: vmlinux - Section mismatch: reference to .init.text:sysenter_setup from .text between 'identify_cpu' (at offset 0xc010a6cb) and 'display_cacheinfo'
WARNING: vmlinux - Section mismatch: reference to .init.text:mtrr_bp_init from .text between 'identify_cpu' (at offset 0xc010a6d5) and 'display_cacheinfo'
WARNING: vmlinux - Section mismatch: reference to .init.text:trap_init_f00f_bug from .text between 'init_intel' (at offset 0xc010c726) and 'cpuid4_cache_lookup'
WARNING: vmlinux - Section mismatch: reference to .init.data:initkmem_list3 from .text between 'set_up_list3s' (at offset 0xc01706df) and 's_start'
WARNING: vmlinux - Section mismatch: reference to .init.text:eisa_root_register from .text between 'pci_eisa_init' (at offset 0xc0260c6b) and 'virtual_eisa_release'
WARNING: vmlinux - Section mismatch: reference to .init.text:eisa_root_register from .text between 'virtual_eisa_root_init' (at offset 0xc0260ccf) and 'cpufreq_unregister_driver'
WARNING: vmlinux - Section mismatch: reference to .init.text: from .text between 'iret_exc' (at offset 0xc02e43f0) and '_etext'
WARNING: vmlinux - Section mismatch: reference to .init.text:start_kernel from .paravirtprobe between '__start_paravirtprobe' (at offset 0xc03adcf0) and '__stop_paravirtprobe'
  CC      /tmp/simple_dummy/sdummy.mod.o
  LD [M]  /tmp/simple_dummy/sdummy.ko
make: Leaving directory `/usr/src/linux-2.6.20'

```

The code was copied word for word, as was the Makefile (I had to change the first line on that from /* Makefile */ to #Makefile before make wouldn't give me an error of some sorts) 

It seems to have made some sort of module, but when I try running it, nothing happens. It is supposed to printk Hello World when starting and printk Goodbye when exiting. 

```
/* sdummy.c */
#include <linux/init.h>
#include <linux/module.h>
#include <linux/kernel.h>

int sdummy_init(void)
{
printk("<1>Hellow\n");
return 0;
}

void sdummy_exit(void)
{
printk("<1>Goodbye\n");
}

module_init(sdummy_init);
module_exit(sdummy_exit);

```

So, two questions - Should I be worried about the warnings, and what's wrong with the .c file which won't work?

Thanks for your help

---

### Post by marufaberlin on 2008-04-14
No sweat, they're just warnings. If they're not errors and there are no three asterisks, then you're ok. Use```
make -s
``` to suppress them.

---

### Post by marufaberlin on 2008-04-14
you have to insert it with insmod or modprobe and look in dmesg.

---

### Post by orionstar on 2008-04-14
> **marufaberlin said:**
> you have to insert it with insmod or modprobe and look in dmesg.

Oh, I see. 

Where is dmseg (or what is the command in Terminal that brings it up) and;

Is there a way to display the message that appears on dmseg to the console?

---

### Post by Trail on 2008-04-14
Type
```

dmesg

```
on the console.

---

### Post by orionstar on 2008-04-14
> **Trail said:**
> Type
```

dmesg

```
on the console.

And now is there a way to output what appears on dmseg to the console?

> **marufaberlin said:**
> No sweat, they're just warnings. If they're not errors and there are no three asterisks, then you're ok. Use```
make -s
``` to suppress them.

And this is what how I'm using it, I don' think the syntax is right because the warnings still show up.
```
make -s -C /usr\src/linux-2.6.20/ M=`pwd` modules
```

---

### Post by orionstar on 2008-04-14
I think the general rules in forums is not to "bump" a thread unless you weren't the previous poster; but the work is due tomorrow and I need to know.

The problem with make isn't that big of a problem, but I do need to know **how to display the printk message to the console**. 

A site is fine, if it is complicated. 

Thanks.

---

