---
title: "Linux Generic Kernel"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-07-28
Hey there, I'm looking to see how I can go about switching over to the linux-generic kernel as I just dropped in a dual core processor and with 686 it's not seeing the two cores. When I run uname -a I get: "Linux craig-desktop 2.6.15-28-686 #1 SMP PREEMPT Wed Jul 18 22:57:30 UTC 2007 i686 GNU/Linux" 

So I don't THINK I'm using the generic one. I loaded up the 686 kernel through synaptic with help from another posting. If anyone can help me to load the generic kernel, I'd greatly appreciate it!! THanks folks!

---

### Post by 5-HT on 2007-07-28
hmmm, your 686 kernel does say it has SMP support for the dual cores.
To insall the generic kernel and restricted modules (if required) and have them automagically updated once a new release hits:
```
sudo apt-get install linux-generic linux-restricted-modules-generic
```cheers,

---

### Post by Tumpster on 2007-07-28
I'm getting this:

craig@craig-desktop:~$ sudo apt-get install linux-generic linux-restricted-modules-generic
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-generic
craig@craig-desktop:~$
craig@craig-desktop:~$


Any ideas?

---

### Post by Bachstelze on 2007-07-28
There is no generic kernel in Dapper, as it was introduced in Edgy. To install a SMP kernel in Dapper, install the package *linux-686-smp*.

---

### Post by Tumpster on 2007-07-28
Thats what I did and am running right now but it's not recognizing both my cores for some reason. ANy ideas?

---

### Post by 5-HT on 2007-07-28
> **Tumpster said:**
> Thats what I did and am running right now but it's not recognizing both my cores for some reason. ANy ideas?

Are you using noapic as a boot option?
If you run cat /proc/cpuinfo do both cores show up?
If you run 'top' and press '1' can you cycle through the cpus?

> **HymnToLife said:**
> There is no generic kernel in Dapper, as it was introduced in Edgy. To install a SMP kernel in Dapper, install the package *linux-686-smp*.

Sorry, missed that.

---

### Post by Bachstelze on 2007-07-28
You sure of that ?

```
uname -r
cat /proc/cpuinfo
```

---

### Post by Tumpster on 2007-07-28
craig@craig-desktop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Hammer Family processor - Model Unknown
stepping        : 2
cpu MHz         : 1809.402
cache size      : 1024 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm
bogomips        : 3622.66

craig@craig-desktop:~$

craig@craig-desktop:~$ top

top - 16:57:39 up 11:19,  2 users,  load average: 0.13, 0.07, 0.13
Tasks:  99 total,   1 running,  98 sleeping,   0 stopped,   0 zombie
Cpu0  :  2.6% us,  0.4% sy,  0.0% ni, 97.0% id,  0.0% wa,  0.1% hi,  0.0% si
Mem:   1554312k total,  1447960k used,   106352k free,   372600k buffers
Swap:  2329384k total,        0k used,  2329384k free,   843240k cached

Any advice?

---

### Post by Bachstelze on 2007-07-28
686 kernels are for Intel CPUs, not AMD. What CPU do you have, exactly ?

---

### Post by Tumpster on 2007-07-28
Whoopsies, I thought that might be my trouble. I have this one: [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103588](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103588)

Which kernel would I require!

---

### Post by 5-HT on 2007-07-29
> **Tumpster said:**
> Whoopsies, I thought that might be my trouble. I have this one: [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103588](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103588)

Which kernel would I require!
I'm not too familiar with AMD, but from the link you posted and some searching:
linux-image-amd64-k8 
linux-restricted-modules-amd64-k8

cheers,

---

### Post by Tumpster on 2007-07-29
Awesome I will go home and give this a try and post back!! :)

---

### Post by Bachstelze on 2007-07-29
Wrong again, there is no k8 kernel in Dapper ;) The closest thing to what you're looking for is *linux-k7-smp*. If it still doesn't work, you'll have to update to a more recent Ubuntu release, or compile your kernel yourself.

---

### Post by Tumpster on 2007-07-29
So now:
craig@craig-desktop:~$ uname -r
2.6.15-28-k7
craig@craig-desktop:~$

But still I do not see 2 cores it only shows one. Anything I can do other than load up fiesty?

---

