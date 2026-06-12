---
title: "Installing Ubuntu on an Apple Xserve G5"
date: 2008-05-21
forum: Apple Hardware Users
---

### Post by fbristow on 2008-05-21
Hi everyone.

I've been having lots of fun over the last couple of days trying to install Ubuntu Hardy on an Apple XServe G5.  While I wouldn't normally be having such issues, this is somewhat of a special circumstance.

The XServe in question is a "Cluster Node" version of the XServe line.  What this means is that it has no internal DVD/CD drive and it has no video card.

We have figured out how to get the machine to boot from an external firewire DVD drive to the yaboot installer, so this part is not much of an issue.

It is important to note that we have successfully installed Debian Etch on an identical box, and we can indeed install Etch on this box, but we would much prefer to use the Ubuntu server distribution.  We have successfully installed a base Ubuntu installation by first installing Debian Etch to the system on a small partition and then installing Ubuntu to a larger partition using debootsrap, but we cannot get the system to boot.  It displays some information to the serial console, then fails at the same point that the installer fails when it is booting up.  The messages that are displayed can be seen below.


The biggest issue that we are encountering is using the Serial console as an output display.  We can get some initial kernel messages being printed to the serial console, but we cannot get any further than a certain point.

So, my question is this: are there any special kernel parameters that we are missing that need to be supplied so that the Ubuntu server kernel will continue to spit its output to the serial console?

