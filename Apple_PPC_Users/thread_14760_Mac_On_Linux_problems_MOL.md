---
title: "Mac On Linux problems MOL"
date: 2005-02-09
forum: Apple PPC Users
---

### Post by ubuntu4everyone on 2005-02-09
I followed the MOL howto on ubuntu how to's and it seemed to go well until I actually tried
it and it appeared that it did not recognise the kernal modules, please help !!!  


:confused:

---

### Post by M-Rick on 2005-02-10
Yes because you have Mac OS X 10.3.6 while actualy MOL only support Mac OS X 10.3.3

From the [Mac On Linux](http://www.maconlinux.org/) start page

 Feature List
 
Client OS support:
- Mac OS X (10.1-10.3.3)
- Mac OS 7.5.2 to 9.2.2
- Linux

---

### Post by ubuntu4everyone on 2005-02-10
But when i tried yellow dog linux it worked once....
and then broke!  
](*,)

---

### Post by val1984 on 2005-02-10
I had no problem running MOL with Mac OS X 10.3.6...

---

### Post by ubuntu4everyone on 2005-02-10
how did u do it

---

### Post by val1984 on 2005-02-10
I followed the instructions found on the wiki.

---

### Post by ubuntu4everyone on 2005-02-10
Ok, I followed it but let's wipe any trace of mol and start again
how do i do that

---

### Post by trash on 2005-02-10
I foolowed the wiki too:D i didn't get any strange errors and everything seemed to go smoothly...

till...

Mac-on-Linux 0.9.70 [Aug 3 2004 16:18]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 0
Removing stale lockfile /var/lock/mol-0
Running in PowerPC 7400 mode, 256 MB RAM
Timebase: 33.29 MHz, Bus: 133.16 MHz, Clock: 466 MHz
Using USB mouse on /dev/input/mice
OHCI USB controller registered
Could not open '/var/lib/mol/x11.kbd'
***** SIGNAL 11 [Segmentation fault] in thread main-thread *****
   si_signo = 11, si_errno 0, si_code 00000001, si_addr 0xfef63f64
   Last RVEC: 0x0 (0), last OSI: 0, mac_nip FFF00100
   NIP 0x0fbc6568
***** Backtrace *****
   7fffedf0: backtrace + 0x3c
   7fffee10: signal_handler + 0x178
   7fffee30: 0x0fd48b64
   7fffee60: 0x7ffff1b8
   7ffff4b0: 0x0fd43cbc
   7ffff4d0: 0x0fbc4fcc
   7ffff4f0: 0x0fef76bc
   7ffff510: 0x0fef767c
   7ffff530: 0x0fee1254
   7ffff560: 0x0fee15e8
   7ffff580: 0x0feee890
   7ffff720: 0x0feee79c
   7ffff750: create_x_picture + 0x1e8
   7ffff860: x11_init + 0x25c
   7ffff8d0: driver_mgr_init + 0xc0
   7ffff8f0: ioports_init + 0x44
   7ffff900: main + 0x18c
   7ffff920: 0x0fb68100
   7ffff960: 0x00000000
cleaning up...

