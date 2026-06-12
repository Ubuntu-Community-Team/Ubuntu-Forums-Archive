---
title: "[SOLVED] Fail to upgrade due to files conflict"
date: 2008-10-08
forum: Arch and derivatives
---

### Post by Dani Filth on 2008-10-08
I tried to upgrade the whole system by "pacman -Syu" today, but it failed due to conflicting files, does anybody know how to overcome this problem?
(I already downloaded the packages needed to upgrade, but cannot perform upgrading)

> bash-3.2# pacman -Syu
:: Synchronizing package databases...
 core is up to date
 extra is up to date
 community is up to date
:: Starting full system upgrade...
resolving dependencies...
looking for inter-conflicts...

Targets (34): curl-7.19.0-1  e2fsprogs-1.41.1-2  xulrunner-1.9.0.3-1  
              firefox-3.0.3-1  pciutils-3.0.2-1  pm-utils-1.2.2.1-1  
              udev-128-5  hal-0.5.11-4  imagemagick-6.4.4.1-1  
              initscripts-2008.09-2  iputils-20071127-2  klibc-1.5.14-1  
              klibc-extras-2.5-1  klibc-kbd-1.15.20080312-7  
              klibc-module-init-tools-3.4-2  klibc-udev-128-1  
              libldap-2.3.43-3  libpng-1.2.32-1  pam-1.0.2-2  
              pcmciautils-015-2  texinfo-4.13a-1  unrar-3.8.3-1  ladspa-1.13-1  
              fluidsynth-1.0.8-1  libdvbpsi-0.1.6-3  zvbi-0.2.26-1  
              taglib-1.5-1  libmodplug-0.8.4-1  libdaemon-0.12-1  
              avahi-0.6.23-1  sdl_image-1.2.6-2  speex-1.2rc1-1  qt-4.4.2-3  
              vlc-0.9.4-1  

Total Download Size:    0.00 MB
Total Installed Size:   191.50 MB