We are passing the following kernel parameters as it stands, and what follows is the output that is printed to the serial console:
```

Apple RackMac3,1 5.1.7f2 BootROM built on 12/09/04 at 10:58:45
Copyright 1994-2004 Apple Computer, Inc.
All Rights Reserved.

Welcome to Open Firmware, the system time and date is: 14:47:24 05/21/2008

To continue booting, type "mac-boot" and press return.
To shut down, type "shut-down" and press return.

 ok
0 > setenv input-device scca  ok
0 > setenv output-device scca  ok
0 > boot /ht/pci@5/firewire@e/node@00d04b200070042b/sbp-2@c000/disk@0:,\install\yaboot
sbp2:Open ->login?
speed=ffffffff 2 2 load-size=25624 adler32=aa6b7e8e

Loading ELF



sbp2:Open ->login?
speed=ffffffff 2 2
sbp2:Open ->login?
speed=ffffffff 2 2
sbp2:Open ->login?
speed=ffffffff 2 2
sbp2:Open ->login?
speed=ffffffff 2 2
sbp2:Open ->login?
speed=ffffffff 2 2 Config file read, 2328 bytes














sbp2:Open ->login?
speed=ffffffff 2 2
sbp2:Open ->login?
speed=ffffffff 2 2
sbp2:Open ->login?
speed=ffffffff 2 2
sbp2:Open ->login?
speed=ffffffff 2 2
sbp2:Open ->login?
speed=ffffffff 2 2 Welcome to Ubuntu Server 8.04 (Hardy Heron)!

This is an Ubuntu Server installation CDROM,
built on 20080424.

The default option is 'install'. For maximum
control, you can use the 'expert' option.

If the system fails to boot at all (the typical
symptom is a white screen which doesn't go away),
use 'install video=ofonly' or 'expert video=ofonly'.

Press the tab key for a list of options, or type
'help' for help.

************************************
If in doubt, just press Enter, and if that
doesn't work, type 'install video=ofonly'.
************************************
Welcome to yaboot version 1.3.13
Enter "help" to get some basic usage information

sbp2:Open ->login?
speed=ffffffff 2 2 boot:
* install                    expert                     install-powerpc64
  expert-powerpc64           check                      check-powerpc64
  rescue                     rescue-powerpc64
boot: expert-powerpc64 console=ttyS0,57600n8 DEBIAN_FRONTEND=text
Please wait, loading kernel...

sbp2:Open ->login?
speed=ffffffff 2 2
sbp2:Open ->login?
speed=ffffffff 2 2
sbp2:Open ->login?
speed=ffffffff 2 2
sbp2:Open ->login?
speed=ffffffff 2 2
sbp2:Open ->login?
speed=ffffffff 2 2    Elf64 kernel loaded...
Loading ramdisk...

sbp2:Open ->login?
speed=ffffffff 2 2
sbp2:Open ->login?
speed=ffffffff 2 2
sbp2:Open ->login?
speed=ffffffff 2 2
sbp2:Open ->login?
speed=ffffffff 2 2
sbp2:Open ->login?
speed=ffffffff 2 2 ramdisk loaded at 01d00000, size: 5802 Kbytes
OF stdout device is: /ht@0,f2000000/pci@3/mac-io@7/escc@13000/ch-a@13020
command line: ro ramdisk_size=8192 file=/cdrom/preseed/ubuntu-server.seed priority=low -- consotmemory layout at init:
  alloc_bottom : 00000000022ab000
  alloc_top    : 0000000030000000
  alloc_top_hi : 0000000120000000
  rmo_top      : 0000000030000000
  ram_top      : 0000000120000000
Looking for displays
copying OF device tree ...
Building dt strings...
Building dt structure...
Device tree strings 0x00000000025ac000 -> 0x00000000025ad357
Device tree struct  0x00000000025ae000 -> 0x00000000025c1000
Calling quiesce ...

erasing fff04000  of Micron B1 part
flashing fff04000  of Micron B1 part
swapping blocks
DO-QUIESCE finishedreturning from prom_init
Hello World !
[    0.000000] Starting Linux PPC64 #1 SMP Thu Apr 10 13:55:52 UTC 2008
[    0.000000] -----------------------------------------------------
[    0.000000] ppc64_pft_size                = 0x0
[    0.000000] physicalMemorySize            = 0xa0000000
[    0.000000] htab_address                  = 0xc00000011c000000
[    0.000000] htab_hash_mask                = 0x7ffff
[    0.000000] -----------------------------------------------------
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-16-powerpc64-smp (buildd@ross) (gcc version 4.1.3 20080308 )CF000012

Setup Arch
[    0.000000] [boot]0012 Setup Arch
[    0.000000] Found U3-AGP PCI host bridge.  Firmware bus number: 240->255
[    0.000000] Can't get bus-range for /ht@0,f2000000, assume bus 0
[    0.000000] Found U3-HT PCI host bridge.  Firmware bus number: 0->239
[    0.000000] via-pmu: Server Mode is disabled
[    0.000000] PMU driver v2 initialized for Core99, firmware: 0c
[    0.000000] nvram: Checking bank 0...
[    0.000000] nvram: gen0=426, gen1=425
[    0.000000] nvram: Active bank is: 0
[    0.000000] nvram: OF partition at 0x410
[    0.000000] nvram: XP partition at 0x1020
[    0.000000] nvram: NR partition at 0x1120
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->  1179648
[    0.000000]   Normal    1179648 ->  1179648
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->   524288
[    0.000000]     0:  1048576 ->  1179648
CF000015

Setup Done
[    0.000000] [boot]0015 Setup Done
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 639232
[    0.000000] Policy zone: DMA
[    0.000000] Kernel command line: ro ramdisk_size=8192 file=/cdrom/preseed/ubuntu-server.seedt[    0.000000] mpic: Setting up MPIC " MPIC 1   " version 1.2 at 80040000, max 4 CPUs
[    0.000000] mpic: ISU size: 120, shift: 7, mask: 7f
[    0.000000] mpic: Initializing for 120 sources
[    0.000000] mpic: Setting up MPIC " MPIC 2   " version 1.2 at f8040000, max 4 CPUs
[    0.000000] mpic: ISU size: 124, shift: 7, mask: 7f
[    0.000000] mpic: Initializing for 124 sources
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000003] clocksource: timebase mult[7800001] shift[22] registered
[    0.012358] Console: colour dummy device 80x25
[    0.024303] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.042695] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.057812] freeing bootmem node 0
[    0.109258] Memory: 2470116k/2621440k available (5840k kernel code, 151324k reserved, 784k d)[    0.130148] SLUB: Genslabs=12, HWalign=128, Order=0-1, MinObjects=4, CPUs=2, Nodes=16
[    0.233776] Security Framework initialized
[    0.241587] SELinux:  Disabled at boot.
[    0.249239] AppArmor: AppArmor initialized
[    0.257386] Failure registering capabilities with primary security module.
[    0.271110] Mount-cache hash table entries: 256
[    0.283911] Initializing cgroup subsys ns
smp_core99_probe
[    0.294745] PowerMac SMP probe found 2 cpus
[    0.303112] KeyWest i2c @0xf8001003 irq 16 /u3@0,f8000000/i2c@f8001000
[    0.316033]  channel 0 bus <multibus>
[    0.323323]  channel 1 bus <multibus>
[    0.330631] KeyWest i2c @0x80018000 irq 26 /ht@0,f2000000/pci@3/mac-io@7/i2c@18000
[    0.345722]  channel 0 bus <multibus>
[    0.353029] PMU i2c /ht@0,f2000000/pci@3/mac-io@7/via-pmu@16000/pmu-i2c
[    0.366209]  channel 1 bus <multibus>
[    0.373501]  channel 2 bus <multibus>
[    0.380879] Processor timebase sync using Pulsar i2c clock
[    0.391733] mpic: requesting IPIs ...
smp_core99_kick_cpu
smp_core99_kick_cpu done
[    0.408012] Processor 1 found.
[    0.458570] Brought up 2 CPUs
core99_setup_cpu 0 done
[    0.501310] net_namespace: 120 bytes
[    0.508850] NET: Registered protocol family 16
[    0.517439] IBM eBus Device Driver
Linux ppc64

#1 SMP Thu Apr 10 13:55:52 UTC 2008
[    0.533727] CPU Hotplug not supported by firmware - disabling.
[    0.586828] IOMMU table initialized, virtual merging disabled
[    0.624889] NET: Registered protocol family 8
[    0.633219] NET: Registered protocol family 20
[    0.642222] AppArmor: AppArmor Filesystem Enabled
[    0.645962] Time: timebase clocksource has been installed.
[    0.663258] NET: Registered protocol family 2
[    0.711151] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.726666] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.747957] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.762397] TCP: Hash tables configured (established 524288 bind 65536)
[    0.775261] TCP reno registered
[    0.791235] checking if image is initramfs... it is
[    1.450832] Freeing initrd memory: 3072k freed
[    1.459604] Freeing initrd memory: 2726k freed
[    1.468612] nvram_init: Could not find nvram partition for nvram buffered error logging.
[    1.529968] Registering G5 CPU frequency driver
[    1.538653] Frequency method: i2c/pfunc, Voltage method: i2c/pfunc
[    1.550976] Low: 1800 Mhz, High: 2300 Mhz, Cur: 1800 MHz
[    1.586397] audit: initializing netlink socket (disabled)
[    1.596845] audit(1211381411.348:1): initialized
[    1.606226] Total HugeTLB memory allocated, 0
[    1.618339] VFS: Disk quotas dquot_6.5.1
[    1.625910] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.638941] io scheduler noop registered
[    1.646464] io scheduler anticipatory registered
[    1.655663] io scheduler deadline registered
[    1.664354] io scheduler cfq registered (default)
[    1.673558] PCI: MSI quirk detected. PCI_BUS_FLAGS_NO_MSI set for 0001:00:02.0 subordinate b.[    1.690909] AMD8131 rev 12 detected, disabling PCI-X MMRBC
[    1.748456] Generic RTC Driver v1.07
[    1.756409] RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
[    1.771138] MacIO PCI driver attached to K2 chipset
[    1.781787] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.797049] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.809565] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    2.841981] ide0: Found Apple K2 ATA-6 controller, bus ID 3, irq 39
[    3.431085] mice: PS/2 mouse device common for all mice
[    3.441361] PowerMac i2c bus pmu 2 registered
[    3.449916] PowerMac i2c bus pmu 1 registered
[    3.458594] PowerMac i2c bus mac-io 0 registered
[    3.467797] PowerMac i2c bus u3 1 registered
[    3.476304] PowerMac i2c bus u3 0 registered
[    3.484868] NET: Registered protocol family 1
[    3.493464] swsusp: Registered nosave memory region: 000000007f000000 - 0000000080000000
[    3.509584] turn off boot console udbg0

```