### Post by 5-HT on 2007-07-29
> **HymnToLife said:**
> Wrong again, there is no k8 kernel in Dapper ;) The closest thing to what you're looking for is *linux-k7-smp*. If it still doesn't work, you'll have to update to a more recent Ubuntu release, or compile your kernel yourself.

Really? [quote=packages.ubuntu.com]
**Package linux-image-2.6.15-23-amd64-k8**

 [LIST]
[*][dapper]("http://packages.ubuntu.com/dapper/base/linux-image-2.6.15-23-amd64-k8") (base): Linux kernel image for version 2.6.15 on AMD K8.    
2.6.15-23.39: amd64 [/quote][/LIST]

---

### Post by Tumpster on 2007-07-29
I don't have Ubuntu 64 though, it appears thats for users who have amd AND Ubuntu 64.....

---

### Post by 5-HT on 2007-07-30
> **Tumpster said:**
> I don't have Ubuntu 64 though, it appears thats for users who have amd AND Ubuntu 64.....

Yup, it is--I don't run that kernel but noticed it was merged into a -generic one post Dapper. After taking a look at the kernel config though,  it won't be of much help. 
Both the 686 and k7 kernels you installed had SMP support and should have worked, but your second core wasn't recognized with either. I'm wondering if there's something else going on here. Can you take a  look at 'dmesg' and search for anything either cpu or acpi related that might pinpoint the issue? Are you using acpi? I run a patched real-time kernel for audio work with most acpi support gutted out, and found out that if I disabled acpi completely only one core would be utilized (SMP support was enabled). Are you running any special boot options (like noapic)?

---

### Post by Tumpster on 2007-07-30
Nothing is really wrong nor do I use anything fancy at all to run my computer or upon booting at all. The only other thing I could think of is a possible motherboard flashing is needed? My board came out JUST before the dual cores hit big, it's set to run them but they had not been released yet in mass quanitites so it wasn't prepped at the get go. I wonder if this has something to do with it. The only other thing I've thought about is an upgrade to Fiesty but who knows if that would fix the problem. Any advice?

---

### Post by Tumpster on 2007-07-31
Any other ideas?

---

### Post by Tumpster on 2007-08-01
ANyone?

---

### Post by walkerk on 2007-08-01
> **Tumpster said:**
> ANyone?

give my thread a shot: [http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974) just installs the newest generic kernel. i use it and it recognizes my dual cores

not sure if it'll work w/ dapper but it easily reversed.. (it doesn't remove you working kernels..)

---

### Post by Tumpster on 2007-08-02
I suppose my only option left now is to load up fiesty. Whats better about fiesty over LTS Dapper?

---

### Post by 5-HT on 2007-08-04
> **Tumpster said:**
> I suppose my only option left now is to load up fiesty. Whats better about fiesty over LTS Dapper?

Can you post your 'dmesg' output after booting to try and track down the issue as I suggested earlier? 

Fiesty has new apps, the whole LTS thing is not about 'stability' (loaded term I know, it needs proper definition), it's about support (security/major bug updates) duration. Depending on what the problem is, Fiesty may or may not do you any good. Please post the dmesg output as I suspect there's another issue going on here (the kernels you tried _do have_ SMP support: your cores should show up with them).
cheers,

---

### Post by Tumpster on 2007-08-04
Here it is, as much as I could get:
 0x5fff3040
