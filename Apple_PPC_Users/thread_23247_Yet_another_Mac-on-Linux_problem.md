---
title: "Yet another Mac-on-Linux problem"
date: 2005-03-31
forum: Apple PPC Users
---

### Post by leaded on 2005-03-31
I've been following the instructions in [the wiki](http://www.ubuntulinux.org/wiki/MacOnLinuxHowto/) and I'm stuck.

I'm up to where I build the kernel module. Here's some output. I would've only included the errors, but I don't know if these warnings are important or not...```
alan@ubuntu:/usr/src/modules/mol$ sudo debian/rules build
m4 -DKVERS="2.6.10-4-powerpc" -DKSRC="/usr/src/linux-headers-2.6.10-4-powerpc" - DKEMAIL="your@email.address" -DKMAINT="Your Name" -DKDREV="ubuntu0" -DDEBDATE="T hu, 31 Mar 2005 22:45:32 -0500" debian/control.m4 > debian/control
m4 -DKVERS="2.6.10-4-powerpc" -DKSRC="/usr/src/linux-headers-2.6.10-4-powerpc" - DKEMAIL="your@email.address" -DKMAINT="Your Name" -DKDREV="ubuntu0" -DDEBDATE="T hu, 31 Mar 2005 22:45:32 -0500" debian/changelog.m4 > debian/changelog
touch configure-stamp
dh_testdir
/usr/bin/make
make[1]: Entering directory `/usr/src/modules/mol'
/usr/bin/make -C src/kmod
make[2]: Entering directory `/usr/src/modules/mol/src/kmod'
+ Entering Linux
  CC [M]  /usr/src/modules/mol/src/kmod/Linux/../build/_kuname.o
  CC [M]  /usr/src/modules/mol/src/kmod/Linux/../build/_fault.o
In file included from /usr/src/modules/mol/src/kmod/build/_fault.c:18:
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `tophys_mol':
/usr/src/modules/mol/src/kmod/build/alloc.h:61: warning: implicit declaration of  function `virt_to_phys'
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `map_phys_range':
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: implicit declaration of  function `phys_to_virt'
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: assignment makes pointe r from integer without a cast
/usr/src/modules/mol/src/kmod/build/_fault.c: In function `get_phys_page':
/usr/src/modules/mol/src/kmod/build/_fault.c:80: warning: assignment makes point er from integer without a cast
/usr/src/modules/mol/src/kmod/build/_fault.c: In function `dbg_get_linux_page':
/usr/src/modules/mol/src/kmod/build/_fault.c:141: warning: assignment makes poin ter from integer without a cast
  CC [M]  /usr/src/modules/mol/src/kmod/Linux/../build/_dev.o
In file included from /usr/src/modules/mol/src/kmod/build/kernel_vars.h:34,
                 from /usr/src/modules/mol/src/kmod/build/_dev.c:25:
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `tophys_mol':
/usr/src/modules/mol/src/kmod/build/alloc.h:61: warning: implicit declaration of  function `virt_to_phys'
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `map_phys_range':
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: implicit declaration of  function `phys_to_virt'
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: assignment makes pointe r from integer without a cast
/usr/src/modules/mol/src/kmod/build/_dev.c: In function `arch_handle_ioctl':
/usr/src/modules/mol/src/kmod/build/_dev.c:184: warning: implicit declaration of  function `ioremap'
/usr/src/modules/mol/src/kmod/build/_dev.c:184: warning: assignment makes pointe r from integer without a cast
/usr/src/modules/mol/src/kmod/build/_dev.c:186: warning: implicit declaration of  function `iounmap'
  CC [M]  /usr/src/modules/mol/src/kmod/Linux/../build/_misc.o
In file included from /usr/src/modules/mol/src/kmod/build/kernel_vars.h:34,
                 from /usr/src/modules/mol/src/kmod/build/_misc.c:23:
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `tophys_mol':
/usr/src/modules/mol/src/kmod/build/alloc.h:61: warning: implicit declaration of  function `virt_to_phys'
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `map_phys_range':
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: implicit declaration of  function `phys_to_virt'
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: assignment makes pointe r from integer without a cast
  CC [M]  /usr/src/modules/mol/src/kmod/Linux/../build/_mmu.o
