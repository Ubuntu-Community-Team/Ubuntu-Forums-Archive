---
title: "Ubuntu 11.10 on a Power7 LPAR - cdrom mount problems"
date: 2011-08-31
forum: Apple Hardware Users
---

### Post by ds2k5 on 2011-08-31
Hello,
i try to install Ubuntu 11.10 (build 08312011)
on a LPAR of a Power7 System.
But the problem is that the installer is unable to mount the media.

   &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; [!!] Detect and mount CD-ROM &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
   &#9474;                                                                       &#9474;
   &#9474; Your installation CD-ROM couldn't be mounted. This probably means     &#9474;
   &#9474; that the CD-ROM was not in the drive. If so you can insert it and try &#9474;
   &#9474; again.                                                                &#9474;
   &#9474;                                                                       &#9474;
   &#9474; Retry mounting the CD-ROM?                                            &#9474;
   &#9474;                                                                       &#9474;
   &#9474;     <Yes>                                                    <No>     &#9474;
   &#9474;                                                                       &#9474;
   &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

if i exit the installer to the shell
i see only that on kernel modul is loaded but not used

~ # uname -a
Linux (none) 3.0.0-9-powerpc64-smp #14-Ubuntu SMP Tue Aug 23 21:24:01 UTC 2011 ppc64 GNU/Linux


~ # lsmod
Module                  Size  Used by
usb_storage            69394  0 

What can i do to mount the media ?

Thanks




boot: expert-powerpc64
Please wait, loading kernel...
   Elf64 kernel loaded...
Loading ramdisk...
ramdisk loaded at 04c80000, size: 6117 Kbytes
OF stdout device is: /vdevice/vty@30000000
Preparing to boot Linux version 3.0.0-9-powerpc64-smp (buildd@adare) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-7ubuntu2) ) #14-Ubuntu SMP Tue Aug 23 21:24:01 UTC 2011 (Ubuntu 3.0.0-9.14-powerpc64-smp 3.0.3)
Max number of cores passed to firmware: 256 (NR_CPUS = 1024)
Calling ibm,client-architecture-support... done
command line: ro ramdisk_size=8192 file=/cdrom/preseed/ubuntu.seed priority=low -- 
memory layout at init:
  memory_limit : 0000000000000000 (16 MB aligned)
  alloc_bottom : 000000000527a000
  alloc_top    : 0000000010000000
  alloc_top_hi : 0000000010000000
  rmo_top      : 0000000010000000
  ram_top      : 0000000010000000
