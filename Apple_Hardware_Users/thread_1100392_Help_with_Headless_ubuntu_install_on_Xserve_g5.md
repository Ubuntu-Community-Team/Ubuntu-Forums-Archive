---
title: "Help with Headless ubuntu install on Xserve g5"
date: 2009-03-19
forum: Apple Hardware Users
---

### Post by splbound on 2009-03-19
Hi,

I'm trying to do a Headless ubuntu install on an Xserve G5.

Booting up with the alternate CD connected to the serial port. I get the following output on the console:


parsing <CHRP-BOOT>

evaluating <BOOT-SCRIPT>

Then it just sits there with nothing more.



I have tried booting it through open firmware using the commands:

> setenv input-device scca
> setenv output-device scca
> boot cd:,\install\yaboot

I can then get to the boot: and I type install 

boot: install

then i get:

Please wait, loading kernel...
   Elf64 kernel loaded...
Loading ramdisk...
ramdisk loaded at 01d00000, size: 5809 Kbytes
OF stdout device is: /ht@0,f2000000/pci@3/mac-io@7/escc@13000/ch-a@13020
command line: ro ramdisk_size=8192 file=/cdrom/preseed/ubuntu.seed quiet --
memory layout at init:
  alloc_bottom : 00000000022ad000
  alloc_top    : 0000000030000000
  alloc_top_hi : 0000000080000000
  rmo_top      : 0000000030000000
  ram_top      : 0000000080000000
Looking for displays
copying OF device tree ...
Building dt strings...
Building dt structure...
Device tree strings 0x00000000025ae000 -> 0x00000000025af357
Device tree struct  0x00000000025b0000 -> 0x00000000025c3000
Calling quiesce ...

DO-QUIESCE finishedreturning from prom_init
Hello World !
CF000012

Setup Arch
CF000015

Setup Done
smp_core99_probe
smp_core99_kick_cpu
smp_core99_kick_cpu done
core99_setup_cpu 0 done
Linux ppc64

#1 SMP Tue Sep 30 16:40:22 UTC 2008

Then it just hangs there.

I would appreciate any help I can get trying to install it.

---