maconlinux.org.. i was searching archive for x11.kbd... tells of a bug and a fix... [http://lists.maconlinux.org/pipermail/mol-general/2004-November/003504.html](http://lists.maconlinux.org/pipermail/mol-general/2004-November/003504.html)

"With the help of Jens and reading the Debian
bug #278921 it works again.  Thank you very much Jens.  :)
In that report of emails the web page to download the Debian packages"

libpng12-0_1.2.5.0-7_powerpc.deb
libpng12-dev_1.2.5.0-7_powerpc.deb
> bug #278921 it works again.

My problem is that I don't seem to have libpng nor can I apt it... anybody else had this?

---

### Post by trash on 2005-02-11
Can anybody with MOL working tell me what version libpng they have.

seems 1.2.7 is the bad guy(which i have and is in the Ubuntu install), I just went to downgrade to 1.2.5 as recommended in the MOL lists but Synaptic want to uninstall half my harddrive to make it happen:(... what do I do here?

---

### Post by ubuntu4everyone on 2005-02-11
Ill post text install text

PTO

---

### Post by ubuntu4everyone on 2005-02-11
Reading Package Lists... Done
Building Dependency Tree... Done
build-essential is already the newest version.
linux-headers-2.6-powerpc is already the newest version.
Suggested packages:
  kernel-headers kernel-source
Recommended packages:
  kernel-package
The following NEW packages will be installed:
  mol-modules-source
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/762kB of archives.
After unpacking 815kB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package mol-modules-source.
(Reading database ... 73793 files and directories currently installed.)
Unpacking mol-modules-source (from .../mol-modules-source_0.9.70-6_powerpc.deb) ...
Setting up mol-modules-source (0.9.70-6) ...

lewis@ubuntu:~ $ sudo apt-get install kernal-package Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package kernal-package
lewis@ubuntu:~ $ sudo apt-get install kernel-package
Reading Package Lists... Done
Building Dependency Tree... Done
Suggested packages:
  kernel-source libdb3-dev libncurses-dev docbook-utils
The following NEW packages will be installed:
  kernel-package
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 300kB of archives.
After unpacking 1114kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main kernel-package 8.091.0ubuntu4 [300kB]Fetched 300kB in 5s (55.9kB/s)

Preconfiguring packages ...
Selecting previously deselected package kernel-package.
(Reading database ... 73798 files and directories currently installed.)
Unpacking kernel-package (from .../kernel-package_8.091.0ubuntu4_all.deb) ...
Setting up kernel-package (8.091.0ubuntu4) ...
lewis@ubuntu:~ $ cd /usr/src
lewis@ubuntu:/usr/src $ sudo tar xzvf mol-modules.tar.gz
modules/
modules/mol/
modules/mol/src/
modules/mol/src/kmod/
modules/mol/src/kmod/Darwin/
modules/mol/src/kmod/Darwin/Info.plist
modules/mol/src/kmod/Darwin/Makefile.am
modules/mol/src/kmod/Darwin/Makefile.mod
modules/mol/src/kmod/Darwin/MolExt.cpp
modules/mol/src/kmod/Darwin/MolExt.h
modules/mol/src/kmod/Darwin/MolUserClient.cpp
modules/mol/src/kmod/Darwin/MolUserClient.h
modules/mol/src/kmod/Darwin/alloc.c
modules/mol/src/kmod/Darwin/init.c
modules/mol/src/kmod/Darwin/mmu.c
modules/mol/src/kmod/Darwin/relbuild.pl
modules/mol/src/kmod/Darwin/alloc.h
modules/mol/src/kmod/Darwin/archinclude.h
modules/mol/src/kmod/Debug/
modules/mol/src/kmod/Debug/mtable_dbg.c
modules/mol/src/kmod/Linux/
modules/mol/src/kmod/Linux/fault.c
modules/mol/src/kmod/Linux/misc.c
modules/mol/src/kmod/Linux/mmu.c
modules/mol/src/kmod/Linux/alloc.h
modules/mol/src/kmod/Linux/archinclude.h
modules/mol/src/kmod/Linux/linux.S
modules/mol/src/kmod/Linux/tlbie.h
modules/mol/src/kmod/Linux/Makefile.24
modules/mol/src/kmod/Linux/Makefile.26
modules/mol/src/kmod/Linux/kuname.c
modules/mol/src/kmod/Linux/dev.c
modules/mol/src/kmod/Linux/Makefile
modules/mol/src/kmod/Linux/checker.pl
modules/mol/src/kmod/Linux/relbuild.pl
modules/mol/src/kmod/include/
modules/mol/src/kmod/include/asmfuncs.h
modules/mol/src/kmod/include/emu.h
modules/mol/src/kmod/include/misc.h
modules/mol/src/kmod/include/mmu.h
modules/mol/src/kmod/include/molasm.h
modules/mol/src/kmod/include/mtable.h
modules/mol/src/kmod/include/performance.h
modules/mol/src/kmod/include/reloc.h
modules/mol/src/kmod/include/vector.h
modules/mol/src/kmod/603.S
modules/mol/src/kmod/actions.S
modules/mol/src/kmod/asm_offsets.inc
modules/mol/src/kmod/context.c
modules/mol/src/kmod/dec.S
modules/mol/src/kmod/emu.c
modules/mol/src/kmod/emulation.S
modules/mol/src/kmod/entry.S
modules/mol/src/kmod/fault.c
modules/mol/src/kmod/hook.c
modules/mol/src/kmod/init.c
modules/mol/src/kmod/iopage.S
modules/mol/src/kmod/mmu.c
modules/mol/src/kmod/mmu_fb.c
modules/mol/src/kmod/mmu_io.c
modules/mol/src/kmod/mmu_tracker.c
modules/mol/src/kmod/mtable.c
modules/mol/src/kmod/ptaccess.c
modules/mol/src/kmod/ptintercept.S
modules/mol/src/kmod/splitmode.S
modules/mol/src/kmod/traps.S
modules/mol/src/kmod/emuaccel.S
modules/mol/src/kmod/skiplist.c
modules/mol/src/kmod/vsid.S
modules/mol/src/kmod/mpc107/
modules/mol/src/kmod/mpc107/Makefile.am
modules/mol/src/kmod/mpc107/Makefile.mod
modules/mol/src/kmod/mpc107/alloc.h
modules/mol/src/kmod/mpc107/archinclude.h
modules/mol/src/kmod/mpc107/fault.c
modules/mol/src/kmod/mpc107/init.c
modules/mol/src/kmod/mpc107/ld.script
modules/mol/src/kmod/mpc107/libc.c
modules/mol/src/kmod/mpc107/mpc107.S
modules/mol/src/kmod/mpc107/mpcvector.h
modules/mol/src/kmod/mpc107/test.c
modules/mol/src/kmod/mpc107/tlbie.h
modules/mol/src/kmod/mpc107/vsprintf.c
modules/mol/src/kmod/misc.c
modules/mol/src/kmod/Makefile
modules/mol/src/netdriver/
modules/mol/src/netdriver/MAKEDEV
modules/mol/src/netdriver/ethertap.c
modules/mol/src/netdriver/if_tun.h
modules/mol/src/netdriver/sheep.c
modules/mol/src/netdriver/tun.c
modules/mol/src/netdriver/Makefile.24
modules/mol/src/netdriver/Makefile.26
modules/mol/src/netdriver/kuname.c
modules/mol/src/netdriver/Kconfig
modules/mol/src/netdriver/Makefile
modules/mol/src/shared/
modules/mol/src/shared/ppc/
modules/mol/src/shared/ppc/mregs.h
modules/mol/src/shared/README
modules/mol/src/shared/asm.m4
modules/mol/src/shared/asm_offsets.c
modules/mol/src/shared/asmdefs.h
modules/mol/src/shared/constants.h
modules/mol/src/shared/kernel_vars.h
modules/mol/src/shared/mac_registers.h
modules/mol/src/shared/mmu_contexts.h
modules/mol/src/shared/mmu_mappings.h
modules/mol/src/shared/mmutypes.h
modules/mol/src/shared/mol_config.h
modules/mol/src/shared/processor.h
modules/mol/src/shared/prom.h
modules/mol/src/shared/rvec.h
modules/mol/src/shared/version.h
modules/mol/src/shared/weaksym.h
modules/mol/src/shared/emuaccel_sh.h
modules/mol/src/shared/skiplist.h
modules/mol/src/shared/osi.h
modules/mol/src/shared/mol-ioctl.h
modules/mol/src/shared/config.h.in
modules/mol/src/shared/config.h
modules/mol/src/include/
modules/mol/src/include/e-ppc/
modules/mol/src/include/e-ppc/mregs.h
modules/mol/src/include/i386/
modules/mol/src/include/i386/mregs.h
modules/mol/src/include/i386/byteorder.h
modules/mol/src/include/async.h
modules/mol/src/include/booter.h
modules/mol/src/include/boothelper_sh.h
modules/mol/src/include/breakpoints.h
modules/mol/src/include/byteorder.h
modules/mol/src/include/debugger.h
modules/mol/src/include/elf.h
modules/mol/src/include/elfload.h
modules/mol/src/include/extralib.h
modules/mol/src/include/getopt.h
modules/mol/src/include/io.h
modules/mol/src/include/keycodes.h
modules/mol/src/include/llseek.h
modules/mol/src/include/memory.h
modules/mol/src/include/mol_assert.h
modules/mol/src/include/molcpu.h
modules/mol/src/include/nvram.h
modules/mol/src/include/obstack.h
modules/mol/src/include/osi_calls.h
modules/mol/src/include/platform.h
modules/mol/src/include/poll.h
modules/mol/src/include/promif.h
modules/mol/src/include/pseudofs.h
modules/mol/src/include/pseudofs_sh.h
modules/mol/src/include/res_manager.h
modules/mol/src/include/session.h
modules/mol/src/include/thread.h
modules/mol/src/include/timer.h
modules/mol/src/include/verbose.h
modules/mol/src/include/video.h
modules/mol/src/include/wrapper.h
modules/mol/src/include/video_sh.h
modules/mol/src/include/os_interface.h
modules/mol/src/include/syscall.h
modules/mol/src/include/atomic.h
modules/mol/src/include/osx/
modules/mol/src/include/osx/byteswap.h
modules/mol/src/include/ppc/
modules/mol/src/include/ppc/byteorder.h
modules/mol/src/include/kbd_sh.h
modules/mol/scripts/
modules/mol/scripts/kernelsrc
modules/mol/scripts/mol_uname
modules/mol/Makefile.top
modules/mol/Rules.make
modules/mol/config/
modules/mol/config/kconfig/
modules/mol/config/kconfig/Makefile
modules/mol/config/kconfig/conf.c
modules/mol/config/kconfig/confdata.c
modules/mol/config/kconfig/expr.c
modules/mol/config/kconfig/expr.h
modules/mol/config/kconfig/lkc.h
modules/mol/config/kconfig/lkc_proto.h
modules/mol/config/kconfig/mconf.c
modules/mol/config/kconfig/menu.c
modules/mol/config/kconfig/symbol.c
modules/mol/config/kconfig/zconf-l.l
modules/mol/config/kconfig/zconf-y.y
modules/mol/config/kconfig/.deps/
modules/mol/config/kconfig/.objs-ppc/
modules/mol/config/kconfig/.objs-ppc/.dummy
modules/mol/config/kconfig/.objs-ppc/zconf-y.o
modules/mol/config/kconfig/.objs-ppc/mconf.o
modules/mol/config/kconfig/.objs-ppc/mconfig
modules/mol/config/kconfig/.objs-ppc/libkconf.a
modules/mol/config/kconfig/.objs-ppc/config
modules/mol/config/kconfig/.objs-ppc/conf.o
modules/mol/config/kconfig/zconf-y.c
modules/mol/config/kconfig/zconf-y.h
modules/mol/config/kconfig/.autoinclude/
modules/mol/config/kconfig/.autoinclude/autoconf-ppc.h
modules/mol/config/kconfig/zconf-l.c
modules/mol/config/lxdialog/
modules/mol/config/lxdialog/BIG.FAT.WARNING
modules/mol/config/lxdialog/Makefile
modules/mol/config/lxdialog/checklist.c
modules/mol/config/lxdialog/colors.h
modules/mol/config/lxdialog/dialog.h
modules/mol/config/lxdialog/inputbox.c
modules/mol/config/lxdialog/lxdialog.c
modules/mol/config/lxdialog/menubox.c
modules/mol/config/lxdialog/msgbox.c
modules/mol/config/lxdialog/textbox.c
modules/mol/config/lxdialog/util.c
modules/mol/config/lxdialog/yesno.c
modules/mol/config/lxdialog/.deps/
modules/mol/config/lxdialog/.objs-ppc/
modules/mol/config/lxdialog/.objs-ppc/lxdialog
modules/mol/config/lxdialog/.objs-ppc/checklist.o
modules/mol/config/lxdialog/.objs-ppc/menubox.o
modules/mol/config/lxdialog/.objs-ppc/textbox.o
modules/mol/config/lxdialog/.objs-ppc/yesno.o
modules/mol/config/lxdialog/.objs-ppc/inputbox.o
modules/mol/config/lxdialog/.objs-ppc/util.o
modules/mol/config/lxdialog/.objs-ppc/lxdialog.o
modules/mol/config/lxdialog/.objs-ppc/msgbox.o
modules/mol/config/Kconfig
modules/mol/config/Makefile
modules/mol/config/Makefile.defs.in
modules/mol/config/Makefile.osx
modules/mol/config/Makefile.ppc
modules/mol/config/defconfig-osx
modules/mol/config/defconfig-ppc
modules/mol/config/nodist
modules/mol/config/Makefile.defs
modules/mol/config/.deps/
modules/mol/.config
modules/mol/.inc-ppc/
modules/mol/.inc-ppc/autoconf.h
modules/mol/.inc-ppc/asm
modules/mol/.inc-ppc/cpu
modules/mol/.inc-ppc/molversion.h
modules/mol/.inc-ppc/asm_offsets.h
modules/mol/debian/
modules/mol/debian/control.m4
modules/mol/debian/changelog.m4
modules/mol/debian/postinst.m4
modules/mol/debian/postrm.m4
modules/mol/debian/rules
modules/mol/Makefile
lewis@ubuntu:/usr/src $ export KVERS="$(uname -r)"
lewis@ubuntu:/usr/src $ export KVERS="$(uname -r)"
lewis@ubuntu:/usr/src $ export KSRC="/usr/src/linux-headers-$(uname -r)"
lewis@ubuntu:/usr/src $ KEMAIL="lewis@shirlandshaun.net"
lewis@ubuntu:/usr/src $ export KMAINT="Your Name"
lewis@ubuntu:/usr/src $ export KMAINT="Lewis Porter"
lewis@ubuntu:/usr/src $ KDREV="ubuntu0"
lewis@ubuntu:/usr/src $ cd modules/mol
lewis@ubuntu:/usr/src/modules/mol $ sudo debian/rules build
make: Nothing to be done for `build'.
lewis@ubuntu:/usr/src/modules/mol $ dir
build-stamp      debian                           Makefile      scripts
config           install-stamp                    Makefile.top  src
configure-stamp  linux-headers-2.6.8.1-3-powerpc  Rules.make
lewis@ubuntu:/usr/src/modules/mol $ sudo debian/rules build
make: Nothing to be done for `build'.
lewis@ubuntu:/usr/src/modules/mol $ sudo debian/rules binary-mol-modules
dh_testdir
dh_testroot
dh_installdocs
dh_installmodules
dh_installchangelogs
dh_link
dh_strip
dh_compress
dh_fixperms
dh_installdeb
dh_gencontrol
dh_md5sums
dh_builddeb --destdir=/usr/src/linux-headers-2.6.8.1-4-powerpc/..
dpkg-deb: building package `mol-modules-2.6.8.1-3-powerpc' in `/usr/src/linux-headers-2.6.8.1-4-powerpc/../mol-modules-2.6.8.1-3-powerpc_0.9.70+ubuntu0_powerpc.deb'.
lewis@ubuntu:/usr/src/modules/mol $ sudo dpkg -i /usr/src/mol-modules-2.6.8.1-4-powerpc_0.9.70+ubuntu0_powerpc.deb
dpkg: error processing /usr/src/mol-modules-2.6.8.1-4-powerpc_0.9.70+ubuntu0_powerpc.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /usr/src/mol-modules-2.6.8.1-4-powerpc_0.9.70+ubuntu0_powerpc.deb
lewis@ubuntu:/usr/src/modules/mol $ dir
build-stamp      debian                           Makefile      scripts
config           install-stamp                    Makefile.top  src
configure-stamp  linux-headers-2.6.8.1-3-powerpc  Rules.make
lewis@ubuntu:/usr/src/modules/mol $

---

### Post by trash on 2005-02-11
Hey ubuntu4everyone, I see why you are having problems.... $(uname -r)
type that command(without brackets) in terminal to get what version you are running ;)

ewis@ubuntu:/usr/src $ export KVERS="$(uname -r)"
lewis@ubuntu:/usr/src $ export KVERS="$(uname -r)"
lewis@ubuntu:/usr/src $ export KSRC="/usr/src/linux-headers-$(uname -r)"

libpng, the version I have is conflicting with something, it isn't part of the install though.
Thanks anyway:)