instantiating rtas at 0x000000000eea0000... done
boot cpu hw idx 0
copying OF device tree...
Building dt strings...
Building dt structure...
Device tree strings 0x000000000537b000 -> 0x000000000537c563
Device tree struct  0x000000000537d000 -> 0x0000000005390000
Calling quiesce...
returning from prom_init
[    0.000000] Using pSeries machine description
[    0.000000] Using 1TB segments
[    0.000000] Found initrd at 0xc000000004c80000:0xc000000005279512
[    0.000000] bootconsole [udbg0] enabled
[    0.000000] Partition configured for 4 cpus.
[    0.000000] CPU maps initialized for 4 threads per core
[    0.000000] Starting Linux PPC64 #14-Ubuntu SMP Tue Aug 23 21:24:01 UTC 2011
[    0.000000] -----------------------------------------------------
[    0.000000] ppc64_pft_size                = 0x1a
[    0.000000] physicalMemorySize            = 0x80000000
[    0.000000] htab_hash_mask                = 0x7ffff
[    0.000000] -----------------------------------------------------
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-9-powerpc64-smp (buildd@adare) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-7ubuntu2) ) #14-Ubuntu SMP Tue Aug 23 21:24:01 UTC 2011 (Ubuntu 3.0.0-9.14-powerpc64-smp 3.0.3)
[    0.000000] [boot]0012 Setup Arch
[    0.000000] EEH: No capable adapters found
[    0.000000] PPC64 nvram contains 15360 bytes
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00080000
[    0.000000]   Normal   empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00080000
[    0.000000] [boot]0015 Setup Done
[    0.000000] PERCPU: Embedded 12 pages/cpu @c000000001600000 s17280 r0 d31872 u262144
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 517120
[    0.000000] Policy zone: DMA
[    0.000000] Kernel command line: ro ramdisk_size=8192 file=/cdrom/preseed/ubuntu.seed priority=low -- 
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] freeing bootmem node 0
[    0.000000] Memory: 2017864k/2097152k available (17588k kernel code, 79288k reserved, 1716k data, 2337k bss, 6516k init)
[    0.000000] SLUB: Genslabs=15, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=256
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:512 nr_irqs:512 16
[    0.000000] clocksource: timebase mult[7d0000] shift[22] registered
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [hvc0] enabled, bootconsole disabled
[    0.000000] console [hvc0] enabled, bootconsole disabled
[    0.000000] allocated 16777216 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.018576] pid_max: default: 32768 minimum: 301
[    0.018616] Security Framework initialized
[    0.018643] AppArmor: AppArmor initialized
[    0.018659] Yama: becoming mindful.
[    0.018987] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.019839] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.028262] Mount-cache hash table entries: 256
[    0.029007] Initializing cgroup subsys cpuacct
[    0.029035] Initializing cgroup subsys memory
[    0.029140] Initializing cgroup subsys devices
[    0.029160] Initializing cgroup subsys freezer
[    0.029183] Initializing cgroup subsys net_cls
[    0.029202] Initializing cgroup subsys blkio
[    0.029225] Initializing cgroup subsys perf_event
[    0.029261] ftrace: allocating 23143 entries in 137 pages
[    0.048516] POWER7 performance monitor hardware support registered
[    0.049355] Brought up 4 CPUs
[    0.049408] Enabling Asymmetric SMT scheduling
[    0.049590] devtmpfs: initialized
[    0.069346] print_constraints: dummy: 
[    0.069401] NET: Registered protocol family 16
[    0.069583] Trying to unpack rootfs image as initramfs...
[    0.079317] PCI: Probing PCI hardware
[    0.079351] io_event_irq: No ibm,io-events on system! IO Event interrupt disabled.
[    0.088282] bio: create slab <bio-0> at 0
[    0.088520] vgaarb: loaded
[    0.088769] SCSI subsystem initialized
[    0.088901] usbcore: registered new interface driver usbfs
[    0.088943] usbcore: registered new interface driver hub
[    0.089023] usbcore: registered new device driver usb
[    0.089191] NetLabel: Initializing
[    0.089209] NetLabel:  domain hash size = 128
[    0.089230] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.089271] NetLabel:  unlabeled traffic allowed by default
[    0.089347] Switching to clocksource timebase
[    0.108190] Switched to NOHz mode on CPU #2
[    0.108194] Switched to NOHz mode on CPU #1
[    0.108197] Switched to NOHz mode on CPU #3
[    0.108200] Switched to NOHz mode on CPU #0
[    0.148347] AppArmor: AppArmor Filesystem Enabled
[    0.158229] NET: Registered protocol family 2
[    0.158405] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.159499] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.169609] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.170072] TCP: Hash tables configured (established 262144 bind 65536)
[    0.170105] TCP reno registered
[    0.170128] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.178235] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.178408] NET: Registered protocol family 1
[    0.179441] vio 30000000: Warning: IOMMU dma not supported: mask 0xffffffffffffffff, table unavailable
[    0.217856] IOMMU table initialized, virtual merging enabled
[    0.254090] vio 4000: Warning: IOMMU dma not supported: mask 0xffffffffffffffff, table unavailable
[    0.254160] vio 4001: Warning: IOMMU dma not supported: mask 0xffffffffffffffff, table unavailable
[    0.254222] vio 4002: Warning: IOMMU dma not supported: mask 0xffffffffffffffff, table unavailable
[    0.254287] vio 4004: Warning: IOMMU dma not supported: mask 0xffffffffffffffff, table unavailable
[    0.254671] audit: initializing netlink socket (disabled)
[    0.254707] type=2000 audit(1314806821.192:1): initialized
[    0.840122] HugeTLB registered 16 MB page size, pre-allocated 0 pages
[    0.848211] HugeTLB registered 16 GB page size, pre-allocated 0 pages
[    0.858701] VFS: Disk quotas dquot_6.5.2
[    0.858812] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.859710] fuse init (API version 7.16)
[    0.859848] msgmni has been set to 3943
[    0.868592] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.868689] io scheduler noop registered
[    0.868713] io scheduler deadline registered
[    0.868780] io scheduler cfq registered (default)
[    0.869262] pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[    0.869356] Linux agpgart interface v0.103
[    0.878929] brd: module loaded
[    0.879715] loop: module loaded



                                                                            