In file included from /usr/src/modules/mol/src/kmod/build/_mmu.c:18:
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `tophys_mol':
/usr/src/modules/mol/src/kmod/build/alloc.h:61: warning: implicit declaration of  function `virt_to_phys'
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `map_phys_range':
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: implicit declaration of  function `phys_to_virt'
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: assignment makes pointe r from integer without a cast
  CC [M]  /usr/src/modules/mol/src/kmod/Linux/../build/init.o
In file included from /usr/src/modules/mol/src/kmod/build/init.c:18:
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `tophys_mol':
/usr/src/modules/mol/src/kmod/build/alloc.h:61: warning: implicit declaration of  function `virt_to_phys'
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `map_phys_range':
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: implicit declaration of  function `phys_to_virt'
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: assignment makes pointe r from integer without a cast
  CC [M]  /usr/src/modules/mol/src/kmod/Linux/../build/emu.o
In file included from /usr/src/modules/mol/src/kmod/build/emu.c:18:
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `tophys_mol':
/usr/src/modules/mol/src/kmod/build/alloc.h:61: warning: implicit declaration of  function `virt_to_phys'
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `map_phys_range':
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: implicit declaration of  function `phys_to_virt'
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: assignment makes pointe r from integer without a cast
  CC [M]  /usr/src/modules/mol/src/kmod/Linux/../build/mmu.o
In file included from /usr/src/modules/mol/src/kmod/build/mmu.c:18:
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `tophys_mol':
/usr/src/modules/mol/src/kmod/build/alloc.h:61: warning: implicit declaration of  function `virt_to_phys'
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `map_phys_range':
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: implicit declaration of  function `phys_to_virt'
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: assignment makes pointe r from integer without a cast
  CC [M]  /usr/src/modules/mol/src/kmod/Linux/../build/mmu_fb.o
In file included from /usr/src/modules/mol/src/kmod/build/mmu_fb.c:18:
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `tophys_mol':
/usr/src/modules/mol/src/kmod/build/alloc.h:61: warning: implicit declaration of  function `virt_to_phys'
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `map_phys_range':
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: implicit declaration of  function `phys_to_virt'
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: assignment makes pointe r from integer without a cast
  CC [M]  /usr/src/modules/mol/src/kmod/Linux/../build/mmu_io.o
In file included from /usr/src/modules/mol/src/kmod/build/mmu_io.c:19:
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `tophys_mol':
/usr/src/modules/mol/src/kmod/build/alloc.h:61: warning: implicit declaration of  function `virt_to_phys'
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `map_phys_range':
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: implicit declaration of  function `phys_to_virt'
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: assignment makes pointe r from integer without a cast
  CC [M]  /usr/src/modules/mol/src/kmod/Linux/../build/mmu_tracker.o
In file included from /usr/src/modules/mol/src/kmod/build/mmu_tracker.c:18:
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `tophys_mol':
/usr/src/modules/mol/src/kmod/build/alloc.h:61: warning: implicit declaration of function `virt_to_phys'
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `map_phys_range':
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: implicit declaration of function `phys_to_virt'
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: assignment makes pointer from integer without a cast  CC [M]  /usr/src/modules/mol/src/kmod/Linux/../build/skiplist.o
  CC [M]  /usr/src/modules/mol/src/kmod/Linux/../build/mtable.o
In file included from /usr/src/modules/mol/src/kmod/build/mtable.c:21:
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `tophys_mol':
/usr/src/modules/mol/src/kmod/build/alloc.h:61: warning: implicit declaration of function `virt_to_phys'
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `map_phys_range':
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: implicit declaration of function `phys_to_virt'
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: assignment makes pointer from integer without a cast  CC [M]  /usr/src/modules/mol/src/kmod/Linux/../build/fault.o
In file included from /usr/src/modules/mol/src/kmod/build/fault.c:18:
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `tophys_mol':
/usr/src/modules/mol/src/kmod/build/alloc.h:61: warning: implicit declaration of function `virt_to_phys'
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `map_phys_range':
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: implicit declaration of function `phys_to_virt'
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: assignment makes pointer from integer without a cast/usr/src/modules/mol/src/kmod/build/fault.c: In function `dsi_exception':
/usr/src/modules/mol/src/kmod/build/fault.c:513: warning: assignment makes pointer from integer without a cast
/usr/src/modules/mol/src/kmod/build/fault.c: In function `isi_exception':
/usr/src/modules/mol/src/kmod/build/fault.c:535: warning: assignment makes pointer from integer without a cast
  CC [M]  /usr/src/modules/mol/src/kmod/Linux/../build/context.o