After this we get no console output, so we cannot proceed any further with the installation, or in the case of the debootstrapped system, we cannot proceed with the system as it is.

If anyone else has had any success installing this on such a beast (I realize that it is a little obscure), any help would be appreciated.

Thanks,
Franklin

---

### Post by stream303 on 2008-05-22
I would probably try looking at your yaboot.conf file in the Debian Etch setup first to get some hints about the console.  Should be similar.

I barely remember a friend doing something like this on his intel box with some kernel parameters (once past the openfirmware firewire firewire boot and yaboot comes up) like

serial --unit=0 --speed=57600
terminal --timout=5 serial console

and then if that worked, modifying grub with
console=ttys0,57600n8  (Is something like this in your Etch yaboot.conf file?)

Sorry I couldn't be of more help - this is off the top of my head, and it's late.. :)

---

### Post by fbristow on 2008-05-22
Hi there,
Thanks muchly for your reply.

Unfortunately, the /etc/yaboot.conf file merely does what I am asking the Ubuntu installer to do anyway:

```
## yaboot.conf generated by debian-installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/sda2
device=/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0:
partition=3
root=/dev/sda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
default=Linux
activate

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="console=ttyS0,57600"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="console=ttyS0,57600"
```

The bit above above where it appends parameters to the kernel launching are precisely the parameters that we are passing to the ubuntu installer.

Due to time constraints, we have decided to simply use Debian Lenny (Testing) and the install for that went smoothly.

Thanks again for your reply!

---

### Post by stream303 on 2008-05-23
> **fbristow said:**
> Due to time constraints, we have decided to simply use Debian Lenny (Testing) and the install for that went smoothly.

Good to hear!  I'm running Lenny on my box as well.

I probably don't need to say it, but beware of the recent openssl security problem!

---

### Post by fbristow on 2008-05-23
Thanks for the heads up!  We've updated all of our machines (including this one) with the fixed OpenSSL stuff.

Are you running Debian on one of these Cluster Node G5 XServes?

---

### Post by stream303 on 2008-05-23
I wish!  Just a G5 iMac for now.  Used to run it on an iBook as well but got rid of that - seller's remorse!

---