BusyBox v1.18.4 (Ubuntu 1:1.18.4-2ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

~ # dmesg
[    0.000000] Allocated 655360 bytes for 1024 pacas at c00000000ee00000
[    0.000000] Using pSeries machine description
[    0.000000] Page orders: linear mapping = 24, virtual = 12, io = 12, vmemmap = 24
[    0.000000] Using 1TB segments
[    0.000000] Found initrd at 0xc000000004c80000:0xc000000005279512
[    0.000000] bootconsole [udbg0] enabled
[    0.000000] Partition configured for 4 cpus.
[    0.000000] CPU maps initialized for 4 threads per core
[    0.000000]  (thread shift is 2)
[    0.000000] Freed 651264 bytes for unused pacas
[    0.000000] Starting Linux PPC64 #14-Ubuntu SMP Tue Aug 23 21:24:01 UTC 2011
[    0.000000] -----------------------------------------------------
[    0.000000] ppc64_pft_size                = 0x1a
[    0.000000] physicalMemorySize            = 0x80000000
[    0.000000] htab_hash_mask                = 0x7ffff
[    0.000000] -----------------------------------------------------
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-9-powerpc64-smp (buildd@adare) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-7ubuntu2) ) #14-Ubuntu SMP Tue Aug 23 21:24:01 UTC 2011 (Ubuntu 3.0.0-9.14-powerpc64-smp 3.0.3)
[    0.000000] [boot]0012 Setup Arch
[    0.000000] Node 0 Memory: 0x0-0x80000000
[    0.000000] EEH: No capable adapters found
[    0.000000] PPC64 nvram contains 15360 bytes
[    0.000000] Using shared processor idle loop
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00080000
[    0.000000]   Normal   empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00080000
[    0.000000] On node 0 totalpages: 524288
[    0.000000]   DMA zone: 7168 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 517120 pages, LIFO batch:31
[    0.000000] [boot]0015 Setup Done
[    0.000000] PERCPU: Embedded 12 pages/cpu @c000000001600000 s17280 r0 d31872 u262144
[    0.000000] pcpu-alloc: s17280 r0 d31872 u262144 alloc=1*1048576
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 517120
[    0.000000] Policy zone: DMA
[    0.000000] Kernel command line: ro ramdisk_size=8192 file=/cdrom/preseed/ubuntu.seed priority=low -- 
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] freeing bootmem node 0
[    0.000000] Memory: 2017864k/2097152k available (17588k kernel code, 79288k reserved, 1716k data, 2337k bss, 6516k init)
[    0.000000] SLUB: Genslabs=15, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=256
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:512 nr_irqs:512 16
[    0.000000] pic: no ISA interrupt controller
[    0.000000] time_init: decrementer frequency = 512.000000 MHz
[    0.000000] time_init: processor frequency   = 3000.000000 MHz
[    0.000000] clocksource: timebase mult[7d0000] shift[22] registered
[    0.000000] clockevent: decrementer mult[83126e97] shift[32] cpu[0]
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [hvc0] enabled, bootconsole disabled
[    0.000000] allocated 16777216 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.018576] pid_max: default: 32768 minimum: 301
[    0.018616] Security Framework initialized
[    0.018643] AppArmor: AppArmor initialized
[    0.018659] Yama: becoming mindful.
[    0.018987] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.019839] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.028262] Mount-cache hash table entries: 256
[    0.029007] Initializing cgroup subsys cpuacct
[    0.029035] Initializing cgroup subsys memory
[    0.029140] Initializing cgroup subsys devices
[    0.029160] Initializing cgroup subsys freezer
[    0.029183] Initializing cgroup subsys net_cls
[    0.029202] Initializing cgroup subsys blkio
[    0.029225] Initializing cgroup subsys perf_event
[    0.029261] ftrace: allocating 23143 entries in 137 pages
[    0.048511] irq: irq 2 on host null mapped to virtual irq 16
[    0.048516] POWER7 performance monitor hardware support registered
[    0.049355] Brought up 4 CPUs
[    0.049378] Node 0 CPUs: 0-3
[    0.049408] Enabling Asymmetric SMT scheduling
[    0.049590] devtmpfs: initialized
[    0.069346] print_constraints: dummy: 
[    0.069401] NET: Registered protocol family 16
[    0.069583] Trying to unpack rootfs image as initramfs...
[    0.079317] PCI: Probing PCI hardware
[    0.079345] PCI: Probing PCI hardware done
[    0.079351] io_event_irq: No ibm,io-events on system! IO Event interrupt disabled.
[    0.088282] bio: create slab <bio-0> at 0
[    0.088520] vgaarb: loaded
[    0.088769] SCSI subsystem initialized
[    0.088851] libata version 3.00 loaded.
[    0.088901] usbcore: registered new interface driver usbfs
[    0.088943] usbcore: registered new interface driver hub
[    0.089023] usbcore: registered new device driver usb
[    0.089191] NetLabel: Initializing
[    0.089209] NetLabel:  domain hash size = 128
[    0.089230] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.089271] NetLabel:  unlabeled traffic allowed by default
[    0.089347] Switching to clocksource timebase
[    0.108190] Switched to NOHz mode on CPU #2
[    0.108194] Switched to NOHz mode on CPU #1
[    0.108197] Switched to NOHz mode on CPU #3
[    0.108200] Switched to NOHz mode on CPU #0
[    0.148347] AppArmor: AppArmor Filesystem Enabled
[    0.158229] NET: Registered protocol family 2
[    0.158405] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.159499] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.169609] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.170072] TCP: Hash tables configured (established 262144 bind 65536)
[    0.170105] TCP reno registered
[    0.170128] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.178235] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.178408] NET: Registered protocol family 1
[    0.178444] PCI: CLS 0 bytes, default 128
[    0.178578] RTAS daemon started
[    0.179344] RTAS: event: 2, Type: Platform Error, Severity: 2
[    0.179432] irq: irq 655360 on host null mapped to virtual irq 17
[    0.179441] vio 30000000: Warning: IOMMU dma not supported: mask 0xffffffffffffffff, table unavailable
[    0.179531] irq: irq 655362 on host null mapped to virtual irq 18
[    0.217856] IOMMU table initialized, virtual merging enabled
[    0.217981] irq: irq 655363 on host null mapped to virtual irq 19
[    0.236089] irq: irq 655364 on host null mapped to virtual irq 20
[    0.254090] vio 4000: Warning: IOMMU dma not supported: mask 0xffffffffffffffff, table unavailable
[    0.254160] vio 4001: Warning: IOMMU dma not supported: mask 0xffffffffffffffff, table unavailable
[    0.254222] vio 4002: Warning: IOMMU dma not supported: mask 0xffffffffffffffff, table unavailable
[    0.254287] vio 4004: Warning: IOMMU dma not supported: mask 0xffffffffffffffff, table unavailable
[    0.254405] irq: irq 589825 on host null mapped to virtual irq 21
[    0.254671] audit: initializing netlink socket (disabled)
[    0.254707] type=2000 audit(1314806821.192:1): initialized
[    0.840122] HugeTLB registered 16 MB page size, pre-allocated 0 pages
[    0.848211] HugeTLB registered 16 GB page size, pre-allocated 0 pages
[    0.858701] VFS: Disk quotas dquot_6.5.2
[    0.858812] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.859710] fuse init (API version 7.16)
[    0.859848] msgmni has been set to 3943
[    0.868592] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.868689] io scheduler noop registered
[    0.868713] io scheduler deadline registered
[    0.868780] io scheduler cfq registered (default)
[    0.869262] pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[    0.869356] Linux agpgart interface v0.103
[    0.878929] brd: module loaded
[    0.879715] loop: module loaded
[    0.879822] Uniform Multi-Platform E-IDE driver
[    0.879872] ide-gd driver 1.18
[    0.879895] ide-cd driver 5.00
[    0.879989] Fixed MDIO Bus: probed
[    0.880014] tun: Universal TUN/TAP device driver, 1.6
[    0.880040] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.888188] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.888250] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.888304] uhci_hcd: USB Universal Host Controller Interface driver
[    0.888452] mousedev: PS/2 mouse device common for all mice
[    0.888703] device-mapper: uevent: version 1.0.3
[    0.888817] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    0.889069] Freeing initrd memory: 6120k freed
[    0.889202] TCP cubic registered
[    0.889384] NET: Registered protocol family 10
[    0.889932] NET: Registered protocol family 17
[    0.889964] Registering the dns_resolver key type
[    0.890064] registered taskstats version 1
[    0.989114] /build/buildd/linux-3.0.0/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[    0.998514] Freeing unused kernel memory: 6516k freed
>[    1.039698] udevd[68]: starting version 173
[    1.580129] ioctl32(console-type:136): Unknown cmd fd(0) cmd(00005603){t:'V';sz:0} arg(ffed7e7c) on /dev/console
[   19.089212] Initializing USB Mass Storage driver...
[   19.089240] usbcore: registered new interface driver usb-storage
[   19.089243] USB Mass Storage support registered.