---

### Post by ubuntu4everyone on 2005-02-11
I messed up system on previous attempts, reinstall and then try again 
:roll:

---

### Post by ubuntu4everyone on 2005-02-11
I have got kernal 2.6.8.1-3powerpc, but when i start it it dosent recognise the modules and says

 it wants   modules for 2.6.8.1-4powerpc, wot do i do

---

### Post by trash on 2005-02-11
AH! i just noticed you have not upgraded your kernel before trying the mol install...
the one package held back all the time in apt is it.
apt-get install kernel or upgrade... there is a Wiki on it i think

---

### Post by ubuntu4everyone on 2005-02-13
lewis@ubuntu:~ $ uname -r
2.6.8.1-4-powerpc
lewis@ubuntu:~ $ ste
bash: ste: command not found
lewis@ubuntu:~ $ startmol
Mac-on-Linux 0.9.70 [Aug 3 2004 16:18]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 0
Mac-on-Linux must be setuid root!
lewis@ubuntu:~ $ sudo startmol
Password:
Mac-on-Linux 0.9.70 [Aug 3 2004 16:18]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 0
====================================================================
  No mol-0.9.70 kernel modules corresponding to the running
  2.6.8.1-4-powerpc kernel were found ('startmol --list' displays
  installed version). Recompile the mol kernel modules (recommended)
  or try starting MOL as root using the '-a' switch. The '-a'
  flag can be made default by the 'allow_kver_mismatch: yes' setting.
====================================================================
lewis@ubuntu:~ $ sudo startmol --list
--------------------------------------------------------------
  Running kernel:         2.6.8.1-4-powerpc
--------------------------------------------------------------
  Available modules:
    <none>
--------------------------------------

wot now ??

---

