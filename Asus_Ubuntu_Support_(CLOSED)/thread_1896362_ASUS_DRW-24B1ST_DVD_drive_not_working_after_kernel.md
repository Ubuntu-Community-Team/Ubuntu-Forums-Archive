---
title: "ASUS DRW-24B1ST DVD drive not working after kernel update"
date: 2011-12-16
forum: Asus Ubuntu Support (CLOSED)
---

### Post by dankTHAstank on 2011-12-16
I am COMPLETELY new to Linux and so far I am enjoying myself but being such a noob i am having some problems.  

 description: Motherboard
       product: P8H67-M PRO
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: MF70BAG03801045
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1104
          date: 09/26/2011
          size: 64KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-2500 CPU @ 3.30GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-2500 CPU @ 3.30GHz
          serial: To Be Filled By O.E.M.
          slot: LGA1155
          size: 3301MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt aes xsave avx lahf_lm ida arat epb xsaveopt pln pts tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=4 enabledcores=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: internal unified
     *-memory
          description: System Memory
          physical id: 2a
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: F3-10666CL9-2GBPK
             vendor: Undefined
             physical id: 0
             serial: 0000000
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM Synchronous [empty]
             product: Array1_PartNumber1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             width: 64 bits
        *-bank:2
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: F3-10666CL9-2GBPK
             vendor: Undefined
             physical id: 2
             serial: 0000000
             slot: DIMM2
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM Synchronous [empty]
             product: Array1_PartNumber3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
             width: 64 bits

i bought all these components from newegg,  I managed to get it all put together without shorting anything which i was happy about.  When i first installed Ubuntu 11.10, my DVD drive worked fine.  I put in my ASUS MB support dvd to update drivers etc, and it gave me a message saying please update to latest kernel for driver support.  So, i jumped from the 3.0 generic kernel to the 3.1.0-030100-generic.  I rebooted, and low and behold my DVD drive no longer reads anything so i cant install the drivers! what is really confusing to me is that when the machine first boots, a message comes up saying that there is a bootable DVD in the drive and asks if i would like to boot from it.  I really hope someone can help me out cuz my brain is starting to hurt :P  Any feedback is much appreciated.

---