Proceed with installation? [Y/n] y
checking package integrity...
(34/34) checking for file conflicts                 [#####################] 100%
error: could not prepare transaction
error: failed to commit transaction (conflicting files)
klibc: /usr/lib/klibc/include/asm/Kbuild exists in filesystem
klibc: /usr/lib/klibc/include/asm/a.out-core.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/a.out.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/acpi.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/agp.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/alternative-asm.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/alternative.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/apic.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/apicdef.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/arch_hooks.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/asm-offsets.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/asm.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/atomic.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/atomic_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/atomic_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/auxvec.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/bios_ebda.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/bitops.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/boot.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/bootparam.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/bug.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/bugs.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/byteorder.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/cache.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/cacheflush.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/calgary.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/calling.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/checksum.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/checksum_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/checksum_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/cmpxchg.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/cmpxchg_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/cmpxchg_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/compat.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/cpu.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/cpufeature.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/cputime.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/current.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/current_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/current_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/debugreg.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/delay.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/desc.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/desc_defs.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/device.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/div64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/dma-mapping.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/dma.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/dmi.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/ds.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/dwarf2.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/dwarf2_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/dwarf2_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/e820.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/e820_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/e820_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/edac.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/efi.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/elf.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/emergency-restart.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/errno.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/fb.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/fcntl.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/fixmap.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/fixmap_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/fixmap_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/floppy.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/frame.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/futex.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/gart.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/genapic.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/genapic_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/genapic_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/geode.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/gpio.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/hardirq.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/hardirq_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/hardirq_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/highmem.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/hpet.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/hugetlb.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/hw_irq.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/hw_irq_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/hw_irq_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/hypertransport.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/i387.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/i8253.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/i8259.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/ia32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/ia32_unistd.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/ide.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/idle.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/intel_arch_perfmon.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/io.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/io_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/io_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/io_apic.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/ioctl.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/ioctls.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/iommu.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/ipcbuf.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/ipi.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/irq.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/irq_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/irq_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/irq_regs.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/irq_regs_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/irq_regs_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/irqflags.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/ist.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/k8.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/kdebug.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/kexec.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/kgdb.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/kmap_types.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/kprobes.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/kvm.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/kvm_host.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/kvm_para.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/kvm_x86_emulate.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/ldt.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/lguest.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/lguest_hcall.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/linkage.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/local.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-bigsmp/mach_apic.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-bigsmp/mach_apicdef.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-bigsmp/mach_ipi.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-bigsmp/mach_mpspec.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-default/apm.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-default/do_timer.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-default/entry_arch.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-default/irq_vectors.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-default/irq_vectors_limits.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-default/mach_apic.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-default/mach_apicdef.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-default/mach_ipi.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-default/mach_mpparse.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-default/mach_mpspec.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-default/mach_timer.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-default/mach_traps.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-default/mach_wakecpu.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-default/pci-functions.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-default/setup_arch.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-default/smpboot_hooks.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-es7000/mach_apic.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-es7000/mach_apicdef.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-es7000/mach_ipi.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-es7000/mach_mpparse.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-es7000/mach_mpspec.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-es7000/mach_wakecpu.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-generic/gpio.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-generic/irq_vectors_limits.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-generic/mach_apic.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-generic/mach_apicdef.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-generic/mach_ipi.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-generic/mach_mpparse.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-generic/mach_mpspec.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-numaq/mach_apic.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-numaq/mach_apicdef.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-numaq/mach_ipi.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-numaq/mach_mpparse.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-numaq/mach_mpspec.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-numaq/mach_wakecpu.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-rdc321x/gpio.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-rdc321x/rdc321x_defs.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-summit/irq_vectors_limits.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-summit/mach_apic.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-summit/mach_apicdef.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-summit/mach_ipi.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-summit/mach_mpparse.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-summit/mach_mpspec.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-visws/cobalt.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-visws/entry_arch.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-visws/irq_vectors.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-visws/lithium.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-visws/mach_apic.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-visws/mach_apicdef.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-visws/piix4.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-visws/setup_arch.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-visws/smpboot_hooks.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-voyager/do_timer.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-voyager/entry_arch.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-voyager/irq_vectors.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-voyager/setup_arch.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/math_emu.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mc146818rtc.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mca.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mca_dma.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mce.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mman.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mmu.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mmu_context.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mmu_context_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mmu_context_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mmx.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mmzone.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mmzone_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mmzone_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/module.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mpspec.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mpspec_def.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/msgbuf.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/msidef.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/msr-index.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/msr.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mtrr.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mutex.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mutex_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mutex_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/namei.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/nmi.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/nops.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/numa.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/numa_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/numa_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/numaq.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/olpc.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/page.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/page_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/page_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/param.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/paravirt.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/parport.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/pat.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/pci-direct.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/pci.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/pci_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/pci_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/pda.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/percpu.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/pgalloc.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/pgtable-2level-defs.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/pgtable-2level.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/pgtable-3level-defs.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/pgtable-3level.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/pgtable.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/pgtable_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/pgtable_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/poll.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/posix_types.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/posix_types_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/posix_types_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/prctl.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/processor-cyrix.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/processor-flags.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/processor.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/proto.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/ptrace-abi.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/ptrace.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/pvclock-abi.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/pvclock.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/reboot.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/reboot_fixups.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/required-features.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/resource.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/resume-trace.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/rio.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/rtc.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/rwlock.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/rwsem.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/scatterlist.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/seccomp.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/seccomp_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/seccomp_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/sections.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/segment.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/semaphore.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/sembuf.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/serial.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/setup.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/shmbuf.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/shmparam.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/sigcontext.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/sigcontext32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/siginfo.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/signal.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/smp.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/socket.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/sockios.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/sparsemem.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/spinlock.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/spinlock_types.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/srat.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/stacktrace.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/stat.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/statfs.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/string.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/string_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/string_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/suspend.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/suspend_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/suspend_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/swiotlb.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/sync_bitops.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/system.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/system_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/tce.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/termbits.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/termios.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/therm_throt.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/thread_info.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/thread_info_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/thread_info_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/time.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/timer.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/timex.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/tlb.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/tlbflush.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/topology.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/trampoline.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/tsc.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/types.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/uaccess.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/uaccess_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/uaccess_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/ucontext.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/unaligned.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/unistd.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/unistd_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/unistd_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/unwind.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/user.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/user32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/user_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/user_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/uv/uv_hub.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/uv/uv_mmrs.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/vdso.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/vga.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/vgtod.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/vic.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/vm86.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/vmi.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/vmi_time.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/voyager.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/vsyscall.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/xen/events.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/xen/grant_table.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/xen/hypercall.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/xen/hypervisor.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/xen/interface.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/xen/page.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/xor.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/xor_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/xor_64.h exists in filesystem
Errors occurred, no packages were upgraded.


---

### Post by Rumor on 2008-10-08
Whoops: I should have read the Arch forums before replying.

This issue is discussed with the way to fix it right here: [http://bbs.archlinux.org/viewtopic.php?id=56431](http://bbs.archlinux.org/viewtopic.php?id=56431)

---

### Post by kpkeerthi on 2008-10-08
> **Dani Filth said:**
> I tried to upgrade the whole system by "pacman -Syu" today, but it failed due to conflicting files, does anybody know how to overcome this problem?
(I already downloaded the packages needed to upgrade, but cannot perform upgrading)

The fix is on Archlinux home page [http://www.archlinux.org/](http://www.archlinux.org/)

---

### Post by handy on 2008-10-11
*Due to a limitation in pacman's conflict checking and symbolic link resolution, the upgrade to klibc-1.5.14-1 requires manual removal of a symbolic link befole updating. Please run the command "rm /usr/lib/klibc/include/asm" as root to remove the symbolic link that will otherwise cause a few hundred false file conflicts.*

---