[17179569.184000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x5fff30c0
[17179569.184000] ACPI: MCFG (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x5fff95c0
[17179569.184000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x5fff9500
[17179569.184000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:3 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: BIOS IRQ0 pin2 override ignored.
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] ACPI: IRQ14 used by override.
[17179569.184000] ACPI: IRQ15 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 68000000 (gap: 60000000:80000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 1809.417 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.512000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.512000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)[17179569.560000] Memory: 1548472k/1572800k available (1977k kernel code, 23040k reserved, 605k data, 288k init, 655296k highmem)
[17179569.560000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.640000] Calibrating delay using timer specific routine.. 3622.53 BogoMIPS (lpj=7245062)
[17179569.640000] Security Framework v1.0.0 initialized
[17179569.640000] SELinux:  Disabled at boot.
[17179569.640000] Mount-cache hash table entries: 512
[17179569.640000] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179569.640000] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179569.640000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.640000] CPU: L2 Cache: 1024K (64 bytes/line)
[17179569.640000] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[17179569.640000] mtrr: v2.0 (20020519)
[17179569.640000] CPU: AMD Hammer Family processor - Model Unknown stepping 02
[17179569.640000] Enabling fast FPU save and restore... done.
[17179569.640000] Enabling unmasked SIMD FPU exception support... done.
[17179569.640000] Checking 'hlt' instruction... OK.
[17179569.656000] checking if image is initramfs... it is
[17179570.196000] Freeing initrd memory: 6618k freed
[17179570.204000] ACPI: Looking for DSDT ... not found!
[17179570.208000] ENABLING IO-APIC IRQs
[17179570.216000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179570.356000] NET: Registered protocol family 16
[17179570.356000] EISA bus registered
[17179570.356000] ACPI: bus type pci registered
[17179570.356000] PCI: PCI BIOS revision 3.00 entry at 0xfb410, last bus=5
[17179570.356000] PCI: Using MMCONFIG
[17179570.356000] ACPI: Subsystem revision 20051216
[17179570.364000] ACPI: Interpreter enabled
[17179570.364000] ACPI: Using IOAPIC for interrupt routing
[17179570.364000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.364000] PCI: Probing PCI hardware (bus 00)
[17179570.372000] PCI: Transparent bridge - 0000:00:09.0
[17179570.372000] Boot video device is 0000:05:00.0
[17179570.372000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.448000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179570.448000] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 7 9 10 11 12 14 15)
[17179570.448000] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[17179570.452000] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[17179570.452000] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[17179570.452000] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179570.452000] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[17179570.452000] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179570.452000] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[17179570.452000] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179570.452000] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179570.452000] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[17179570.452000] ACPI: PCI Interrupt Link [LUB2] (IRQs *3 4 5 7 9 10 11 12 14 15)
[17179570.452000] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179570.456000] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[17179570.456000] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[17179570.456000] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179570.456000] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[17179570.456000] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[17179570.456000] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[17179570.456000] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[17179570.456000] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[17179570.456000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[17179570.456000] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[17179570.460000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0, disabled.
[17179570.460000] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[17179570.460000] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[17179570.460000] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[17179570.460000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[17179570.460000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[17179570.460000] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0, disabled.
[17179570.460000] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[17179570.460000] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[17179570.464000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.464000] pnp: PnP ACPI init
[17179570.472000] pnp: PnP ACPI: found 13 devices
[17179570.472000] PnPBIOS: Disabled by ACPI PNP
[17179570.472000] PCI: Using ACPI for IRQ routing
[17179570.472000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.472000] PCI: Cannot allocate resource region 0 of device 0000:03:00.0
[17179570.472000] PCI: Cannot allocate resource region 2 of device 0000:05:00.0
[17179570.472000] PCI: Cannot allocate resource region 0 of device 0000:05:00.1
[17179570.552000] pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
[17179570.552000] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
[17179570.552000] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
[17179570.552000] pnp: 00:00: ioport range 0x4480-0x44ff could not be reserved
[17179570.552000] pnp: 00:00: ioport range 0x4800-0x487f has been reserved
[17179570.552000] pnp: 00:00: ioport range 0x4880-0x48ff has been reserved
[17179570.552000] PCI: Bridge: 0000:00:09.0
[17179570.552000]   IO window: d000-dfff
[17179570.552000]   MEM window: fe900000-fe9fffff
[17179570.552000]   PREFETCH window: fea00000-feafffff
[17179570.552000] PCI: Bridge: 0000:00:0b.0
[17179570.552000]   IO window: c000-cfff
[17179570.552000]   MEM window: fe800000-fe8fffff
[17179570.552000]   PREFETCH window: fe700000-fe7fffff
[17179570.552000] PCI: Bridge: 0000:00:0c.0
[17179570.552000]   IO window: b000-bfff
[17179570.552000]   MEM window: fe600000-fe6fffff
[17179570.552000]   PREFETCH window: fe500000-fe5fffff
[17179570.552000] PCI: Bridge: 0000:00:0d.0
[17179570.552000]   IO window: a000-afff
[17179570.552000]   MEM window: fe400000-fe4fffff
[17179570.552000]   PREFETCH window: fe300000-fe3fffff
[17179570.552000] PCI: Bridge: 0000:00:0e.0
[17179570.552000]   IO window: 9000-9fff
[17179570.552000]   MEM window: fe200000-fe2fffff
[17179570.552000]   PREFETCH window: c8000000-d7ffffff
[17179570.552000] PCI: Setting latency timer of device 0000:00:09.0 to 64
[17179570.552000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[17179570.552000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[17179570.552000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[17179570.552000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[17179570.552000] audit: initializing netlink socket (disabled)
[17179570.552000] audit(1186233066.552:1): initialized
[17179570.552000] highmem bounce pool size: 64 pages
[17179570.552000] VFS: Disk quotas dquot_6.5.1
[17179570.552000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.552000] Initializing Cryptographic API
[17179570.552000] io scheduler noop registered
[17179570.552000] io scheduler anticipatory registered
[17179570.552000] io scheduler deadline registered
[17179570.552000] io scheduler cfq registered
[17179570.556000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[17179570.556000] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[17179570.556000] assign_interrupt_mode Found MSI capability
[17179570.556000] Allocate Port Service[pcie00]
[17179570.556000] Allocate Port Service[pcie03]
[17179570.556000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[17179570.556000] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[17179570.556000] assign_interrupt_mode Found MSI capability
[17179570.556000] Allocate Port Service[pcie00]
[17179570.556000] Allocate Port Service[pcie03]
[17179570.556000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[17179570.556000] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[17179570.556000] assign_interrupt_mode Found MSI capability
[17179570.556000] Allocate Port Service[pcie00]
[17179570.556000] Allocate Port Service[pcie03]
[17179570.556000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[17179570.556000] pcie_portdrv_probe->Dev[005d:10de] has invalid IRQ. Check vendor BIOS
[17179570.556000] assign_interrupt_mode Found MSI capability
[17179570.556000] Allocate Port Service[pcie00]
[17179570.556000] Allocate Port Service[pcie03]
[17179570.556000] isapnp: Scanning for PnP cards...
[17179570.908000] isapnp: No Plug & Play device found
[17179570.920000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179570.920000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.920000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.920000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179570.920000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.920000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.924000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.924000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.924000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.924000] mice: PS/2 mouse device common for all mice
[17179570.924000] EISA: Probing bus 0 at eisa.0
[17179570.924000] Cannot allocate resource for EISA slot 4
[17179570.924000] EISA: Detected 0 cards.
[17179570.924000] NET: Registered protocol family 2
[17179570.944000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179570.964000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.964000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179570.964000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.964000] TCP: Hash tables configured (established 262144 bind 65536)
[17179570.964000] TCP reno registered
[17179570.964000] TCP bic registered
[17179570.964000] NET: Registered protocol family 1
[17179570.964000] NET: Registered protocol family 8
[17179570.964000] NET: Registered protocol family 20
[17179570.964000] Using IPI Shortcut mode
[17179570.964000] ACPI wakeup devices:
[17179570.964000] HUB0 XVR0 XVR1 XVR2 XVR3 USB0 USB2 MMAC MMCI UAR1
[17179570.964000] ACPI: (supports S0 S1 S4 S5)
[17179570.964000] Freeing unused kernel memory: 288k freed
[17179571.008000] vga16fb: initializing
[17179571.008000] vga16fb: mapped to 0xc00a0000
[17179571.120000] Console: switching to colour frame buffer device 80x25
[17179571.120000] fb0: VGA16 VGA frame buffer device
[17179572.180000] Capability LSM initialized
[17179572.312000] ACPI: Fan [FAN] (on)
[17179572.316000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179572.316000] ACPI: Thermal Zone [THRM] (22 C)
[17179572.800000] SCSI subsystem initialized
[17179572.800000] ACPI: bus type scsi registered
[17179572.800000] libata version 1.20 loaded.
[17179572.800000] sata_nv 0000:00:07.0: version 0.8
[17179572.800000] **** SET: Misaligned resource pointer: df876b02 Type 07 Len 0
[17179572.800000] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[17179572.800000] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 23 (level, low) -> IRQ 217
[17179572.800000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[17179572.800000] ata1: SATA max UDMA/133 cmd 0x9F0 ctl 0xBF2 bmdma 0xF600 irq 217
[17179572.800000] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xB72 bmdma 0xF608 irq 217
[17179573.004000] ata1: no device found (phy stat 00000000)
[17179573.004000] scsi0 : sata_nv
[17179573.208000] ata2: no device found (phy stat 00000000)
[17179573.208000] scsi1 : sata_nv
[17179573.208000] **** SET: Misaligned resource pointer: df876a02 Type 07 Len 0
[17179573.208000] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[17179573.208000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 22 (level, low) -> IRQ 225
[17179573.208000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[17179573.208000] ata3: SATA max UDMA/133 cmd 0x9E0 ctl 0xBE2 bmdma 0xF100 irq 225
[17179573.208000] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xB62 bmdma 0xF108 irq 225
[17179573.412000] ata3: no device found (phy stat 00000000)
[17179573.412000] scsi2 : sata_nv
[17179573.616000] ata4: no device found (phy stat 00000000)
[17179573.616000] scsi3 : sata_nv
[17179573.616000] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[17179573.616000] NFORCE-CK804: chipset revision 162
[17179573.616000] NFORCE-CK804: not 100% native mode: will probe irqs later
[17179573.616000] NFORCE-CK804: BIOS didn't set cable bits correctly. Enabling workaround.
[17179573.616000] NFORCE-CK804: 0000:00:06.0 (rev a2) UDMA133 controller
[17179573.616000]     ide0: BM-DMA at 0xfb00-0xfb07, BIOS settings: hda:DMA, hdb:DMA
[17179573.616000]     ide1: BM-DMA at 0xfb08-0xfb0f, BIOS settings: hdc:DMA, hdd:DMA
[17179573.616000] Probing IDE interface ide0...
[17179573.904000] hda: SAMSUNG SP0802N, ATA DISK drive
[17179574.184000] hdb: Maxtor 7Y250P0, ATA DISK drive
[17179574.240000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.248000] Probing IDE interface ide1...
[17179574.984000] hdc: _NEC DVD_RW ND-3520A, ATAPI CD/DVD-ROM drive
[17179575.768000] hdd: LITE-ON DVD SOHD-167T, ATAPI CD/DVD-ROM drive
[17179575.824000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.832000] hda: max request size: 1024KiB
[17179575.844000] hda: 156368016 sectors (80060 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(133)
[17179575.848000] hda: cache flushes supported
[17179575.848000]  hda: hda2 hda3 < hda5 >
[17179575.876000] hdb: max request size: 1024KiB
[17179575.876000] hdb: 490234752 sectors (251000 MB) w/7936KiB Cache, CHS=30515/255/63, UDMA(133)
[17179575.876000] hdb: cache flushes supported
[17179575.876000]  hdb: hdb1 < hdb5 >
[17179575.892000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179575.892000] Uniform CD-ROM driver Revision: 3.20
[17179576.048000] hdd: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
[17179576.296000] usbcore: registered new driver usbfs
[17179576.296000] usbcore: registered new driver hub
[17179576.300000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179576.300000] **** SET: Misaligned resource pointer: dfa576c2 Type 07 Len 0
[17179576.300000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[17179576.300000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 21 (level, low) -> IRQ 233
[17179576.300000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179576.300000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179576.316000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[17179576.316000] ohci_hcd 0000:00:02.0: irq 233, io mem 0xfebff000
[17179576.372000] hub 1-0:1.0: USB hub found
[17179576.372000] hub 1-0:1.0: 10 ports detected
[17179576.400000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[17179576.476000] **** SET: Misaligned resource pointer: dfa573c2 Type 07 Len 0
[17179576.476000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[17179576.476000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 20 (level, low) -> IRQ 50
[17179576.476000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[17179576.476000] ehci_hcd 0000:00:02.1: EHCI Host Controller
[17179576.476000] ehci_hcd 0000:00:02.1: debug port 1
[17179576.476000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[17179576.476000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[17179576.476000] ehci_hcd 0000:00:02.1: irq 50, io mem 0xfebfe000
[17179576.476000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179576.476000] hub 2-0:1.0: USB hub found
[17179576.476000] hub 2-0:1.0: 10 ports detected
[17179576.580000] **** SET: Misaligned resource pointer: dfa570c2 Type 07 Len 0
[17179576.580000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[17179576.580000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 217
[17179576.580000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[17179576.580000] forcedeth: using HIGHDMA
[17179576.820000] ohci_hcd 0000:00:02.0: wakeup
[17179577.100000] eth0: forcedeth.c: subsystem: 01462:7125 bound to 0000:00:0a.0[17179577.156000] Attempting manual resume
[17179577.188000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.200000] kjournald starting.  Commit interval 5 seconds
[17179577.204000] usb 1-7: new full speed USB device using ohci_hcd and address 2
[17179585.900000] ieee80211_crypt: registered algorithm 'NULL'
[17179585.900000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[17179585.900000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179585.980000] mrv8k: Marvel 8xxx Wireless driver, 0.0.2
[17179585.980000] mrv8k: Copyright(c) 2005 Luc Saillard <luc@saillard.org>
[17179585.980000] mrv8k: mrv8k_init_one: enter
[17179585.980000] **** SET: Misaligned resource pointer: dfad3302 Type 07 Len 0
[17179585.980000] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[17179585.980000] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 58
[17179585.980000] mrv8k: bar1 (0xfe9d0000) relocated at 0xf89c0000
[17179585.980000] mrv8k: bar2 (0xfe9e0000) relocated at 0xf89e0000
[17179586.004000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[17179586.004000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[17179586.408000] Linux video capture interface: v1.00
[17179586.616000] input: PC Speaker as /class/input/input1
[17179586.696000] Real Time Clock Driver v1.12
[17179586.704000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179586.772000] mrv8k: Firmware 'mrv8k-b.fw' not available or load failed.
[17179586.772000] mrv8k: mrv8k_init_one: return -2
[17179586.772000] mrv8k: Command SET_RADIO. len=12 state=off preamble=auto
[17179586.772000] mrv8k: queue command (f7d1d600)
[17179586.772000] mrv8k: kickoff command (f7d1d600)
[17179586.856000] parport: PnPBIOS parport detected.
[17179586.856000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179586.884000] NET: Registered protocol family 17
[17179586.896000] FDC 0 is a post-1991 82077
[17179586.904000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179586.944000] logips2pp: Detected unknown logitech mouse model 127
[17179586.956000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4D11
[17179586.956000] usbcore: registered new driver usblp
[17179586.956000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[17179587.396000] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input2[17179587.412000] ts: Compaq touchscreen protocol output
[17179587.800000] ACPI: PCI interrupt for device 0000:01:07.0 disabled
[17179587.800000] mrv8k: mrv8k_init_one: return -2
[17179587.800000] mrv8k: probe of 0000:01:07.0 failed with error -2
[17179587.816000] gameport: EMU10K1 is pci0000:01:08.1/gameport0, io 0xde00, speed 1217kHz
[17179587.816000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179587.816000] **** SET: Misaligned resource pointer: f7f5bb02 Type 07 Len 0
[17179587.816000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[17179587.816000] ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 66
[17179587.816000] saa7133[0]: found at 0000:01:09.0, rev: 209, irq: 66, latency: 32, mmio: 0xfe9ff000
[17179587.816000] saa7133[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[17179587.816000] saa7133[0]: board init: gpio is 40
[17179587.816000] **** SET: Misaligned resource pointer: f7f5bb02 Type 07 Len 0
[17179587.816000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[17179587.816000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 74
[17179587.920000] saa7133[0]: Huh, no eeprom present (err=-5)?
[17179587.920000] saa7133[0]: registered device video0 [v4l2]
[17179587.920000] saa7133[0]: registered device vbi0
[17179587.928000] **** SET: Misaligned resource pointer: f78417c2 Type 07 Len 0
[17179587.928000] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[17179587.928000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 82
[17179587.928000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[17179587.928000] sky2 v1.4 addr 0xfe600000 irq 82 Yukon-EC (0xb6) rev 1
[17179587.928000] sky2 eth1: addr 00:11:09:da:22:73
[17179587.932000] saa7134 ALSA driver for DMA sound loaded
[17179587.932000] saa7133[0]/alsa: saa7133[0] at 0xfe9ff000 irq 66 registered as card -1
[17179588.928000] lp0: using parport0 (interrupt-driven).
[17179588.988000] fuse init (API version 7.3)
[17179589.016000] usbcore: registered new driver usbserial
[17179589.016000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[17179589.016000] usbcore: registered new driver usbserial_generic
[17179589.016000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
[17179589.020000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Handspring Visor / Palm OS
[17179589.020000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 3.5
[17179589.020000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 5.0
[17179589.020000] usbcore: registered new driver visor
[17179589.020000] drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver
[17179589.060000] Adding 2329384k swap on /dev/hda5.  Priority:-1 extents:1 across:2329384k
[17179589.200000] EXT3 FS on hda2, internal journal
[17179589.336000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179589.336000] md: bitmap version 4.39
[17179589.824000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179591.668000] NET: Registered protocol family 10
[17179591.668000] lo: Disabled Privacy Extensions
[17179591.668000] IPv6 over IPv4 tunneling driver
[17179595.136000] cdrom: open failed.
[17179600.408000] ACPI: Power Button (FF) [PWRF]
[17179600.408000] ACPI: Power Button (CM) [PWRB]
[17179600.500000] ibm_acpi: ec object not found
[17179600.528000] pcc_acpi: loading...
[17179601.060000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.50.4)
[17179601.064000] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[17179602.548000] eth0: no IPv6 routers present
[17179605.956000] ppdev: user-space parallel port driver
[17179607.276000] Linux agpgart interface v0.101 (c) Dave Jones
[17179607.316000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179607.320000] [fglrx] Maximum main memory to use for locked dma buffers: 1414 MBytes.
[17179607.320000] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[17179607.372000] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 74
[17179607.908000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179607.908000] apm: overridden by ACPI.
[17179608.768000] [fglrx:firegl_unlock] *ERROR* Process 4736 using kernel context 0
[17179617.004000] Bluetooth: Core ver 2.8
[17179617.004000] NET: Registered protocol family 31
[17179617.004000] Bluetooth: HCI device and connection manager initialized
[17179617.004000] Bluetooth: HCI socket layer initialized
[17179617.040000] Bluetooth: L2CAP ver 2.8
[17179617.040000] Bluetooth: L2CAP socket layer initialized
[17179617.044000] Bluetooth: RFCOMM socket layer initialized
[17179617.044000] Bluetooth: RFCOMM TTY layer initialized
[17179617.044000] Bluetooth: RFCOMM ver 1.7
[17179752.048000] UDF-fs: No VRS found
[17179752.136000] UDF-fs: No VRS found
[17179752.332000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179752.376000] ISO 9660 Extensions: RRIP_1991A
craig@craig-desktop:~$

---

### Post by Tumpster on 2007-08-05
There it all is for you.....

---

### Post by 5-HT on 2007-08-05
> **Tumpster said:**
> There it all is for you.....

> **Tumpster said:**
> Nothing is really wrong nor do I use anything fancy at all to run my computer or upon booting at all. The only other thing I could think of is a possible motherboard flashing is needed? My board came out JUST before the dual cores hit big, it's set to run them but they had not been released yet in mass quanitites so it wasn't prepped at the get go. I wonder if this has something to do with it. The only other thing I've thought about is an upgrade to Fiesty but who knows if that would fix the problem. Any advice?

Looks like a BIOS update may do the trick.
[http://www.nabble.com/opteron-175:-only-one-core-recognized-t3978125.html](http://www.nabble.com/opteron-175:-only-one-core-recognized-t3978125.html)

---

### Post by Tumpster on 2007-08-06
So i made the bootable cd, got the bios utility up but when I try to flash I get errors, it asks for file and i input the file and it says source file not found but on a dir search it shows it right on the cd!! What is going on?

---

### Post by Tumpster on 2007-08-06
Disregard!!! I got it working, I just forgot to add the extension to the file and flashed the motherboard properly and all is well!! I have two cores showing now!! Thanks to all that helped!!! :)



P.S. WHich kernel is best to run?

---

### Post by 5-HT on 2007-08-06
> **Tumpster said:**
>  I have two cores showing now!! Thanks to all that helped!!! :)
P.S. WHich kernel is best to run?
Glad you got it! The k7 kernel will be your best bet, but the 686 kernel will work fine as well.
cheers,

---

### Post by Tumpster on 2007-08-07
Is there any performance difference or anything different between the two being run???

---

