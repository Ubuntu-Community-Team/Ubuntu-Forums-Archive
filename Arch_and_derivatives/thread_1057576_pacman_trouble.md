---
title: "pacman trouble"
date: 2009-02-01
forum: Arch and derivatives
---

### Post by stonecoldjha on 2009-02-01
i typed pacman -Syu,and it very well connected to the proxy,and downloaded some stuff,and saved that.Then it displayed the following in the commandline:

Starting full system upgrade
Replace netkit-telnet with core/inetutils?[Y/n]Y
Replace iproute with core/iproute2?[Y/n]Y
Replace at12 with core/kernel26?[Y/n]Y
Replace wlan-ng26 with core/kernel26[Y/n]Y
resolving dependencis
looking for inter-conflicts
error:failed to prepare transaction(could not satisfy dependencies)
at12:requires kernel26<2.6.26
ipw3945:requires kernel26<2.6.26


Now,this leaves me totally baffled.How do i solve this?

---

### Post by kerry_s on 2009-02-02
that's your wireless stuff right?

i would say get plugged in, remove the packages:
```
pacman -Rsn at12 ipw3945
```

do the update, then reinstall the packages.

---

### Post by Nepherte on 2009-02-02
Arch now uses the opensource version for your wireless network card: [http://www.archlinux.org/packages/core/i686/iwlwifi-3945-ucode/](http://www.archlinux.org/packages/core/i686/iwlwifi-3945-ucode/)

Also check out the wiki: [http://wiki.archlinux.org/index.php/Wireless_Setup#iwl3945.2C_iwl4965_and_iwl5000-series](http://wiki.archlinux.org/index.php/Wireless_Setup#iwl3945.2C_iwl4965_and_iwl5000-series)

---

### Post by stonecoldjha on 2009-02-02
thanks,i got it done.i uninstalled those two packages,and then proceeded to update the system,so i typed "pacman -Syu".It downloaded some 115 MB of updates within 2-3 minutes,and then perhaps went ahead to install the packages.the console read like:-

checking package integrity

errors occurred,no packages were upgraded.



now,tell me what this is?and,how do i get around this?

---

### Post by kerry_s on 2009-02-02
how old is your install?
are you using other than the main repo's?
did you use the core/net installer?
[ftp://mirror.cs.vt.edu/pub/ArchLinux/iso/latest/archlinux-2008.06-core-i686.iso](ftp://mirror.cs.vt.edu/pub/ArchLinux/iso/latest/archlinux-2008.06-core-i686.iso)

---

### Post by stonecoldjha on 2009-02-02
i installed it just a day ago.no,i don't use any repos other than those enabled by default.

---

### Post by kerry_s on 2009-02-02
try cleaning things first:
pacman -Scc

than sync and update
pacman -Syu

---

### Post by stonecoldjha on 2009-02-02
i did exactly that,cleaned the cache,and then executed "pacman -Syu".It downloaded the packages.
But,still it showed the same thing that errors occurred,could not upgrade packages.

---

### Post by Nepherte on 2009-02-02
Could you post the full output of pacman? Add the last lines (up to you to decide how many lines that relate to your problem) of /var/log/pacman.log to it as well.

---

### Post by stonecoldjha on 2009-02-02
how do i do that?

---

### Post by stonecoldjha on 2009-02-02
the following is the output file of pacman -Syu:



:: Synchronizing package databases...
:: Starting full system upgrade...
resolving dependencies...
warning: provider package was selected (iproute2 provides iproute)
looking for inter-conflicts...

Targets (121): kernel-headers-2.6.27.6-2  tzdata-2008i-1  glibc-2.9-4  
               ncurses-5.7-2  readline-5.2.013-2  bash-3.2.048-3  
               texinfo-4.13a-3  diffutils-2.8.1-6  m4-1.4.12-1  
               autoconf-2.63-1  gcc-libs-4.3.3-1  db-4.7.25-2  perl-5.10.0-4  
               automake-1.10.2-1  binutils-2.19-1  bison-2.4.1-1  
               bridge-utils-1.4-2  bzip2-1.0.5-3  zlib-1.2.3.3-3  
               openssl-0.9.8j-1  run-parts-2.30-1  ca-certificates-20080809-5  
               cracklib-2.8.13-1  device-mapper-1.02.29-1  e2fsprogs-1.41.3-2  
               libgcrypt-1.4.3-2  popt-1.14-1  cryptsetup-1.0.6-2  
               dhcpcd-4.0.7-1  dialog-1.1_20080819-1  dmraid-1.0.0.rc14-2  
               dnsutils-9.5.0.P2-1  dosfstools-3.0.1-1  ed-1.1-2  
               eventlog-0.2.9-1  filesystem-2009.01-1  fakeroot-1.12.1-1  
               file-4.26-1  flex-2.5.35-1  fuse-2.7.4-1  gmp-4.2.4-1.1  
               mpfr-2.3.2-2  gcc-4.3.3-1  gettext-0.17-2  pcre-7.8-1  
               glib2-2.18.4-1  gpm-1.20.5-2  groff-1.20.1-1  grub-0.97-15  
               hdparm-9.6-1  sqlite3-3.6.10-1  heimdal-1.2.1-3  
               hwdetect-2009.01-1  ifenslave-1.1.0-4  util-linux-ng-2.14-1  
               udev-135-1  initscripts-2009.01-1  iptables-1.4.2-1  
               iputils-20071127-2  iwlwifi-3945-ucode-15.28.2.8-1  
               iwlwifi-4965-ucode-228.57.2.23-1  jfsutils-1.1.13-1  
               klibc-1.5.15-1  klibc-extras-2.5-2  klibc-kbd-1.15.20080312-8  
               klibc-module-init-tools-3.5-1  klibc-udev-135-2  
               mkinitcpio-0.5.23-1  module-init-tools-3.5-1  
               kernel26-2.6.28.2-1  libevent-1.4.8-2  libsasl-2.1.22-7  
               libldap-2.3.43-3  libpcap-1.0.0-1  tar-1.21-1  libtool-2.2.6a-1  
               links-2.2-2  linux-atm-2.5.0-1  logrotate-3.7.7-3  
               lvm2-2.02.43-1  madwifi-utils-0.9.4.3844-1  
               madwifi-0.9.4.3844-3  man-pages-3.17-1  mdadm-2.6.8-1  
               mlocate-0.21.1-1  nano-2.0.9-1  ndiswrapper-utils-1.53-1  
               ndiswrapper-1.53-4  expat-2.0.1-2  dbus-core-1.2.4-1  
               wpa_supplicant-0.5.11-1  netcfg-2.1.2-1  nfsidmap-0.21-2  
               nfs-utils-1.1.3-2  ntfs-3g-2009.1.1-1  pam-1.0.3-1  
               openssh-5.1p1-2  openvpn-2.0.9-4  pciutils-3.0.3-1  
               pcmciautils-015-2  ppp-2.4.4-7  pptpclient-1.7.2-1  
               procinfo-19-3  procps-3.2.7-5  psmisc-22.6-2  
               reiserfsprogs-3.6.21-1  rp-pppoe-3.10-1  rt2500-1.1.0_B4-26  
               rt2x00-rt61-fw-1.2-3  rt2x00-rt71w-fw-1.8-3  sdparm-1.03-2  
               shadow-4.1.2.1-2  syslog-ng-2.1.3-2  tiacx-20080210-8  
               vi-7.2.65-1  iproute2-2.6.28-1  vpnc-0.5.3-1  wget-1.11.4-1  
               which-2.20-1  wlan-ng26-utils-0.2.9-1  xfsprogs-2.10.2-1  

Total Download Size:    150.67 MB
Total Installed Size:   482.61 MB

:: Retrieving packages from core...
:: Retrieving packages from extra...
checking package integrity...
checking for file conflicts...
error: could not prepare transaction
klibc: /usr/lib/klibc/include/asm/Kbuild exists in filesystem
klibc: /usr/lib/klibc/include/asm/a.out.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/acpi.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/agp.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/alternative-asm.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/alternative.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/apic.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/apicdef.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/arch_hooks.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/asm-offsets.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/atomic.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/atomic_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/atomic_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/auxvec.h exists in filesystem
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
klibc: /usr/lib/klibc/include/asm/debugreg.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/delay.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/desc.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/desc_defs.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/device.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/div64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/dma-mapping.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/dma.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/dmi.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/dwarf2.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/e820.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/edac.h exists in filesystem
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
klibc: /usr/lib/klibc/include/asm/hardirq.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/hardirq_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/hardirq_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/highmem.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/hpet.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/hw_irq.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/hypertransport.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/i387.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/i8253.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/i8259.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/ia32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/ia32_unistd.h exists in filesystem
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
klibc: /usr/lib/klibc/include/asm/irq_regs.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/irq_regs_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/irq_regs_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/irqflags.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/ist.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/k8.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/kdebug.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/kexec.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/kmap_types.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/kprobes.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/ldt.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/lguest.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/lguest_hcall.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/linkage.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/local.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-default/apm.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-default/do_timer.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-default/entry_arch.h exists in filesystem
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
klibc: /usr/lib/klibc/include/asm/mach-generic/mach_apic.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-generic/mach_apicdef.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-generic/mach_ipi.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-generic/mach_mpparse.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-generic/mach_mpspec.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-voyager/do_timer.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/mach-voyager/entry_arch.h exists in filesystem
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
klibc: /usr/lib/klibc/include/asm/nmi.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/numa.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/numa_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/numa_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/numaq.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/page.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/page_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/page_64.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/param.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/paravirt.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/parport.h exists in filesystem
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
klibc: /usr/lib/klibc/include/asm/time.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/timer.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/timex.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/tlb.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/tlbflush.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/topology.h exists in filesystem
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
klibc: /usr/lib/klibc/include/asm/vga.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/vgtod.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/vic.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/vm86.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/vmi.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/vmi_time.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/voyager.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/vsyscall.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/xen/hypercall.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/xen/hypervisor.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/xen/interface.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/xor.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/xor_32.h exists in filesystem
klibc: /usr/lib/klibc/include/asm/xor_64.h exists in filesystem
Errors occurred, no packages were upgraded.

---

### Post by Nepherte on 2009-02-02
This problem has been on the frontpage of archlinux.org for a while. Here's the solution to your problem: [http://www.archlinux.org/news/411/](http://www.archlinux.org/news/411/)

---

### Post by handy on 2009-02-02
***@stonecoldjha:***  It is worth bookmarking the following link & referring to it from time to time.

It will help to keep you out of trouble with Arch:

*_[http://bbs.archlinux.org/viewtopic.php?id=57205](http://bbs.archlinux.org/viewtopic.php?id=57205)_*

The info' on this page can quickly get you out of serious trouble also (the above link is incorporated into it):

*_[http://ubuntuforums.org/showpost.php?p=6283883&postcount=3](http://ubuntuforums.org/showpost.php?p=6283883&postcount=3)_*

---

