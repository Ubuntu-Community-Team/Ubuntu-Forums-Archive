---
title: "Linux Mint: Help with wireless card"
date: 2012-04-24
forum: Any Other OS
---

### Post by Adhso on 2012-04-24
I have the cisco AE2500 wireless USB adapter and i can't get it to work with my linux mint.  I have the 64-bit version if that helps.

---

### Post by Perfect Storm on 2012-04-25
Moved to Other OS/Distro Talk.

---

### Post by chili555 on 2012-04-25
Please insert the device and run and post:```
lsusb
```Which Mint version are you running?```
lsb_release -rc
```Have you tried anything yet to install it?

---

### Post by Adhso on 2012-04-25
> **chili555 said:**
> Please insert the device and run and post:```
lsusb
```Which Mint version are you running?```
lsb_release -rc
```Have you tried anything yet to install it?

When i put in lsusb it said:
>   Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 002 Device 003: ID 13b1:003a Linksys
  Bus 002 Device 004: ID 18e3:9106 Fitipower Integrated Technology Inc
  Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
  Bus 005 Device 002: ID 046d:c22d Logitech, Inc.


and when i put in lsb_ release -rc it said
>   
Release:           12
  Codename:      lisa
  

---

### Post by chili555 on 2012-04-25
If you've searched this forum for your usb.id 13b1:003a, you'll find very little, maybe no success. Here is an example: [http://ubuntuforums.org/showthread.php?t=1805830&page=9](http://ubuntuforums.org/showthread.php?t=1805830&page=9)> So my solution was to go out and buy a new wireless card Thanks for all the help everybody!However, I love a mystery and my wireless works just fine! If you'd like to try, I'll be happy to assist. If you'd like to go shopping, I'll cheer you on. What is your preference?

---

### Post by Adhso on 2012-04-25
> **chili555 said:**
> If you've searched this forum for your usb.id 13b1:003a, you'll find very little, maybe no success. Here is an example: [http://ubuntuforums.org/showthread.php?t=1805830&page=9](http://ubuntuforums.org/showthread.php?t=1805830&page=9)However, I love a mystery and my wireless works just fine! If you'd like to try, I'll be happy to assist. If you'd like to go shopping, I'll cheer you on. What is your preference?

Well i have had this wireless adapter for along time and i really don't want  to go out and buy a new one so i would love it if you could get it working!!!  :P

---

### Post by chili555 on 2012-04-25
> **CrYph1x said:**
> Well i have had this wireless adapter for along time and i really don't want  to go out and buy a new one so i would love it if you could get it working!!!  :PThere is certainly no guarantee that we can, but let's try. Download the attached file to your desktop. Right-click it and select *Extract Here*. Open a terminal and do:```
cd Desktop/xp_64
sudo ndiswrapper -i bcmwlhigh5.inf
sudo modprobe ndiswrapper
```Do we have lift-off? If not, please post:```
dmesg | grep ndis
```Thanks and good luck!

---

### Post by Adhso on 2012-04-25
> **chili555 said:**
> There is certainly no guarantee that we can, but let's try. Download the attached file to your desktop. Right-click it and select *Extract Here*. Open a terminal and do:```
cd Desktop/xp_64
sudo ndiswrapper -i bcmwlhigh5.inf
sudo modprobe ndiswrapper
```Do we have lift-off? If not, please post:```
dmesg | grep ndis
```Thanks and good luck!

I did all of that and i got 
>   installing bcmwlhigh5 ...
  couldn't find section "Linksys_AE1200.files.NTamd64" -
  installation may be incomplete
  couldn't find section "Linksys_AE2500.files.NTamd64" -
  installation may be incomplete
  

Thats what happend after i did the first command and i tried all the others and nothing really happened.

---

### Post by chili555 on 2012-04-25
I suggest you try this: [http://ubuntuforums.org/showpost.php?p=11811107&postcount=79](http://ubuntuforums.org/showpost.php?p=11811107&postcount=79)

I will be away for a while. I'll look in later to see how you're doing.

---

### Post by Adhso on 2012-04-25
> **chili555 said:**
> I suggest you try this: [http://ubuntuforums.org/showpost.php?p=11811107&postcount=79](http://ubuntuforums.org/showpost.php?p=11811107&postcount=79)

I will be away for a while. I'll look in later to see how you're doing.

Well i did everything that tut said and it still didn't work :(  I don't think i'm going to be able to get it to work.

---

### Post by chili555 on 2012-04-25
Are there any clues here?```
dmesg | grep ndis
```

---

### Post by Adhso on 2012-04-25
when i put in dmesg i get  
>   [    0.392920] pnp 00:00: [io  0x0000-0x0cf7 window]
  [    0.392921] pnp 00:00: [io  0x0d00-0xffff window]
  [    0.392923] pnp 00:00: [mem 0x000a0000-0x000bffff window]
  [    0.392925] pnp 00:00: [mem 0x000d0000-0x000dffff window]
  [    0.392926] pnp 00:00: [mem 0xd0000000-0xdfffffff window]
  [    0.392928] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
  [    0.392971] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
  [    0.393034] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
  [    0.393035] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
  [    0.393076] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
  [    0.393106] pnp 00:02: [dma 4]
  [    0.393107] pnp 00:02: [io  0x0000-0x000f]
  [    0.393109] pnp 00:02: [io  0x0081-0x0083]
  [    0.393110] pnp 00:02: [io  0x0087]
  [    0.393112] pnp 00:02: [io  0x0089-0x008b]
  [    0.393113] pnp 00:02: [io  0x008f]
  [    0.393114] pnp 00:02: [io  0x00c0-0x00df]
  [    0.393134] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
  [    0.393141] pnp 00:03: [io  0x0070-0x0071]
  [    0.393151] pnp 00:03: [irq 8]
  [    0.393170] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
  [    0.393178] pnp 00:04: [io  0x0061]
  [    0.393194] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
  [    0.393200] pnp 00:05: [io  0x00f0-0x00ff]
  [    0.393236] pnp 00:05: [irq 13]
  [    0.393256] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
  [    0.393273] pnp 00:06: [mem 0xfed00000-0xfed003ff]
  [    0.393290] pnp 00:06: Plug and Play ACPI device, IDs PNP0103 (active)
  [    0.393341] pnp 00:07: [io  0x0060]
  [    0.393343] pnp 00:07: [io  0x0064]
  [    0.393344] pnp 00:07: [mem 0xfec00000-0xfec00fff]
  [    0.393346] pnp 00:07: [mem 0xfee00000-0xfee00fff]
  [    0.393381] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
  [    0.393383] system 00:07: [mem 0xfee00000-0xfee00fff] has been reserved
  [    0.393386] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
  [    0.393481] pnp 00:08: [io  0x0010-0x001f]
  [    0.393483] pnp 00:08: [io  0x0022-0x003f]
  [    0.393484] pnp 00:08: [io  0x0062-0x0063]
  [    0.393485] pnp 00:08: [io  0x0065-0x006f]
  [    0.393487] pnp 00:08: [io  0x0072-0x007f]
  [    0.393488] pnp 00:08: [io  0x0080]
  [    0.393490] pnp 00:08: [io  0x0084-0x0086]
  [    0.393494] pnp 00:08: [io  0x0088]
  [    0.393496] pnp 00:08: [io  0x008c-0x008e]
  [    0.393497] pnp 00:08: [io  0x0090-0x009f]
  [    0.393498] pnp 00:08: [io  0x00a2-0x00bf]
  [    0.393500] pnp 00:08: [io  0x00b1]
  [    0.393501] pnp 00:08: [io  0x00e0-0x00ef]
  [    0.393503] pnp 00:08: [io  0x04d0-0x04d1]
  [    0.393504] pnp 00:08: [io  0x040b]
  [    0.393505] pnp 00:08: [io  0x04d6]
  [    0.393507] pnp 00:08: [io  0x0c00-0x0c01]
  [    0.393508] pnp 00:08: [io  0x0c14]
  [    0.393509] pnp 00:08: [io  0x0c50-0x0c51]
  [    0.393511] pnp 00:08: [io  0x0c52]
  [    0.393512] pnp 00:08: [io  0x0c6c]
  [    0.393513] pnp 00:08: [io  0x0c6f]
  [    0.393515] pnp 00:08: [io  0x0cd0-0x0cd1]
  [    0.393516] pnp 00:08: [io  0x0cd2-0x0cd3]
  [    0.393517] pnp 00:08: [io  0x0cd4-0x0cd5]
  [    0.393519] pnp 00:08: [io  0x0cd6-0x0cd7]
  [    0.393520] pnp 00:08: [io  0x0cd8-0x0cdf]
  [    0.393522] pnp 00:08: [io  0x0800-0x089f]
  [    0.393523] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
  [    0.393525] pnp 00:08: [io  0x0b00-0x0b0f]
  [    0.393526] pnp 00:08: [io  0x0b20-0x0b3f]
  [    0.393528] pnp 00:08: [io  0x0900-0x090f]
  [    0.393529] pnp 00:08: [io  0x0910-0x091f]
  [    0.393530] pnp 00:08: [io  0xfe00-0xfefe]
  [    0.393532] pnp 00:08: [io  0x0060]
  [    0.393533] pnp 00:08: [io  0x0064]
  [    0.393535] pnp 00:08: [mem 0xffb80000-0xffbfffff]
  [    0.393536] pnp 00:08: [mem 0xfec10000-0xfec1001f]
  [    0.393580] system 00:08: [io  0x04d0-0x04d1] has been reserved
  [    0.393583] system 00:08: [io  0x040b] has been reserved
  [    0.393585] system 00:08: [io  0x04d6] has been reserved
  [    0.393586] system 00:08: [io  0x0c00-0x0c01] has been reserved
  [    0.393588] system 00:08: [io  0x0c14] has been reserved
  [    0.393590] system 00:08: [io  0x0c50-0x0c51] has been reserved
  [    0.393592] system 00:08: [io  0x0c52] has been reserved
  [    0.393594] system 00:08: [io  0x0c6c] has been reserved
  [    0.393596] system 00:08: [io  0x0c6f] has been reserved
  [    0.393598] system 00:08: [io  0x0cd0-0x0cd1] has been reserved
  [    0.393600] system 00:08: [io  0x0cd2-0x0cd3] has been reserved
  [    0.393602] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
  [    0.393604] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
  [    0.393606] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
  [    0.393608] system 00:08: [io  0x0800-0x089f] has been reserved
  [    0.393611] system 00:08: [io  0x0b00-0x0b0f] has been reserved
  [    0.393613] system 00:08: [io  0x0b20-0x0b3f] has been reserved
  [    0.393615] system 00:08: [io  0x0900-0x090f] has been reserved
  [    0.393617] system 00:08: [io  0x0910-0x091f] has been reserved
  [    0.393619] system 00:08: [io  0xfe00-0xfefe] has been reserved
  [    0.393622] system 00:08: [mem 0xffb80000-0xffbfffff] has been reserved
  [    0.393624] system 00:08: [mem 0xfec10000-0xfec1001f] has been reserved
  [    0.393626] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
  [    0.393724] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
  [    0.393726] pnp 00:09: [io  0x0e00-0x0e0f]
  [    0.393728] pnp 00:09: [io  0x0e80-0x0e8f]
  [    0.393729] pnp 00:09: [io  0x0f40-0x0f4f]
  [    0.393756] system 00:09: [io  0x0e00-0x0e0f] has been reserved
  [    0.393759] system 00:09: [io  0x0e80-0x0e8f] has been reserved
  [    0.393761] system 00:09: [io  0x0f40-0x0f4f] has been reserved
  [    0.393763] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
  [    0.393784] pnp 00:0a: [mem 0xe0000000-0xefffffff]
  [    0.393813] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
  [    0.393816] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
  [    0.393893] pnp 00:0b: [mem 0x00000000-0x0009ffff]
  [    0.393894] pnp 00:0b: [mem 0x000c0000-0x000cffff]
  [    0.393896] pnp 00:0b: [mem 0x000e0000-0x000fffff]
  [    0.393898] pnp 00:0b: [mem 0x00100000-0xcfffffff]
  [    0.393899] pnp 00:0b: [mem 0xfec00000-0xffffffff]
  [    0.393930] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
  [    0.393932] system 00:0b: [mem 0x000c0000-0x000cffff] could not be reserved
  [    0.393935] system 00:0b: [mem 0x000e0000-0x000fffff] could not be reserved
  [    0.393937] system 00:0b: [mem 0x00100000-0xcfffffff] could not be reserved
  [    0.393939] system 00:0b: [mem 0xfec00000-0xffffffff] could not be reserved
  [    0.393942] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
  [    0.394032] pnp: PnP ACPI: found 12 devices
  [    0.394033] ACPI: ACPI bus type pnp unregistered
  [    0.399707] PCI: max bus depth: 1 pci_try_num: 2
  [    0.399725] pci 0000:00:01.0: PCI bridge to [bus 01-01]
  [    0.399728] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
  [    0.399730] pci 0000:00:01.0:   bridge window [mem 0xfe900000-0xfeafffff]
  [    0.399733] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
  [    0.399737] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
  [    0.399739] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
  [    0.399741] pci 0000:00:0a.0:   bridge window [mem 0xfeb00000-0xfebfffff]
  [    0.399744] pci 0000:00:0a.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
  [    0.399747] pci 0000:00:14.4: PCI bridge to [bus 03-03]
  [    0.399748] pci 0000:00:14.4:   bridge window [io  disabled]
  [    0.399753] pci 0000:00:14.4:   bridge window [mem disabled]
  [    0.399756] pci 0000:00:14.4:   bridge window [mem pref disabled]
  [    0.399781] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
  [    0.399784] pci 0000:00:0a.0: setting latency timer to 64
  [    0.399791] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
  [    0.399793] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
  [    0.399795] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
  [    0.399797] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
  [    0.399799] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
  [    0.399800] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
  [    0.399802] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
  [    0.399804] pci_bus 0000:01: resource 1 [mem 0xfe900000-0xfeafffff]
  [    0.399806] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
  [    0.399808] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
  [    0.399810] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
  [    0.399812] pci_bus 0000:02: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
  [    0.399814] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
  [    0.399816] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
  [    0.399818] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
  [    0.399820] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
  [    0.399821] pci_bus 0000:03: resource 8 [mem 0xd0000000-0xdfffffff]
  [    0.399823] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfebfffff]
  [    0.399858] NET: Registered protocol family 2
  [    0.400064] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
  [    0.401466] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
  [    0.404578] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
  [    0.404962] TCP: Hash tables configured (established 524288 bind 65536)
  [    0.404964] TCP reno registered
  [    0.404982] UDP hash table entries: 4096 (order: 5, 131072 bytes)
  [    0.405053] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
  [    0.405216] NET: Registered protocol family 1
  [    0.405225] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
  [    1.168148] pci 0000:01:05.0: Boot video device
  [    1.168156] PCI: CLS 64 bytes, default 64
  [    1.169183] PCI-DMA: Disabling AGP.
  [    1.169309] PCI-DMA: aperture base @ c4000000 size 65536 KB
  [    1.169311] PCI-DMA: using GART IOMMU.
  [    1.169313] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
  [    1.172390] audit: initializing netlink socket (disabled)
  [    1.172416] type=2000 audit(1335364767.168:1): initialized
  [    1.199335] HugeTLB registered 2 MB page size, pre-allocated 0 pages
  [    1.223400] VFS: Disk quotas dquot_6.5.2
  [    1.223445] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
  [    1.224043] fuse init (API version 7.16)
  [    1.224120] msgmni has been set to 11428
  [    1.224750] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
  [    1.224846] io scheduler noop registered
  [    1.224850] io scheduler deadline registered
  [    1.224921] io scheduler cfq registered (default)
  [    1.225227] pcieport 0000:00:0a.0: setting latency timer to 64
  [    1.225262] pcieport 0000:00:0a.0: irq 40 for MSI/MSI-X
  [    1.225395] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
  [    1.225418] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
  [    1.225510] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
  [    1.225514] ACPI: Power Button [PWRB]
  [    1.225542] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
  [    1.225545] ACPI: Power Button [PWRF]
  [    1.225597] ACPI: acpi_idle registered with cpuidle
  [    1.226284] ERST: Table is not found!
  [    1.226348] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
  [    1.273484] Freeing initrd memory: 13420k freed
  [    1.420304] Linux agpgart interface v0.103
  [    1.421014] brd: module loaded
  [    1.421346] loop: module loaded
  [    1.421668] Fixed MDIO Bus: probed
  [    1.421683] PPP generic driver version 2.4.2
  [    1.421716] tun: Universal TUN/TAP device driver, 1.6
  [    1.421717] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
  [    1.421772] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
  [    1.421909] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
  [    1.422021] ehci_hcd 0000:00:12.2: EHCI Host Controller
  [    1.422094] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
  [    1.422119] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
  [    1.422144] ehci_hcd 0000:00:12.2: debug port 1
  [    1.422164] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe8ff800
  [    1.432085] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
  [    1.432216] hub 1-0:1.0: USB hub found
  [    1.432219] hub 1-0:1.0: 6 ports detected
  [    1.432412] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
  [    1.432431] ehci_hcd 0000:00:13.2: EHCI Host Controller
  [    1.432459] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
  [    1.432467] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
  [    1.432487] ehci_hcd 0000:00:13.2: debug port 1
  [    1.432506] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe8ff400
  [    1.444085] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
  [    1.444214] hub 2-0:1.0: USB hub found
  [    1.444217] hub 2-0:1.0: 6 ports detected
  [    1.444366] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
  [    1.444492] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
  [    1.444514] ohci_hcd 0000:00:12.0: OHCI Host Controller
  [    1.444569] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
  [    1.444596] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe8fe000
  [    1.504187] hub 3-0:1.0: USB hub found
  [    1.504229] hub 3-0:1.0: 3 ports detected
  [    1.504361] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
  [    1.504380] ohci_hcd 0000:00:12.1: OHCI Host Controller
  [    1.504414] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
  [    1.504433] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe8fd000
  [    1.564178] hub 4-0:1.0: USB hub found
  [    1.564220] hub 4-0:1.0: 3 ports detected
  [    1.564355] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
  [    1.564375] ohci_hcd 0000:00:13.0: OHCI Host Controller
  [    1.564409] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
  [    1.564436] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe8fc000
  [    1.624182] hub 5-0:1.0: USB hub found
  [    1.624223] hub 5-0:1.0: 3 ports detected
  [    1.624356] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
  [    1.624375] ohci_hcd 0000:00:13.1: OHCI Host Controller
  [    1.624407] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
  [    1.624428] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe8f7000
  [    1.684177] hub 6-0:1.0: USB hub found
  [    1.684219] hub 6-0:1.0: 3 ports detected
  [    1.684317] uhci_hcd: USB Universal Host Controller Interface driver
  [    1.684390] i8042: PNP: No PS/2 controller found. Probing ports directly.
  [    1.684903] serio: i8042 KBD port at 0x60,0x64 irq 1
  [    1.684914] serio: i8042 AUX port at 0x60,0x64 irq 12
  [    1.685009] mousedev: PS/2 mouse device common for all mice
  [    1.685116] rtc_cmos 00:03: RTC can wake from S4
  [    1.685194] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
  [    1.685217] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
  [    1.685300] device-mapper: uevent: version 1.0.3
  [    1.685346] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
  [    1.685387] cpuidle: using governor ladder
  [    1.685389] cpuidle: using governor menu
  [    1.685390] EFI Variables Facility v0.08 2004-May-17
  [    1.685560] TCP cubic registered
  [    1.685640] NET: Registered protocol family 10
  [    1.685986] NET: Registered protocol family 17
  [    1.686001] Registering the dns_resolver key type
  [    1.686084] PM: Hibernation image not present or could not be loaded.
  [    1.686093] registered taskstats version 1
  [    1.703503]   Magic number: 8:483:688
  [    1.703643] rtc_cmos 00:03: setting system clock to 2012-04-25 14:39:28 UTC (1335364768)
  [    1.703658] powernow-k8: Found 1 AMD Athlon(tm) II X4 635 Processor (4 cpu cores) (version 2.20.00)
  [    1.703688] powernow-k8:    0 : pstate 0 (2900 MHz)
  [    1.703689] powernow-k8:    1 : pstate 1 (2200 MHz)
  [    1.703691] powernow-k8:    2 : pstate 2 (1700 MHz)
  [    1.703692] powernow-k8:    3 : pstate 3 (800 MHz)
  [    1.704313] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
  [    1.704316] EDD information not available.
  [    1.705656] Freeing unused kernel memory: 984k freed
  [    1.705877] Write protecting the kernel read-only data: 10240k
  [    1.706118] Freeing unused kernel memory: 20k freed
  [    1.710001] Freeing unused kernel memory: 1400k freed
  [    1.732539] udevd[117]: starting version 173
  [    1.760318] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
  [    1.760346] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
  [    1.760391] r8169 0000:02:00.0: setting latency timer to 64
  [    1.760472] r8169 0000:02:00.0: irq 41 for MSI/MSI-X
  [    1.760831] r8169 0000:02:00.0: eth0: RTL8168e/8111e at 0xffffc90000c72000, d4:85:64:b1:a9:41, XID 0c200000 IRQ 41
  [    1.764128] ahci 0000:00:11.0: version 3.0
  [    1.764191] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
  [    1.764316] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
  [    1.764320] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc
  [    1.765849] scsi0 : ahci
  [    1.766045] scsi1 : ahci
  [    1.767548] scsi2 : ahci
  [    1.768579] scsi3 : ahci
  [    1.768696] ata1: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffd00 irq 22
  [    1.768700] ata2: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffd80 irq 22
  [    1.768703] ata3: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffe00 irq 22
  [    1.768706] ata4: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffe80 irq 22
  [    1.972086] usb 2-2: new high speed USB device number 3 using ehci_hcd
  [    2.088133] ata4: SATA link down (SStatus 0 SControl 300)
  [    2.088177] ata1: SATA link down (SStatus 0 SControl 300)
  [    2.172105] Refined TSC clocksource calibration: 2899.999 MHz.
  [    2.172111] Switching to clocksource tsc
  [    2.220079] usb 2-6: new high speed USB device number 4 using ehci_hcd
  [    2.260090] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
  [    2.260119] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
  [    2.262655] ata3.00: ATAPI: ATAPI   iHAS124   B, AL0S, max UDMA/100
  [    2.263545] ata3.00: configured for UDMA/100
  [    2.266622] ata2.00: ATA-7: SAMSUNG HD103SI, 1AG01118, max UDMA7
  [    2.266626] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
  [    2.273179] ata2.00: configured for UDMA/133
  [    2.273359] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD103SI  1AG0 PQ: 0 ANSI: 5
  [    2.273516] sd 1:0:0:0: Attached scsi generic sg0 type 0
  [    2.273582] sd 1:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
  [    2.273706] sd 1:0:0:0: [sda] Write Protect is off
  [    2.273708] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
  [    2.273732] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
  [    2.274727] scsi 2:0:0:0: CD-ROM            ATAPI    iHAS124   B      AL0S PQ: 0 ANSI: 5
  [    2.278434] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
  [    2.278438] cdrom: Uniform CD-ROM driver Revision: 3.20
  [    2.278554] sr 2:0:0:0: Attached scsi CD-ROM sr0
  [    2.278620] sr 2:0:0:0: Attached scsi generic sg1 type 5
  [    2.357484] usbcore: registered new interface driver uas
  [    2.616036] usb 3-3: new full speed USB device number 2 using ohci_hcd
  [    2.752366]  sda: sda1 sda2
  [    2.752764] sd 1:0:0:0: [sda] Attached SCSI disk
  [    2.753518] Initializing USB Mass Storage driver...
  [    2.754193] scsi4 : usb-storage 2-6:1.0
  [    2.754618] usbcore: registered new interface driver usb-storage
  [    2.754620] USB Mass Storage support registered.
  [    2.799299] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/input/input2
  [    2.799376] generic-usb 0003:046D:C52B.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:12.0-3/input0
  [    2.804396] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.1/input/input3
  [    2.804527] generic-usb 0003:046D:C52B.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:12.0-3/input1
  [    2.813208] generic-usb 0003:046D:C52B.0003: hiddev0,hidraw2: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:12.0-3/input2
  [    2.813225] usbcore: registered new interface driver usbhid
  [    2.813227] usbhid: USB HID core driver
  [    3.056046] usb 5-1: new full speed USB device number 2 using ohci_hcd
  [    3.235269] input: Logitech G510 Gaming Keyboard as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input4
  [    3.235358] generic-usb 0003:046D:C22D.0004: input,hidraw3: USB HID v1.11 Keyboard [Logitech G510 Gaming Keyboard] on usb-0000:00:13.0-1/input0
  [    3.254190] input: Logitech G510 Gaming Keyboard as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.1/input/input5
  [    3.254300] generic-usb 0003:046D:C22D.0005: input,hiddev0,hidraw4: USB HID v1.11 Device [Logitech G510 Gaming Keyboard] on usb-0000:00:13.0-1/input1
  [    3.549143] EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts: (null)
  [    3.752949] scsi 4:0:0:0: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0
  [    3.753572] scsi 4:0:0:1: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
  [    3.754197] scsi 4:0:0:2: Direct-Access     Generic- SM/xD-Picture    1.02 PQ: 0 ANSI: 0
  [    3.754947] scsi 4:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.03 PQ: 0 ANSI: 0 CCS
  [    4.160224] sd 4:0:0:0: Attached scsi generic sg2 type 0
  [    4.160312] sd 4:0:0:1: Attached scsi generic sg3 type 0
  [    4.160394] sd 4:0:0:2: Attached scsi generic sg4 type 0
  [    4.160479] sd 4:0:0:3: Attached scsi generic sg5 type 0
  [    4.166876] sd 4:0:0:0: [sdb] Attached SCSI removable disk
  [    4.167504] sd 4:0:0:1: [sdc] Attached SCSI removable disk
  [    4.168245] sd 4:0:0:2: [sdd] Attached SCSI removable disk
  [    4.168992] sd 4:0:0:3: [sde] Attached SCSI removable disk
  [   14.686650] udevd[408]: starting version 173
  [   14.706361] lp: driver loaded but no devices found
  [   14.725916] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 1022 ss_did 9602
  [   14.725922] shpchp 0000:00:01.0: Cannot reserve MMIO region
  [   14.725989] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
  [   14.755894] wmi: Mapper loaded
  [   14.785603] [drm] Initialized drm 1.1.0 20060810
  [   14.788038] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
  [   14.794004] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
  [   14.794110] SP5100 TCO timer: mmio address 0xfec000f0 already in use
  [   14.803654] MCE: In-kernel MCE decoding enabled.
  [   14.807598] [drm] radeon defaulting to kernel modesetting.
  [   14.807602] [drm] radeon kernel modesetting enabled.
  [   14.808902] EDAC MC: Ver: 2.1.0
  [   14.811759] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
  [   14.811765] radeon 0000:01:05.0: setting latency timer to 64
  [   14.812048] [drm] initializing kernel modesetting (RS880 0x1002:0x9710 0x103C:0x2AB1).
  [   14.812079] [drm] register mmio base: 0xFE9F0000
  [   14.812081] [drm] register mmio size: 65536
  [   14.812755] ATOM BIOS: BR34448.bin
  [   14.812779] radeon 0000:01:05.0: VRAM: 256M 0x00000000C0000000 - 0x00000000CFFFFFFF (256M used)
  [   14.812782] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
  [   14.812831] AMD64 EDAC driver v3.4.0
  [   14.813125] [drm] Detected VRAM RAM=256M, BAR=256M
  [   14.813129] [drm] RAM width 32bits DDR
  [   14.813361] EDAC amd64: DRAM ECC disabled.
  [   14.813370] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
  [   14.813372]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
  [   14.813373]  (Note that use of the override may cause unknown side effects.)
  [   14.815086] [TTM] Zone  kernel: Available graphics memory: 2933554 kiB.
  [   14.815090] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
  [   14.815091] [TTM] Initializing pool allocator.
  [   14.815121] [drm] radeon: 256M of VRAM memory ready
  [   14.815123] [drm] radeon: 512M of GTT memory ready.
  [   14.815138] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
  [   14.815139] [drm] Driver supports precise vblank timestamp query.
  [   14.815157] [drm] radeon: irq initialized.
  [   14.815161] [drm] GART: num cpu pages 131072, num gpu pages 131072
  [   14.816576] [drm] Loading RS780 Microcode
  [   14.827063] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
  [   14.881259] hda_codec: ALC888-VD: BIOS auto-probing.
  [   14.892786] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
  [   14.934215] radeon 0000:01:05.0: WB enabled
  [   14.966053] [drm] ring test succeeded in 1 usecs
  [   14.966144] [drm] radeon: ib pool ready.
  [   14.966202] [drm] ib test succeeded in 0 usecs
  [   14.966455] [drm] Radeon Display Connectors
  [   14.966456] [drm] Connector 0:
  [   14.966457] [drm]   VGA
  [   14.966459] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
  [   14.966460] [drm]   Encoders:
  [   14.966462] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
  [   14.966463] [drm] Connector 1:
  [   14.966464] [drm]   DVI-D
  [   14.966465] [drm]   HPD1
  [   14.966466] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
  [   14.966467] [drm]   Encoders:
  [   14.966468] [drm]     DFP1: INTERNAL_KLDSCP_LVTMA
  [   15.017910] [drm] Radeon display connector VGA-1: Found valid EDID
  [   15.069226] [drm] Radeon display connector DVI-D-1: Found valid EDID
  [   15.069247] [drm] radeon: power management initialized
  [   15.209927] [drm] fb mappable at 0xD0141000
  [   15.209928] [drm] vram apper at 0xD0000000
  [   15.209929] [drm] size 5787648
  [   15.209930] [drm] fb depth is 24
  [   15.209931] [drm]    pitch is 6400
  [   15.209998] fbcon: radeondrmfb (fb0) is primary device
  [   15.210101] Console: switching to colour frame buffer device 200x56
  [   15.210124] fb0: radeondrmfb frame buffer device
  [   15.210126] drm: registered panic notifier
  [   15.210133] [drm] Initialized radeon 2.10.0 20080528 for 0000:01:05.0 on minor 0
  [   15.210512] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
  [   15.210561] HDA Intel 0000:01:05.1: setting latency timer to 64
  [   15.416151] Adding 262136k swap on /host/linuxmint/disks/swap.disk.  Priority:-1 extents:1 across:262136k
  [   15.438218] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro
  [   15.797188] r8169 0000:02:00.0: eth0: link down
  [   15.797911] ADDRCONF(NETDEV_UP): eth0: link is not ready
  [   15.960236] usb 2-2: usbfs: USBDEVFS_CONTROL failed cmd mtp-probe rqt 128 rq 6 len 1024 ret -110
  [   16.029039] ppdev: user-space parallel port driver
  [   16.100820] init: failsafe main process (864) killed by TERM signal
  [   16.214632] Bluetooth: Core ver 2.16
  [   16.214661] NET: Registered protocol family 31
  [   16.214662] Bluetooth: HCI device and connection manager initialized
  [   16.214665] Bluetooth: HCI socket layer initialized
  [   16.214666] Bluetooth: L2CAP socket layer initialized
  [   16.214875] Bluetooth: SCO socket layer initialized
  [   16.216857] Bluetooth: RFCOMM TTY layer initialized
  [   16.216862] Bluetooth: RFCOMM socket layer initialized
  [   16.216864] Bluetooth: RFCOMM ver 1.11
  [   16.217256] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
  [   16.217260] Bluetooth: BNEP filters: protocol multicast
  [   16.444414] radeon 0000:01:05.0: texture bo too small (1600 900 26 0 -> 5785600 have 5763072)
  [   16.444418] radeon 0000:01:05.0: alignments 1600 64 8 256
  [   16.444420] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
  [   17.524359] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
  [   17.882940] init: plymouth-stop pre-start process (1480) terminated with status 1
  [   18.814663] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
  

When i put in the 2nd command nothing happens.

---

### Post by chili555 on 2012-04-25
It looks like ndiswrapper is not loaded. Please try:```
sudo modprobe ndiswrapper
ndiswrapper -l
dmesg | grep ndis
```Please note and post any errors or warnings.

---

### Post by Adhso on 2012-04-25
This is what i get after i did the first command and that d one
>   [    0.393215] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
  [    0.393222] pnp 00:03: [io  0x0070-0x0071]
  [    0.393266] pnp 00:03: [irq 8]
  [    0.393285] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
  [    0.393294] pnp 00:04: [io  0x0061]
  [    0.393310] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
  [    0.393316] pnp 00:05: [io  0x00f0-0x00ff]
  [    0.393359] pnp 00:05: [irq 13]
  [    0.393377] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
  [    0.393395] pnp 00:06: [mem 0xfed00000-0xfed003ff]
  [    0.393411] pnp 00:06: Plug and Play ACPI device, IDs PNP0103 (active)
  [    0.393462] pnp 00:07: [io  0x0060]
  [    0.393464] pnp 00:07: [io  0x0064]
  [    0.393465] pnp 00:07: [mem 0xfec00000-0xfec00fff]
  [    0.393467] pnp 00:07: [mem 0xfee00000-0xfee00fff]
  [    0.393501] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
  [    0.393504] system 00:07: [mem 0xfee00000-0xfee00fff] has been reserved
  [    0.393506] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
  [    0.393602] pnp 00:08: [io  0x0010-0x001f]
  [    0.393604] pnp 00:08: [io  0x0022-0x003f]
  [    0.393605] pnp 00:08: [io  0x0062-0x0063]
  [    0.393606] pnp 00:08: [io  0x0065-0x006f]
  [    0.393608] pnp 00:08: [io  0x0072-0x007f]
  [    0.393609] pnp 00:08: [io  0x0080]
  [    0.393611] pnp 00:08: [io  0x0084-0x0086]
  [    0.393615] pnp 00:08: [io  0x0088]
  [    0.393616] pnp 00:08: [io  0x008c-0x008e]
  [    0.393617] pnp 00:08: [io  0x0090-0x009f]
  [    0.393619] pnp 00:08: [io  0x00a2-0x00bf]
  [    0.393620] pnp 00:08: [io  0x00b1]
  [    0.393622] pnp 00:08: [io  0x00e0-0x00ef]
  [    0.393623] pnp 00:08: [io  0x04d0-0x04d1]
  [    0.393624] pnp 00:08: [io  0x040b]
  [    0.393626] pnp 00:08: [io  0x04d6]
  [    0.393627] pnp 00:08: [io  0x0c00-0x0c01]
  [    0.393629] pnp 00:08: [io  0x0c14]
  [    0.393630] pnp 00:08: [io  0x0c50-0x0c51]
  [    0.393631] pnp 00:08: [io  0x0c52]
  [    0.393633] pnp 00:08: [io  0x0c6c]
  [    0.393634] pnp 00:08: [io  0x0c6f]
  [    0.393635] pnp 00:08: [io  0x0cd0-0x0cd1]
  [    0.393637] pnp 00:08: [io  0x0cd2-0x0cd3]
  [    0.393638] pnp 00:08: [io  0x0cd4-0x0cd5]
  [    0.393640] pnp 00:08: [io  0x0cd6-0x0cd7]
  [    0.393641] pnp 00:08: [io  0x0cd8-0x0cdf]
  [    0.393642] pnp 00:08: [io  0x0800-0x089f]
  [    0.393644] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
  [    0.393646] pnp 00:08: [io  0x0b00-0x0b0f]
  [    0.393647] pnp 00:08: [io  0x0b20-0x0b3f]
  [    0.393649] pnp 00:08: [io  0x0900-0x090f]
  [    0.393650] pnp 00:08: [io  0x0910-0x091f]
  [    0.393651] pnp 00:08: [io  0xfe00-0xfefe]
  [    0.393653] pnp 00:08: [io  0x0060]
  [    0.393654] pnp 00:08: [io  0x0064]
  [    0.393656] pnp 00:08: [mem 0xffb80000-0xffbfffff]
  [    0.393657] pnp 00:08: [mem 0xfec10000-0xfec1001f]
  [    0.393701] system 00:08: [io  0x04d0-0x04d1] has been reserved
  [    0.393703] system 00:08: [io  0x040b] has been reserved
  [    0.393705] system 00:08: [io  0x04d6] has been reserved
  [    0.393707] system 00:08: [io  0x0c00-0x0c01] has been reserved
  [    0.393709] system 00:08: [io  0x0c14] has been reserved
  [    0.393711] system 00:08: [io  0x0c50-0x0c51] has been reserved
  [    0.393713] system 00:08: [io  0x0c52] has been reserved
  [    0.393715] system 00:08: [io  0x0c6c] has been reserved
  [    0.393717] system 00:08: [io  0x0c6f] has been reserved
  [    0.393719] system 00:08: [io  0x0cd0-0x0cd1] has been reserved
  [    0.393721] system 00:08: [io  0x0cd2-0x0cd3] has been reserved
  [    0.393723] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
  [    0.393725] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
  [    0.393727] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
  [    0.393729] system 00:08: [io  0x0800-0x089f] has been reserved
  [    0.393731] system 00:08: [io  0x0b00-0x0b0f] has been reserved
  [    0.393733] system 00:08: [io  0x0b20-0x0b3f] has been reserved
  [    0.393735] system 00:08: [io  0x0900-0x090f] has been reserved
  [    0.393737] system 00:08: [io  0x0910-0x091f] has been reserved
  [    0.393740] system 00:08: [io  0xfe00-0xfefe] has been reserved
  [    0.393742] system 00:08: [mem 0xffb80000-0xffbfffff] has been reserved
  [    0.393744] system 00:08: [mem 0xfec10000-0xfec1001f] has been reserved
  [    0.393747] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
  [    0.393845] pnp 00:09: [io  0x0000-0xffffffffffffffff disabled]
  [    0.393847] pnp 00:09: [io  0x0e00-0x0e0f]
  [    0.393848] pnp 00:09: [io  0x0e80-0x0e8f]
  [    0.393849] pnp 00:09: [io  0x0f40-0x0f4f]
  [    0.393876] system 00:09: [io  0x0e00-0x0e0f] has been reserved
  [    0.393878] system 00:09: [io  0x0e80-0x0e8f] has been reserved
  [    0.393880] system 00:09: [io  0x0f40-0x0f4f] has been reserved
  [    0.393883] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
  [    0.393904] pnp 00:0a: [mem 0xe0000000-0xefffffff]
  [    0.393932] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
  [    0.393935] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
  [    0.394012] pnp 00:0b: [mem 0x00000000-0x0009ffff]
  [    0.394014] pnp 00:0b: [mem 0x000c0000-0x000cffff]
  [    0.394015] pnp 00:0b: [mem 0x000e0000-0x000fffff]
  [    0.394017] pnp 00:0b: [mem 0x00100000-0xcfffffff]
  [    0.394019] pnp 00:0b: [mem 0xfec00000-0xffffffff]
  [    0.394049] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
  [    0.394051] system 00:0b: [mem 0x000c0000-0x000cffff] could not be reserved
  [    0.394053] system 00:0b: [mem 0x000e0000-0x000fffff] could not be reserved
  [    0.394055] system 00:0b: [mem 0x00100000-0xcfffffff] could not be reserved
  [    0.394058] system 00:0b: [mem 0xfec00000-0xffffffff] could not be reserved
  [    0.394060] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
  [    0.394130] pnp: PnP ACPI: found 12 devices
  [    0.394132] ACPI: ACPI bus type pnp unregistered
  [    0.399774] PCI: max bus depth: 1 pci_try_num: 2
  [    0.399792] pci 0000:00:01.0: PCI bridge to [bus 01-01]
  [    0.399794] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
  [    0.399797] pci 0000:00:01.0:   bridge window [mem 0xfe900000-0xfeafffff]
  [    0.399799] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
  [    0.399803] pci 0000:00:0a.0: PCI bridge to [bus 02-02]
  [    0.399805] pci 0000:00:0a.0:   bridge window [io  0xe000-0xefff]
  [    0.399807] pci 0000:00:0a.0:   bridge window [mem 0xfeb00000-0xfebfffff]
  [    0.399810] pci 0000:00:0a.0:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
  [    0.399813] pci 0000:00:14.4: PCI bridge to [bus 03-03]
  [    0.399814] pci 0000:00:14.4:   bridge window [io  disabled]
  [    0.399818] pci 0000:00:14.4:   bridge window [mem disabled]
  [    0.399822] pci 0000:00:14.4:   bridge window [mem pref disabled]
  [    0.399848] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
  [    0.399850] pci 0000:00:0a.0: setting latency timer to 64
  [    0.399858] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
  [    0.399860] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
  [    0.399861] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
  [    0.399863] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
  [    0.399865] pci_bus 0000:00: resource 8 [mem 0xd0000000-0xdfffffff]
  [    0.399867] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
  [    0.399869] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
  [    0.399870] pci_bus 0000:01: resource 1 [mem 0xfe900000-0xfeafffff]
  [    0.399872] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
  [    0.399874] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
  [    0.399875] pci_bus 0000:02: resource 1 [mem 0xfeb00000-0xfebfffff]
  [    0.399877] pci_bus 0000:02: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
  [    0.399879] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
  [    0.399881] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
  [    0.399882] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
  [    0.399884] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
  [    0.399886] pci_bus 0000:03: resource 8 [mem 0xd0000000-0xdfffffff]
  [    0.399887] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfebfffff]
  [    0.399922] NET: Registered protocol family 2
  [    0.400165] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
  [    0.401548] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
  [    0.404680] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
  [    0.405066] TCP: Hash tables configured (established 524288 bind 65536)
  [    0.405068] TCP reno registered
  [    0.405085] UDP hash table entries: 4096 (order: 5, 131072 bytes)
  [    0.405151] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
  [    0.405313] NET: Registered protocol family 1
  [    0.405324] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
  [    1.120152] pci 0000:01:05.0: Boot video device
  [    1.120159] PCI: CLS 64 bytes, default 64
  [    1.121187] PCI-DMA: Disabling AGP.
  [    1.121319] PCI-DMA: aperture base @ c4000000 size 65536 KB
  [    1.121320] PCI-DMA: using GART IOMMU.
  [    1.121323] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
  [    1.124393] audit: initializing netlink socket (disabled)
  [    1.124414] type=2000 audit(1335366844.120:1): initialized
  [    1.151349] HugeTLB registered 2 MB page size, pre-allocated 0 pages
  [    1.175389] VFS: Disk quotas dquot_6.5.2
  [    1.175435] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
  [    1.175994] fuse init (API version 7.16)
  [    1.176088] msgmni has been set to 11428
  [    1.176707] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
  [    1.176817] io scheduler noop registered
  [    1.176821] io scheduler deadline registered
  [    1.176889] io scheduler cfq registered (default)
  [    1.177159] pcieport 0000:00:0a.0: setting latency timer to 64
  [    1.177192] pcieport 0000:00:0a.0: irq 40 for MSI/MSI-X
  [    1.177329] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
  [    1.177351] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
  [    1.177445] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
  [    1.177450] ACPI: Power Button [PWRB]
  [    1.177477] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
  [    1.177479] ACPI: Power Button [PWRF]
  [    1.177531] ACPI: acpi_idle registered with cpuidle
  [    1.178219] ERST: Table is not found!
  [    1.178280] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
  [    1.222622] Freeing initrd memory: 13420k freed
  [    1.376207] Linux agpgart interface v0.103
  [    1.376917] brd: module loaded
  [    1.377252] loop: module loaded
  [    1.377574] Fixed MDIO Bus: probed
  [    1.377589] PPP generic driver version 2.4.2
  [    1.377622] tun: Universal TUN/TAP device driver, 1.6
  [    1.377624] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
  [    1.377679] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
  [    1.377830] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
  [    1.377883] ehci_hcd 0000:00:12.2: EHCI Host Controller
  [    1.377968] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
  [    1.377985] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
  [    1.378009] ehci_hcd 0000:00:12.2: debug port 1
  [    1.378030] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe8ff800
  [    1.388085] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
  [    1.388217] hub 1-0:1.0: USB hub found
  [    1.388220] hub 1-0:1.0: 6 ports detected
  [    1.388407] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
  [    1.388425] ehci_hcd 0000:00:13.2: EHCI Host Controller
  [    1.388455] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
  [    1.388463] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
  [    1.388483] ehci_hcd 0000:00:13.2: debug port 1
  [    1.388504] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe8ff400
  [    1.400084] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
  [    1.400212] hub 2-0:1.0: USB hub found
  [    1.400215] hub 2-0:1.0: 6 ports detected
  [    1.400326] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
  [    1.400395] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
  [    1.400415] ohci_hcd 0000:00:12.0: OHCI Host Controller
  [    1.400446] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
  [    1.400471] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe8fe000
  [    1.460187] hub 3-0:1.0: USB hub found
  [    1.460229] hub 3-0:1.0: 3 ports detected
  [    1.460360] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
  [    1.460380] ohci_hcd 0000:00:12.1: OHCI Host Controller
  [    1.460413] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
  [    1.460432] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe8fd000
  [    1.520180] hub 4-0:1.0: USB hub found
  [    1.520222] hub 4-0:1.0: 3 ports detected
  [    1.520358] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
  [    1.520379] ohci_hcd 0000:00:13.0: OHCI Host Controller
  [    1.520413] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
  [    1.520439] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe8fc000
  [    1.580181] hub 5-0:1.0: USB hub found
  [    1.580223] hub 5-0:1.0: 3 ports detected
  [    1.580383] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
  [    1.580404] ohci_hcd 0000:00:13.1: OHCI Host Controller
  [    1.580434] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
  [    1.580453] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe8f7000
  [    1.640196] hub 6-0:1.0: USB hub found
  [    1.640237] hub 6-0:1.0: 3 ports detected
  [    1.640333] uhci_hcd: USB Universal Host Controller Interface driver
  [    1.640400] i8042: PNP: No PS/2 controller found. Probing ports directly.
  [    1.640915] serio: i8042 KBD port at 0x60,0x64 irq 1
  [    1.640924] serio: i8042 AUX port at 0x60,0x64 irq 12
  [    1.641021] mousedev: PS/2 mouse device common for all mice
  [    1.641125] rtc_cmos 00:03: RTC can wake from S4
  [    1.641203] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
  [    1.641226] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
  [    1.641308] device-mapper: uevent: version 1.0.3
  [    1.641354] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
  [    1.641395] cpuidle: using governor ladder
  [    1.641397] cpuidle: using governor menu
  [    1.641398] EFI Variables Facility v0.08 2004-May-17
  [    1.641567] TCP cubic registered
  [    1.641646] NET: Registered protocol family 10
  [    1.641991] NET: Registered protocol family 17
  [    1.642005] Registering the dns_resolver key type
  [    1.642085] PM: Hibernation image not present or could not be loaded.
  [    1.642094] registered taskstats version 1
  [    1.659521]   Magic number: 8:624:235
  [    1.659660] rtc_cmos 00:03: setting system clock to 2012-04-25 15:14:04 UTC (1335366844)
  [    1.659675] powernow-k8: Found 1 AMD Athlon(tm) II X4 635 Processor (4 cpu cores) (version 2.20.00)
  [    1.659705] powernow-k8:    0 : pstate 0 (2900 MHz)
  [    1.659707] powernow-k8:    1 : pstate 1 (2200 MHz)
  [    1.659708] powernow-k8:    2 : pstate 2 (1700 MHz)
  [    1.659709] powernow-k8:    3 : pstate 3 (800 MHz)
  [    1.660341] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
  [    1.660344] EDD information not available.
  [    1.661684] Freeing unused kernel memory: 984k freed
  [    1.661909] Write protecting the kernel read-only data: 10240k
  [    1.662185] Freeing unused kernel memory: 20k freed
  [    1.666062] Freeing unused kernel memory: 1400k freed
  [    1.688270] udevd[117]: starting version 173
  [    1.704182] usb 1-1: new high speed USB device number 2 using ehci_hcd
  [    1.726573] ahci 0000:00:11.0: version 3.0
  [    1.726642] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
  [    1.726773] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
  [    1.726776] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc
  [    1.728186] scsi0 : ahci
  [    1.728237] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
  [    1.728264] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
  [    1.728308] r8169 0000:02:00.0: setting latency timer to 64
  [    1.728351] r8169 0000:02:00.0: irq 41 for MSI/MSI-X
  [    1.728694] r8169 0000:02:00.0: eth0: RTL8168e/8111e at 0xffffc90000c74000, d4:85:64:b1:a9:41, XID 0c200000 IRQ 41
  [    1.728997] scsi1 : ahci
  [    1.729176] scsi2 : ahci
  [    1.729660] scsi3 : ahci
  [    1.729770] ata1: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffd00 irq 22
  [    1.729773] ata2: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffd80 irq 22
  [    1.729776] ata3: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffe00 irq 22
  [    1.729778] ata4: SATA max UDMA/133 abar m1024@0xfe8ffc00 port 0xfe8ffe80 irq 22
  [    1.842576] usbcore: registered new interface driver uas
  [    2.048097] ata1: SATA link down (SStatus 0 SControl 300)
  [    2.048142] ata4: SATA link down (SStatus 0 SControl 300)
  [    2.124075] Refined TSC clocksource calibration: 2899.999 MHz.
  [    2.124086] Switching to clocksource tsc
  [    2.172077] usb 2-2: new high speed USB device number 3 using ehci_hcd
  [    2.220086] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
  [    2.220116] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
  [    2.223602] ata3.00: ATAPI: ATAPI   iHAS124   B, AL0S, max UDMA/100
  [    2.224506] ata3.00: configured for UDMA/100
  [    2.226653] ata2.00: ATA-7: SAMSUNG HD103SI, 1AG01118, max UDMA7
  [    2.226657] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
  [    2.233266] ata2.00: configured for UDMA/133
  [    2.233465] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD103SI  1AG0 PQ: 0 ANSI: 5
  [    2.233626] sd 1:0:0:0: Attached scsi generic sg0 type 0
  [    2.233697] sd 1:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
  [    2.233849] sd 1:0:0:0: [sda] Write Protect is off
  [    2.233852] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
  [    2.233877] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
  [    2.234842] scsi 2:0:0:0: CD-ROM            ATAPI    iHAS124   B      AL0S PQ: 0 ANSI: 5
  [    2.238271] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
  [    2.238275] cdrom: Uniform CD-ROM driver Revision: 3.20
  [    2.238415] sr 2:0:0:0: Attached scsi CD-ROM sr0
  [    2.238477] sr 2:0:0:0: Attached scsi generic sg1 type 5
  [    2.252477]  sda: sda1 sda2
  [    2.252915] sd 1:0:0:0: [sda] Attached SCSI disk
  [    2.253872] Initializing USB Mass Storage driver...
  [    2.254555] scsi4 : usb-storage 1-1:1.0
  [    2.254669] usbcore: registered new interface driver usb-storage
  [    2.254670] USB Mass Storage support registered.
  [    2.420083] usb 2-6: new high speed USB device number 4 using ehci_hcd
  [    2.559549] scsi5 : usb-storage 2-6:1.0
  [    2.820044] usb 5-1: new full speed USB device number 2 using ohci_hcd
  [    3.000297] input: Logitech G510 Gaming Keyboard as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input2
  [    3.000377] generic-usb 0003:046D:C22D.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech G510 Gaming Keyboard] on usb-0000:00:13.0-1/input0
  [    3.019194] input: Logitech G510 Gaming Keyboard as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.1/input/input3
  [    3.019320] generic-usb 0003:046D:C22D.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech G510 Gaming Keyboard] on usb-0000:00:13.0-1/input1
  [    3.019336] usbcore: registered new interface driver usbhid
  [    3.019337] usbhid: USB HID core driver
  [    3.253047] scsi 4:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  3.21 PQ: 0 ANSI: 2
  [    3.256049] usb 3-3: new full speed USB device number 2 using ohci_hcd
  [    3.424255] sd 4:0:0:0: Attached scsi generic sg2 type 0
  [    3.426269] sd 4:0:0:0: [sdb] 2006673 512-byte logical blocks: (1.02 GB/979 MiB)
  [    3.426885] sd 4:0:0:0: [sdb] Write Protect is off
  [    3.426889] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
  [    3.427383] sd 4:0:0:0: [sdb] No Caching mode page present
  [    3.427386] sd 4:0:0:0: [sdb] Assuming drive cache: write through
  [    3.429890] sd 4:0:0:0: [sdb] No Caching mode page present
  [    3.429894] sd 4:0:0:0: [sdb] Assuming drive cache: write through
  [    3.434520]  sdb: sdb1
  [    3.437362] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.0/input/input4
  [    3.437460] generic-usb 0003:046D:C52B.0003: input,hidraw2: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:12.0-3/input0
  [    3.438060] sd 4:0:0:0: [sdb] No Caching mode page present
  [    3.438063] sd 4:0:0:0: [sdb] Assuming drive cache: write through
  [    3.438065] sd 4:0:0:0: [sdb] Attached SCSI removable disk
  [    3.442364] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.0/usb3/3-3/3-3:1.1/input/input5
  [    3.442526] generic-usb 0003:046D:C52B.0004: input,hiddev0,hidraw3: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:12.0-3/input1
  [    3.451161] generic-usb 0003:046D:C52B.0005: hiddev0,hidraw4: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:12.0-3/input2
  [    3.556844] scsi 5:0:0:0: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0
  [    3.557452] scsi 5:0:0:1: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
  [    3.558095] scsi 5:0:0:2: Direct-Access     Generic- SM/xD-Picture    1.02 PQ: 0 ANSI: 0
  [    3.558845] scsi 5:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.03 PQ: 0 ANSI: 0 CCS
  [    3.624269] EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts: (null)
  [    3.760228] sd 5:0:0:0: Attached scsi generic sg3 type 0
  [    3.760315] sd 5:0:0:1: Attached scsi generic sg4 type 0
  [    3.760397] sd 5:0:0:2: Attached scsi generic sg5 type 0
  [    3.760481] sd 5:0:0:3: Attached scsi generic sg6 type 0
  [    3.767307] sd 5:0:0:0: [sdc] Attached SCSI removable disk
  [    3.768077] sd 5:0:0:2: [sde] Attached SCSI removable disk
  [    3.768801] sd 5:0:0:1: [sdd] Attached SCSI removable disk
  [    3.769550] sd 5:0:0:3: [sdf] Attached SCSI removable disk
  [   16.660089] udevd[502]: starting version 173
  [   16.674685] lp: driver loaded but no devices found
  [   16.684858] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 1022 ss_did 9602
  [   16.684864] shpchp 0000:00:01.0: Cannot reserve MMIO region
  [   16.684921] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
  [   16.738277] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
  [   16.738838] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
  [   16.738986] SP5100 TCO timer: mmio address 0xfec000f0 already in use
  [   16.739463] MCE: In-kernel MCE decoding enabled.
  [   16.741742] EDAC MC: Ver: 2.1.0
  [   16.744795] AMD64 EDAC driver v3.4.0
  [   16.746081] EDAC amd64: DRAM ECC disabled.
  [   16.746091] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
  [   16.746092]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
  [   16.746093]  (Note that use of the override may cause unknown side effects.)
  [   16.759931] [drm] Initialized drm 1.1.0 20060810
  [   16.771479] [drm] radeon defaulting to kernel modesetting.
  [   16.771483] [drm] radeon kernel modesetting enabled.
  [   16.773309] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
  [   16.773315] radeon 0000:01:05.0: setting latency timer to 64
  [   16.773530] [drm] initializing kernel modesetting (RS880 0x1002:0x9710 0x103C:0x2AB1).
  [   16.773564] [drm] register mmio base: 0xFE9F0000
  [   16.773565] [drm] register mmio size: 65536
  [   16.774247] ATOM BIOS: BR34448.bin
  [   16.774270] radeon 0000:01:05.0: VRAM: 256M 0x00000000C0000000 - 0x00000000CFFFFFFF (256M used)
  [   16.774272] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
  [   16.774530] [drm] Detected VRAM RAM=256M, BAR=256M
  [   16.774533] [drm] RAM width 32bits DDR
  [   16.776062] [TTM] Zone  kernel: Available graphics memory: 2933554 kiB.
  [   16.776065] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
  [   16.776067] [TTM] Initializing pool allocator.
  [   16.776095] [drm] radeon: 256M of VRAM memory ready
  [   16.776097] [drm] radeon: 512M of GTT memory ready.
  [   16.776114] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
  [   16.776115] [drm] Driver supports precise vblank timestamp query.
  [   16.776133] [drm] radeon: irq initialized.
  [   16.776139] [drm] GART: num cpu pages 131072, num gpu pages 131072
  [   16.777550] [drm] Loading RS780 Microcode
  [   16.792794] wmi: Mapper loaded
  [   16.849349] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
  [   16.892244] radeon 0000:01:05.0: WB enabled
  [   16.924477] hda_codec: ALC888-VD: BIOS auto-probing.
  [   16.928076] [drm] ring test succeeded in 1 usecs
  [   16.928212] [drm] radeon: ib pool ready.
  [   16.928292] [drm] ib test succeeded in 0 usecs
  [   16.928587] [drm] Radeon Display Connectors
  [   16.928589] [drm] Connector 0:
  [   16.928590] [drm]   VGA
  [   16.928592] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
  [   16.928593] [drm]   Encoders:
  [   16.928594] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
  [   16.928595] [drm] Connector 1:
  [   16.928596] [drm]   DVI-D
  [   16.928597] [drm]   HPD1
  [   16.928598] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
  [   16.928599] [drm]   Encoders:
  [   16.928601] [drm]     DFP1: INTERNAL_KLDSCP_LVTMA
  [   16.972068] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
  [   16.988123] [drm] Radeon display connector VGA-1: Found valid EDID
  [   17.039492] [drm] Radeon display connector DVI-D-1: Found valid EDID
  [   17.039520] [drm] radeon: power management initialized
  [   17.167996] [drm] fb mappable at 0xD0141000
  [   17.167997] [drm] vram apper at 0xD0000000
  [   17.167998] [drm] size 5787648
  [   17.168006] [drm] fb depth is 24
  [   17.168007] [drm]    pitch is 6400
  [   17.168054] fbcon: radeondrmfb (fb0) is primary device
  [   17.168157] Console: switching to colour frame buffer device 200x56
  [   17.168180] fb0: radeondrmfb frame buffer device
  [   17.168182] drm: registered panic notifier
  [   17.168188] [drm] Initialized radeon 2.10.0 20080528 for 0000:01:05.0 on minor 0
  [   17.168551] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
  [   17.168601] HDA Intel 0000:01:05.1: setting latency timer to 64
  [   17.904143] usb 2-2: usbfs: USBDEVFS_CONTROL failed cmd mtp-probe rqt 128 rq 6 len 1024 ret -110
  [   17.964791] Adding 262136k swap on /host/linuxmint/disks/swap.disk.  Priority:-1 extents:1 across:262136k
  [   18.034993] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro
  [   18.837185] r8169 0000:02:00.0: eth0: link down
  [   18.837913] ADDRCONF(NETDEV_UP): eth0: link is not ready
  [   19.065024] ppdev: user-space parallel port driver
  [   19.302937] init: failsafe main process (932) killed by TERM signal
  [   19.399431] Bluetooth: Core ver 2.16
  [   19.399457] NET: Registered protocol family 31
  [   19.399459] Bluetooth: HCI device and connection manager initialized
  [   19.399463] Bluetooth: HCI socket layer initialized
  [   19.399464] Bluetooth: L2CAP socket layer initialized
  [   19.399917] Bluetooth: SCO socket layer initialized
  [   19.401693] Bluetooth: RFCOMM TTY layer initialized
  [   19.401698] Bluetooth: RFCOMM socket layer initialized
  [   19.401700] Bluetooth: RFCOMM ver 1.11
  [   19.402115] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
  [   19.402118] Bluetooth: BNEP filters: protocol multicast
  [   19.616549] radeon 0000:01:05.0: texture bo too small (1600 900 26 0 -> 5785600 have 5763072)
  [   19.616554] radeon 0000:01:05.0: alignments 1600 64 8 256
  [   19.616556] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
  [   20.700524] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
  [   21.054115] init: plymouth-stop pre-start process (1552) terminated with status 1
  [   21.697813] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
  

---

### Post by chili555 on 2012-04-26
A whole lot of information we don't need, because none of it mentions ndiswrapper, and none of the information we *do* need. When you did the first command, what happened? ```
sudo modprobe ndiswrapper
```Nothing? Please tell us. If nothing happened, that tells us valuable information, that there was no error or warning.

When you did the second command, what happened? ```
ndiswrapper -l
```Surely, it said something like:> bcmwlhigh5 : driver installedWe need to know what it said.

Finally, did you use the pipe symbol | and grep? The pipe symbol is on the right side of my keyboard on the same key with \. If you loaded ndiswrapper as above, there should have been at least some recognition in dmesg:> $ dmesg | grep ndiswrapper 
[25142.597196] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[25142.622130] usbcore: registered new interface driver ndiswrapper
Without the information I requested, I'm unable to help further.

---

### Post by Adhso on 2012-04-26
When i put in

   [FONT=&quot]sudo modprobe ndiswrapper[/FONT]
  
  
I got 

>   FATAL: Module ndiswrapper not found.
  

Then when i put  in   ndiswrapper -l
  

I got 
>   bcmwlhigh5 : driver installed
  [FONT=&quot]            device (13B1:003A) present[/FONT]

 When I put in grep ndis nothing happens, the [EMAIL="cryph1x@linuxmint"][COLOR=windowtext]cryph1x@linuxmint[/COLOR][/EMAIL] doesn't even show up.


Thanks for all your help again and sorry i didn't put what you wanted earlier.

---

### Post by chili555 on 2012-04-26
> FATAL: Module ndiswrapper not found. That's a very good reason it isn't working! I suggest you go to Synaptic and mark each and every ndiswrapper package for reinstallation. Then try again:```
sudo modprobe ndiswrapper
```If you still get a fatal error, we'll another strategy.

---

### Post by Adhso on 2012-04-26
> **chili555 said:**
> That's a very good reason it isn't working! I suggest you go to Synaptic and mark each and every ndiswrapper package for reinstallation. Then try again:```
sudo modprobe ndiswrapper
```If you still get a fatal error, we'll another strategy.

Is Synaptic a website or something?  If so how do i install the ndiswrapper packages?

---

### Post by chili555 on 2012-04-26
> **CrYph1x said:**
> Is Synaptic a website or something?  If so how do i install the ndiswrapper packages?It's been a while since I tried Mint. Isn't Synaptic the software manager? If you can't find it, try:```
sudo apt-get install synaptic
```After it installs, open it with:```
sudo synaptic
```Search for ndiswrapper in the search box and reinstall them.

---

### Post by Adhso on 2012-04-26
Well i got it installed and when i did the command it opened up and when i searched for ndiswrapper it pops up with a lot of stuff and it won't let me  install any of it cause some i need to be connected to the internet and others get an error.

---

### Post by chili555 on 2012-04-27
How did you get Synaptic installed without being connected to the internet? If you were, why can't you reinstall ndiswrapper?

---

### Post by Adhso on 2012-04-27
> **chili555 said:**
> How did you get Synaptic installed without being connected to the internet? If you were, why can't you reinstall ndiswrapper?

I guess it was already installed, and idk why it won't let me.  Is there a command to install ndiswrapper?

---

### Post by chili555 on 2012-04-27
Yes there is:```
sudo apt-get install synaptic
```

---

### Post by Adhso on 2012-04-28
Nvm i got it to work!!!  I just found a different wifi adapter in my drawer and just used that, thanks again for all your help!!!

---