/bin # discover-ibm 
ibmvscsic:IBM Virtual SCSI
ibmvscsic:IBM Virtual SCSI
ibmveth:IBM Virtual Ethernet

---

### Post by rsavage on 2011-08-31
I had a similar problem when trying to boot from a USB device that I had copied the CD onto.  My solution is on the rambling posts on this page [http://ubuntuforums.org/showthread.php?t=780320&page=4](http://ubuntuforums.org/showthread.php?t=780320&page=4) .  Don't know if this helps?

---

### Post by ds2k5 on 2011-08-31
hi rsavage,
no, i cant see some SCSI Devices

~ # ls -la /dev
drwxr-xr-x    8 root     root          2900 Aug 31 16:48 .
drwxrwxr-x   18 root     root             0 Aug 31 17:04 ..
drwxr-xr-x    2 root     root           520 Aug 31 16:48 block
drwxr-xr-x    2 root     root          2240 Aug 31 16:48 char
crw-------    1 root     root        5,   1 Aug 31 17:03 console
lrwxrwxrwx    1 root     root            11 Aug 31 16:48 core -> /proc/kcore
crw-------    1 root     root       10,  60 Aug 31 17:03 cpu_dma_latency
crw-------    1 root     root       10,  61 Aug 31 17:03 ecryptfs
lrwxrwxrwx    1 root     root            13 Aug 31 16:48 fd -> /proc/self/fd
crw-rw-rw-    1 root     root        1,   7 Aug 31 17:03 full
crw-rw-rw-    1 root     root       10, 229 Aug 31 17:03 fuse
crw-------    1 root     root      229,   0 Aug 31 19:20 hvc0
crw-------    1 root     root      229,   1 Aug 31 17:03 hvc1
crw-------    1 root     root      229,   2 Aug 31 17:03 hvc2
crw-------    1 root     root      229,   3 Aug 31 17:03 hvc3
crw-------    1 root     root      229,   4 Aug 31 17:03 hvc4
crw-------    1 root     root      229,   5 Aug 31 17:03 hvc5
crw-------    1 root     root      229,   6 Aug 31 17:03 hvc6
crw-------    1 root     root      229,   7 Aug 31 17:03 hvc7
drwxr-xr-x    2 root     root            60 Aug 31 16:48 input
crw-------    1 root     root        1,  11 Aug 31 17:03 kmsg
srw-rw-rw-    1 root     root             0 Aug 31 16:48 log
brw-------    1 root     root        7,   0 Aug 31 17:03 loop0
brw-------    1 root     root        7,   1 Aug 31 17:03 loop1
brw-------    1 root     root        7,   2 Aug 31 17:03 loop2
brw-------    1 root     root        7,   3 Aug 31 17:03 loop3
brw-------    1 root     root        7,   4 Aug 31 17:03 loop4
brw-------    1 root     root        7,   5 Aug 31 17:03 loop5
brw-------    1 root     root        7,   6 Aug 31 17:03 loop6
brw-------    1 root     root        7,   7 Aug 31 17:03 loop7
drwxr-xr-x    2 root     root            60 Aug 31 16:48 mapper
crw-r-----    1 root     root        1,   1 Aug 31 17:03 mem
drwxr-xr-x    2 root     root            60 Aug 31 16:48 net
crw-------    1 root     root       10,  59 Aug 31 17:03 network_latency
crw-------    1 root     root       10,  58 Aug 31 17:03 network_throughput
crw-rw-rw-    1 root     root        1,   3 Aug 31 17:03 null
crw-r-----    1 root     root       10, 144 Aug 31 17:03 nvram
crw-------    1 root     root        1,  12 Aug 31 17:03 oldmem
crw-r-----    1 root     root        1,   4 Aug 31 17:03 port
crw-------    1 root     root       10,   1 Aug 31 17:03 psaux
crw-rw-rw-    1 root     root        5,   2 Aug 31 17:03 ptmx
drwxr-xr-x    2 root     root             0 Aug 31 16:48 pts
brw-------    1 root     root        1,   0 Aug 31 17:03 ram0
brw-------    1 root     root        1,   1 Aug 31 17:03 ram1
brw-------    1 root     root        1,  10 Aug 31 17:03 ram10
brw-------    1 root     root        1,  11 Aug 31 17:03 ram11
brw-------    1 root     root        1,  12 Aug 31 17:03 ram12
brw-------    1 root     root        1,  13 Aug 31 17:03 ram13
brw-------    1 root     root        1,  14 Aug 31 17:03 ram14
brw-------    1 root     root        1,  15 Aug 31 17:03 ram15
brw-------    1 root     root        1,   2 Aug 31 17:03 ram2
brw-------    1 root     root        1,   3 Aug 31 17:03 ram3
brw-------    1 root     root        1,   4 Aug 31 17:03 ram4
brw-------    1 root     root        1,   5 Aug 31 17:03 ram5
brw-------    1 root     root        1,   6 Aug 31 17:03 ram6
brw-------    1 root     root        1,   7 Aug 31 17:03 ram7
brw-------    1 root     root        1,   8 Aug 31 17:03 ram8
brw-------    1 root     root        1,   9 Aug 31 17:03 ram9
crw-rw-rw-    1 root     root        1,   8 Aug 31 17:03 random
crw-r--r--    1 root     root       10,  62 Aug 31 17:03 rfkill
crw-------    1 root     root       10, 231 Aug 31 17:03 snapshot
lrwxrwxrwx    1 root     root            15 Aug 31 16:48 stderr -> /proc/self/fd/2
lrwxrwxrwx    1 root     root            15 Aug 31 16:48 stdin -> /proc/self/fd/0
lrwxrwxrwx    1 root     root            15 Aug 31 16:48 stdout -> /proc/self/fd/1
crw-rw-rw-    1 root     root        5,   0 Aug 31 17:03 tty
crw--w----    1 root     root        4,   0 Aug 31 17:03 tty0
crw--w----    1 root     root        4,   1 Aug 31 17:03 tty1
crw--w----    1 root     root        4,  10 Aug 31 17:03 tty10
crw--w----    1 root     root        4,  11 Aug 31 17:03 tty11
crw--w----    1 root     root        4,  12 Aug 31 17:03 tty12
crw--w----    1 root     root        4,  13 Aug 31 17:03 tty13
crw--w----    1 root     root        4,  14 Aug 31 17:03 tty14
crw--w----    1 root     root        4,  15 Aug 31 17:03 tty15
crw--w----    1 root     root        4,  16 Aug 31 17:03 tty16
crw--w----    1 root     root        4,  17 Aug 31 17:03 tty17
crw--w----    1 root     root        4,  18 Aug 31 17:03 tty18
crw--w----    1 root     root        4,  19 Aug 31 17:03 tty19
crw--w----    1 root     root        4,   2 Aug 31 17:03 tty2
crw--w----    1 root     root        4,  20 Aug 31 17:03 tty20
crw--w----    1 root     root        4,  21 Aug 31 17:03 tty21
crw--w----    1 root     root        4,  22 Aug 31 17:03 tty22
crw--w----    1 root     root        4,  23 Aug 31 17:03 tty23
crw--w----    1 root     root        4,  24 Aug 31 17:03 tty24
crw--w----    1 root     root        4,  25 Aug 31 17:03 tty25
crw--w----    1 root     root        4,  26 Aug 31 17:03 tty26
crw--w----    1 root     root        4,  27 Aug 31 17:03 tty27
crw--w----    1 root     root        4,  28 Aug 31 17:03 tty28
crw--w----    1 root     root        4,  29 Aug 31 17:03 tty29
crw--w----    1 root     root        4,   3 Aug 31 17:03 tty3
crw--w----    1 root     root        4,  30 Aug 31 17:03 tty30
crw--w----    1 root     root        4,  31 Aug 31 17:03 tty31
crw--w----    1 root     root        4,  32 Aug 31 17:03 tty32
crw--w----    1 root     root        4,  33 Aug 31 17:03 tty33
crw--w----    1 root     root        4,  34 Aug 31 17:03 tty34
crw--w----    1 root     root        4,  35 Aug 31 17:03 tty35
crw--w----    1 root     root        4,  36 Aug 31 17:03 tty36
crw--w----    1 root     root        4,  37 Aug 31 17:03 tty37
crw--w----    1 root     root        4,  38 Aug 31 17:03 tty38
crw--w----    1 root     root        4,  39 Aug 31 17:03 tty39
crw--w----    1 root     root        4,   4 Aug 31 17:34 tty4
crw--w----    1 root     root        4,  40 Aug 31 17:03 tty40
crw--w----    1 root     root        4,  41 Aug 31 17:03 tty41
crw--w----    1 root     root        4,  42 Aug 31 17:03 tty42
crw--w----    1 root     root        4,  43 Aug 31 17:03 tty43
crw--w----    1 root     root        4,  44 Aug 31 17:03 tty44
crw--w----    1 root     root        4,  45 Aug 31 17:03 tty45
crw--w----    1 root     root        4,  46 Aug 31 17:03 tty46
crw--w----    1 root     root        4,  47 Aug 31 17:03 tty47
crw--w----    1 root     root        4,  48 Aug 31 17:03 tty48
crw--w----    1 root     root        4,  49 Aug 31 17:03 tty49
crw--w----    1 root     root        4,   5 Aug 31 17:03 tty5
crw--w----    1 root     root        4,  50 Aug 31 17:03 tty50
crw--w----    1 root     root        4,  51 Aug 31 17:03 tty51
crw--w----    1 root     root        4,  52 Aug 31 17:03 tty52
crw--w----    1 root     root        4,  53 Aug 31 17:03 tty53
crw--w----    1 root     root        4,  54 Aug 31 17:03 tty54
crw--w----    1 root     root        4,  55 Aug 31 17:03 tty55
crw--w----    1 root     root        4,  56 Aug 31 17:03 tty56
crw--w----    1 root     root        4,  57 Aug 31 17:03 tty57
crw--w----    1 root     root        4,  58 Aug 31 17:03 tty58
crw--w----    1 root     root        4,  59 Aug 31 17:03 tty59
crw--w----    1 root     root        4,   6 Aug 31 17:03 tty6
crw--w----    1 root     root        4,  60 Aug 31 17:03 tty60
crw--w----    1 root     root        4,  61 Aug 31 17:03 tty61
crw--w----    1 root     root        4,  62 Aug 31 17:03 tty62
crw--w----    1 root     root        4,  63 Aug 31 17:03 tty63
crw--w----    1 root     root        4,   7 Aug 31 17:03 tty7
crw--w----    1 root     root        4,   8 Aug 31 17:03 tty8
crw--w----    1 root     root        4,   9 Aug 31 17:03 tty9
crw-------    1 root     root        5,   3 Aug 31 17:03 ttyprintk
crw-r-----    1 root     root       10, 223 Aug 31 17:03 uinput
crw-rw-rw-    1 root     root        1,   9 Aug 31 17:03 urandom
crw-------    1 root     root      252,   0 Aug 31 17:03 usbmon0
crw-------    1 root     root        7,   0 Aug 31 17:03 vcs
crw-------    1 root     root        7,   1 Aug 31 17:03 vcs1
crw-------    1 root     root        7,   2 Aug 31 17:03 vcs2
crw-------    1 root     root        7,   3 Aug 31 17:03 vcs3
crw-------    1 root     root        7,   4 Aug 31 17:03 vcs4
crw-------    1 root     root        7, 128 Aug 31 17:03 vcsa
crw-------    1 root     root        7, 129 Aug 31 17:03 vcsa1
crw-------    1 root     root        7, 130 Aug 31 17:03 vcsa2
crw-------    1 root     root        7, 131 Aug 31 17:03 vcsa3
crw-------    1 root     root        7, 132 Aug 31 17:03 vcsa4
crw-------    1 root     root       10,  63 Aug 31 17:03 vga_arbiter
crw-rw-rw-    1 root     root        1,   5 Aug 31 17:03 zero

---