In file included from /usr/src/modules/mol/src/kmod/build/context.c:18:
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `tophys_mol':
/usr/src/modules/mol/src/kmod/build/alloc.h:61: warning: implicit declaration of function `virt_to_phys'
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `map_phys_range':
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: implicit declaration of function `phys_to_virt'
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: assignment makes pointer from integer without a cast/usr/src/modules/mol/src/kmod/build/context.c: In function `flush_all_PTEs':
/usr/src/modules/mol/src/kmod/build/context.c:34: warning: initialization makes pointer from integer without a cast
  CC [M]  /usr/src/modules/mol/src/kmod/Linux/../build/ptaccess.o
In file included from /usr/src/modules/mol/src/kmod/build/kernel_vars.h:34,
                 from /usr/src/modules/mol/src/kmod/build/mmu.h:21,
                 from /usr/src/modules/mol/src/kmod/build/ptaccess.c:18:
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `tophys_mol':
/usr/src/modules/mol/src/kmod/build/alloc.h:61: warning: implicit declaration of function `virt_to_phys'
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `map_phys_range':
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: implicit declaration of function `phys_to_virt'
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: assignment makes pointer from integer without a cast  CC [M]  /usr/src/modules/mol/src/kmod/Linux/../build/misc.o
In file included from /usr/src/modules/mol/src/kmod/build/kernel_vars.h:34,
                 from /usr/src/modules/mol/src/kmod/build/mmu.h:21,
                 from /usr/src/modules/mol/src/kmod/build/misc.c:19:
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `tophys_mol':
/usr/src/modules/mol/src/kmod/build/alloc.h:61: warning: implicit declaration of function `virt_to_phys'
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `map_phys_range':
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: implicit declaration of function `phys_to_virt'
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: assignment makes pointer from integer without a castIn file included from /usr/src/modules/mol/src/kmod/build/kernel_vars.h:34,
                 from /usr/src/modules/mol/src/kmod/build/tmp-offsets.c:13:
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `tophys_mol':
/usr/src/modules/mol/src/kmod/build/alloc.h:61: warning: implicit declaration of function `virt_to_phys'
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `map_phys_range':
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: implicit declaration of function `phys_to_virt'
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: assignment makes pointer from integer without a cast  AS [x]   /usr/src/modules/mol/src/kmod/Linux/../build/_traps.o
  CC [M]  /usr/src/modules/mol/src/kmod/Linux/../build/hook.o
In file included from /usr/src/modules/mol/src/kmod/build/hook.c:18:
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `tophys_mol':
/usr/src/modules/mol/src/kmod/build/alloc.h:61: warning: implicit declaration of function `virt_to_phys'
/usr/src/modules/mol/src/kmod/build/alloc.h: In function `map_phys_range':
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: implicit declaration of function `phys_to_virt'
/usr/src/modules/mol/src/kmod/build/alloc.h:68: warning: assignment makes pointer from integer without a cast  AS [x]   /usr/src/modules/mol/src/kmod/Linux/../build/_actions.o
  CC [M]  /usr/src/modules/mol/src/kmod/Linux/../build/_performance.o
  LD [M]  /usr/src/modules/mol/src/kmod/Linux/../build/mol.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /usr/src/modules/mol/src/kmod/Linux/../build/._traps.o.cmd for /usr/src/modules/mol/src/kmod/Linux/../build/_traps.o
*** Warning: "phys_to_virt" [/usr/src/modules/mol/src/kmod/Linux/../build/mol.ko] undefined!
*** Warning: "virt_to_phys" [/usr/src/modules/mol/src/kmod/Linux/../build/mol.ko] undefined!
  CC      /usr/src/modules/mol/src/kmod/Linux/../build/_kuname.mod.o
  LD [M]  /usr/src/modules/mol/src/kmod/Linux/../build/_kuname.ko
  CC      /usr/src/modules/mol/src/kmod/Linux/../build/mol.mod.o
  LD [M]  /usr/src/modules/mol/src/kmod/Linux/../build/mol.ko
    Kernel source                 : /usr/src/linux-headers-2.6.10-4-powerpc
    Module compiled for           : 2.6.10-4-powerpc
    Running kernel                : 2.6.10-4-powerpc
install -d ../../../mollib/modules/`cat ../build/.kuname`
ln -f ../build/mol.ko ../../../mollib/modules/`cat ../build/.kuname`/
make[2]: Leaving directory `/usr/src/modules/mol/src/kmod'
/usr/bin/make -C src/netdriver
make[2]: Entering directory `/usr/src/modules/mol/src/netdriver'
  CC [M]  /usr/src/modules/mol/src/netdriver/build/kuname.o
strings /usr/src/modules/mol/src/netdriver/build/kuname.o | grep -- '-MAGIC-' | sed -e s/-MAGIC-// > /usr/src/modules/mol/src/netdriver/build/.kuname
  CC [M]  /usr/src/modules/mol/src/netdriver/build/sheep.o
/usr/src/modules/mol/src/netdriver/build/sheep.c: In function `sheep_net_receiver':
/usr/src/modules/mol/src/netdriver/build/sheep.c:156: error: union has no member named `ethernet'
/usr/src/modules/mol/src/netdriver/build/sheep.c:170: error: union has no member named `ethernet'
/usr/src/modules/mol/src/netdriver/build/sheep.c:181: error: union has no member named `ethernet'
/usr/src/modules/mol/src/netdriver/build/sheep.c:185: error: union has no member named `ethernet'
/usr/src/modules/mol/src/netdriver/build/sheep.c:190: error: union has no member named `ethernet'
/usr/src/modules/mol/src/netdriver/build/sheep.c:218: error: union has no member named `ethernet'
/usr/src/modules/mol/src/netdriver/build/sheep.c: In function `sheep_net_open':
/usr/src/modules/mol/src/netdriver/build/sheep.c:252: warning: use of cast expressions as lvalues is deprecated
/usr/src/modules/mol/src/netdriver/build/sheep.c: In function `sheep_net_writev':
/usr/src/modules/mol/src/netdriver/build/sheep.c:399: error: union has no member named `ethernet'
make[4]: *** [/usr/src/modules/mol/src/netdriver/build/sheep.o] Error 1
make[3]: *** [_module_/usr/src/modules/mol/src/netdriver/build] Error 2
make[2]: Leaving directory `/usr/src/modules/mol/src/netdriver'
make[1]: Leaving directory `/usr/src/modules/mol'
touch build-stamp
alan@ubuntu:/usr/src/modules/mol$
``` I went ahead and followed the rest of instructions anyway, and here's where I can't go any further...```
alan@ubuntu:/usr/src$ startmol --osx
Mac-on-Linux 0.9.70 [Aug 3 2004 16:18]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 1
====================================================================
  No mol-0.9.70 kernel modules corresponding to the running
  2.6.10-4-powerpc kernel were found ('startmol --list' displays
  installed version). Recompile the mol kernel modules (recommended)
  or try starting MOL as root using the '-a' switch. The '-a'
  flag can be made default by the 'allow_kver_mismatch: yes' setting.
====================================================================
alan@ubuntu:/usr/src$ 
```

Any ideas on what I can do? Prior to doing this, I had just installed from the CD, then ran the Ubuntu Update Manager that was next to the clock. Other than that, this Ubuntu installation is so fresh and so clean...

Oh, and since it mentions an error around ethernet, here's my hardware: PowerMac G4 Dual 1Ghz MDD (no F/W 800), AirPort (not Extreme) being used, Ethernet not being used, 512mb ram. (Anything else)? And I'm running Hoary, so I skipped over the section on editing the kernel headers.

In advance, thanks for helping!

---

### Post by leaded on 2005-04-04
Anyone?

---

### Post by philcolbourn on 2005-04-10
i'm hoping they get LOM working soon so (I am guessing) the airport extreme and track pad and all other devices are supported.

If i get a usb mouse i will give MOL a go, but without 802.11g and the trackpad it is really just an exercise that can't work too well (in my case on a 2005 powerbook g4)

---

