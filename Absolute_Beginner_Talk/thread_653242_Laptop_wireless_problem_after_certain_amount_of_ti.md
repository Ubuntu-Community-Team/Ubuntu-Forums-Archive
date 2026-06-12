---
title: "Laptop wireless problem after certain amount of time or suspend/hibernate"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by PreviousN on 2007-12-29
Hi there. I've installed ubuntu on my dad's laptop (came with vista) and everything works fine...except for one thing. 

After about an hour or two the wireless disconnects and cannot reconnect. A similar effect happens when I suspend or hibernate the computer. In order to get wireless to reconnect I have to restart. _When I try to restart, the operating system will unload, but it will not turn off without holding down the power button. The last screen shows the ubuntu logo with a fully unloaded bar at the bottom. The computer never turns off unless I hold the button _

I wanted to try using NDISWRAPPER, but encountered crazy problems (one...the drivers are in an .exe that installs automatically. You can't just find an ".inf" for NDISwrapper. Second, I don't know which module to blacklist so it doesn't try to load the linux wifi driver).

I've googled/searched the forumns for hours. I'm starting to get slightly frustrated... Can anyone help?

**outputs before suspend/hibernate**

Output of iwlist scanning
```
          Cell 01 - Address: 00:13:10:E4:3D:41
                    ESSID:"*******"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:03:93:EC:74:EB
                    ESSID:"******"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:11:24:0C:53:05
                    ESSID:"*******"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:59/100  Signal level:-58 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

Here's the output of lspci
```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
```

Here's the output of dmesg | tail:
```
[   22.680000] Failure registering capabilities with primary security module.
[   24.000000] Clocksource tsc unstable (delta = -250018789 ns)
[  716.444000] NET: Registered protocol family 10
[  716.444000] lo: Disabled Privacy Extensions
[  716.448000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  725.240000] NET: Registered protocol family 17
[  727.252000] wlan0: no IPv6 routers present
[  786.636000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  797.664000] wlan0: no IPv6 routers present
[  816.684000] wlan0: no IPv6 routers present

```

The output of lsmod:
```
Module                  Size  Used by
af_packet              24840  4 
ipv6                  273892  12 
ppdev                  10244  0 
powernow_k8            16960  1 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  1 
freq_table              5792  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
button                  8976  0 
dock                   10656  0 
video                  18060  8 
ac                      6148  0 
battery                11012  0 
sbs                    19592  0 
container               5504  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ndiswrapper           185240  0 
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               6221648  36 
k8temp                  6656  0 
agpgart                35016  1 nvidia
pcspkr                  4224  0 
psmouse                39952  0 
serio_raw               8068  0 
i2c_nforce2             7040  0 
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
i2c_core               26112  2 nvidia,i2c_nforce2
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  3 
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
sata_nv                20612  2 
ata_generic             8452  0 
libata                125168  2 sata_nv,ata_generic
forcedeth              51592  0 
scsi_mod              147084  3 sg,sd_mod,libata
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  4 ndiswrapper,ehci_hcd,ohci_hcd
amd74xx                15260  0 [permanent]
ide_core              116804  2 ide_cd,amd74xx
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

Uname -r
2.6.22-14-generic

ifconfig 
```
eth0      Link encap:Ethernet  HWaddr 00:16:17:4F:96:DE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:19:DB:00:71:D8  
          inet addr:192.168.1.139  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:dbff:fe00:71d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1740 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1829055 (1.7 MB)  TX bytes:184191 (179.8 KB)

```

I'll post the output of dmesg, ifconfig, lsmod, lspci after suspend/hibernate.

---

### Post by PreviousN on 2007-12-29
As promised, here's the outputs after hibernating/suspending:

iwlist scanning
```

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```

ifconfig 
```
eth0      Link encap:Ethernet  HWaddr 00:16:17:4F:96:DE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:19:DB:00:71:D8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```


lsmod
```
Module                  Size  Used by
battery                11012  0 
ac                      6148  0 
thermal                14344  0 
fan                     5764  0 
button                  8976  0 
forcedeth              51592  0 
ndiswrapper           185240  0 
af_packet              24840  0 
ipv6                  273892  12 
ppdev                  10244  0 
powernow_k8            16960  1 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  1 
freq_table              5792  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
dock                   10656  0 
video                  18060  8 
sbs                    19592  0 
container               5504  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               6221648  36 
k8temp                  6656  0 
agpgart                35016  1 nvidia
pcspkr                  4224  0 
psmouse                39952  0 
serio_raw               8068  0 
i2c_nforce2             7040  0 
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
i2c_core               26112  2 nvidia,i2c_nforce2
evdev                  11136  5 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  3 
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
sata_nv                20612  2 
ata_generic             8452  0 
libata                125168  2 sata_nv,ata_generic
scsi_mod              147084  3 sg,sd_mod,libata
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  4 ndiswrapper,ehci_hcd,ohci_hcd
amd74xx                15260  0 [permanent]
ide_core              116804  2 ide_cd,amd74xx
processor              32072  2 thermal,powernow_k8
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

lspci
```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
```

dmesg
```
[  816.684000] wlan0: no IPv6 routers present
[ 1640.616000] usbcore: deregistering interface driver ndiswrapper
[ 1641.332000] ndiswrapper: device wlan0 removed
[ 1641.348000] ndiswrapper version 1.45 loaded (smp=yes)
[ 1641.484000] usb 1-8: reset high speed USB device using ehci_hcd and address 2
[ 1641.688000] ndiswrapper: driver rt73 (Ralink,01/12/2006, 1.00.04.0000) loaded
[ 1642.252000] wlan0: ethernet device 00:19:db:00:71:d8 using NDIS driver: rt73, version: 0x0, NDIS version: 0x500, vendor: 'IEEE 802.11g Wireless Card.', 0DB0:6877.F.conf
[ 1642.252000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 1642.252000] usbcore: registered new interface driver ndiswrapper
[ 1642.256000] usbcore: deregistering interface driver ndiswrapper
[ 1642.972000] ndiswrapper: device wlan0 removed
[ 1643.068000] ACPI: PCI interrupt for device 0000:00:14.0 disabled
[ 1643.268000] ndiswrapper version 1.45 loaded (smp=yes)
[ 1643.436000] usb 1-8: reset high speed USB device using ehci_hcd and address 2
[ 1643.688000] ndiswrapper: driver rt73 (Ralink,01/12/2006, 1.00.04.0000) loaded
[ 1644.444000] wlan0: ethernet device 00:19:db:00:71:d8 using NDIS driver: rt73, version: 0x0, NDIS version: 0x500, vendor: 'IEEE 802.11g Wireless Card.', 0DB0:6877.F.conf
[ 1644.448000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 1644.448000] usbcore: registered new interface driver ndiswrapper
[ 1645.392000] PM: Preparing system for mem sleep
[ 1645.392000] Stopping tasks ... done.
[ 1645.544000] Suspending console(s)
[ 1645.544000] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 1645.748000] sd 0:0:0:0: [sda] Stopping disk
[ 1646.192000] ndiswrapper (mp_set_power_state:409): wlan0 does not support power management; halting the device
[ 1646.908000] usb_device usbdev2.1: PM: suspend 0->2, parent usb2 already 2
[ 1646.908000] usb_endpoint usbdev2.1_ep81: PM: suspend 0->2, parent 2-0:1.0 already 2
[ 1646.908000] hub 2-0:1.0: PM: suspend 2->2, parent usb2 already 2
[ 1646.908000] usb_endpoint usbdev2.1_ep00: PM: suspend 0->2, parent usb2 already 2
[ 1647.412000] ACPI: PCI interrupt for device 0000:00:10.1 disabled
[ 1647.428000] ACPI: PCI interrupt for device 0000:00:0e.0 disabled
[ 1647.444000] ACPI: PCI interrupt for device 0000:00:0b.1 disabled
[ 1647.460000] ACPI: PCI interrupt for device 0000:00:0b.0 disabled
[ 1647.476000] NVRM: RmPowerManagement: 3
[ 1647.688000] Disabling non-boot CPUs ...
[ 1647.808000] CPU 1 is now offline
[ 1647.808000] SMP alternatives: switching to UP code
[ 1647.808000] CPU1 is down
[ 1647.808000] PM: Entering mem sleep
[ 1647.808000] Back to C!
[ 1647.808000] PM: Finishing wakeup.
[ 1647.808000] Enabling non-boot CPUs ...
[ 1647.820000] SMP alternatives: switching to SMP code
[ 1647.820000] Booting processor 1/1 eip 3000
[ 1647.824000] Initializing CPU#1
[ 1647.904000] Calibrating delay using timer specific routine.. 3214.50 BogoMIPS (lpj=6429002)
[ 1647.904000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[ 1647.904000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[ 1647.904000] CPU: L2 Cache: 256K (64 bytes/line)
[ 1647.904000] CPU 1(2) -> Core 1
[ 1647.904000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[ 1647.904000] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-50 stepping 02
[ 1647.904000] CPU1 is up
[ 1647.904000] PM: Writing back config space on device 0000:00:00.0 at offset f (was 0, writing ff)
[ 1647.904000] PM: Writing back config space on device 0000:00:00.3 at offset f (was 0, writing ff)
[ 1647.904000] PM: Writing back config space on device 0000:00:00.4 at offset f (was 0, writing ff)
[ 1647.904000] PM: Writing back config space on device 0000:00:00.5 at offset f (was 0, writing ff)
[ 1647.904000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[ 1647.904000] NVRM: RmPowerManagement: 4
[ 1647.908000] Switched to high resolution mode on CPU 1
[ 1648.880000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUB0] -> GSI 22 (level, low) -> IRQ 17
[ 1648.880000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[ 1648.896000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUB2] -> GSI 23 (level, low) -> IRQ 16
[ 1648.896000] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[ 1648.912000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LSA0] -> GSI 20 (level, low) -> IRQ 19
[ 1648.912000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[ 1648.912000] PCI: Setting latency timer of device 0000:00:10.0 to 64
[ 1648.928000] PM: Writing back config space on device 0000:00:10.1 at offset 4 (was de000000, writing 40000000)
[ 1648.928000] PM: Writing back config space on device 0000:00:10.1 at offset 1 (was b00006, writing b00002)
[ 1648.928000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 23 (level, low) -> IRQ 16
[ 1648.928000] PCI: Setting latency timer of device 0000:00:10.1 to 64
[ 1649.012000] PM: Writing back config space on device 0000:00:14.0 at offset 1 (was b00007, writing b00003)
[ 1649.012000] pnp: Failed to activate device 00:03.
[ 1649.012000] pnp: Failed to activate device 00:04.
[ 1649.224000] ata2: SATA link down (SStatus 0 SControl 300)
[ 1649.684000] ACPI Error (dsopcode-0481): Attempt to CreateField of length zero [20070126]
[ 1649.684000] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.PCI0.IDE0.RATA] (Node eee5fb88), AE_AML_OPERAND_VALUE
[ 1649.684000] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.PCI0.IDE0.CHN0.DRV1._GTF] (Node eee5f930), AE_AML_OPERAND_VALUE
[ 1649.684000] do_drive_get_GTF: Run _GTF error: status = 0x3006
[ 1649.732000] usb_endpoint usbdev2.1_ep00: PM: resume from 0, parent usb2 still 2
[ 1649.732000] usb_endpoint usbdev2.1_ep81: PM: resume from 0, parent 2-0:1.0 still 2
[ 1649.732000] usb_device usbdev2.1: PM: resume from 0, parent usb2 still 2
[ 1649.732000] usb_endpoint usbdev1.2_ep00: PM: resume from 0, parent 1-8 still 2
[ 1649.732000] ndiswrapper 1-8:1.0: PM: resume from 2, parent 1-8 still 2
[ 1649.732000] usb_device usbdev1.2: PM: resume from 0, parent 1-8 still 2
[ 1649.732000] sd 0:0:0:0: [sda] Starting disk
[ 1649.772000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 1649.796000] ata1.00: ACPI cmd ef/03:46:00:00:00:a0 failed (Emask=0x1 Stat=0x51 Err=0x04)
[ 1649.796000] ata1.00: revalidation failed (errno=-5)
[ 1649.796000] ata1: failed to recover some devices, retrying in 5 secs
[ 1655.432000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 1655.440000] ata1.00: ACPI cmd ef/03:46:00:00:00:a0 failed (Emask=0x1 Stat=0x51 Err=0x04)
[ 1655.440000] ata1.00: ACPI on devcfg failed the second time, disabling (errno=-5)
[ 1655.440000] ata1.00: revalidation failed (errno=1)
[ 1655.440000] ata1: failed to recover some devices, retrying in 5 secs
[ 1661.076000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 1661.100000] ata1.00: configured for UDMA/100
[ 1661.528000] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[ 1661.528000] usb_endpoint usbdev1.2_ep81: PM: resume from 0, parent 1-8:1.0 still 2
[ 1661.528000] usb_endpoint usbdev1.2_ep01: PM: resume from 0, parent 1-8:1.0 still 2
[ 1661.528000] net wlan0: PM: resume from 0, parent 1-8:1.0 still 2
[ 1661.528000] Restarting tasks ... <6>usb 1-8: USB disconnect, address 2
[ 1661.528000] BUG: unable to handle kernel paging request at virtual address f0b913a8
[ 1661.528000]  printing eip:
[ 1661.528000] f0b6c31d
[ 1661.528000] *pde = 2ffcd067
[ 1661.528000] *pte = 00000000
[ 1661.528000] Oops: 0002 [#1]
[ 1661.528000] SMP 
[ 1661.528000] Modules linked in: ndiswrapper af_packet ipv6 ppdev powernow_k8 cpufreq_userspace cpufreq_powersave cpufreq_stats cpufreq_conservative cpufreq_ondemand freq_table button dock video ac battery sbs container parport_pc lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device nvidia(P) k8temp agpgart pcspkr psmouse serio_raw i2c_nforce2 snd soundcore snd_page_alloc shpchp pci_hotplug i2c_core evdev ext3 jbd mbcache sg sd_mod ide_cd cdrom sata_nv ata_generic libata scsi_mod ehci_hcd ohci_hcd usbcore amd74xx ide_core thermal processor fan fuse apparmor commoncap
[ 1661.528000] CPU:    0
[ 1661.528000] EIP:    0060:[<f0b6c31d>]    Tainted: P       VLI
[ 1661.528000] EFLAGS: 00010293   (2.6.22-14-generic #1)
[ 1661.528000] EIP is at 0xf0b6c31d
[ 1661.528000] eax: f0b91000   ebx: d333a500   ecx: 00000014   edx: 00000014
[ 1661.528000] esi: 00000001   edi: ee46dcc0   ebp: ee46dc4c   esp: ee46dbb8
[ 1661.528000] ds: 007b   es: 007b   fs: 00d8  gs: 0000  ss: 0068
[ 1661.528000] Process khubd (pid: 2158, ti=ee46c000 task=df9c2f90 task.ti=ee46c000)
[ 1661.528000] Stack: dfdf9060 dfdf9060 dfda7780 00000014 00000006 fffffffc 00000000 ee46dc20 
[ 1661.528000]        f0898079 80000d80 00000002 00304b40 c0304b80 00000001 00000001 fffffffc 
[ 1661.528000]        00000000 00000020 c15e3ca0 df9c2f90 00000001 c03b5600 00000246 00000001 
[ 1661.528000] Call Trace:
[ 1661.528000]  [<f0898079>] qh_urb_transaction+0xd9/0x330 [ehci_hcd]
[ 1661.528000]  [<c0194d8b>] inode_init_once+0x5b/0x110
[ 1661.528000]  [<f0a6fb59>] mp_request+0x1b9/0x1f0 [ndiswrapper]
[ 1661.528000]  [<f0a6fbff>] mp_set+0x2f/0x40 [ndiswrapper]
[ 1661.528000]  [<f0a5ba6e>] disassociate+0x1e/0x90 [ndiswrapper]
[ 1661.528000]  [<f0a696e5>] IofCallDriver+0x55/0xc0 [ndiswrapper]
[ 1661.528000]  [<f0a6f972>] wrap_ndis_remove_device+0x202/0x230 [ndiswrapper]
[ 1661.528000]  [<f0a7077d>] NdisDispatchPnp+0x12d/0xdb0 [ndiswrapper]
[ 1661.528000]  [<c02f1832>] klist_node_init+0x32/0x50
[ 1661.528000]  [<c025ebb9>] device_add+0x59/0x570
[ 1661.528000]  [<c01fa096>] kobject_get_path+0x66/0xd0
[ 1661.528000]  [<f0a69a9b>] IoAllocateIrp+0x5b/0x80 [ndiswrapper]
[ 1661.528000]  [<f0a6a1e5>] IoBuildAsynchronousFsdRequest+0x35/0x170 [ndiswrapper]
[ 1661.528000]  [<f0a696e5>] IofCallDriver+0x55/0xc0 [ndiswrapper]
[ 1661.528000]  [<f0a6e97b>] IoSendIrpTopDev+0xbb/0x120 [ndiswrapper]
[ 1661.528000]  [<f0a6ea53>] pnp_remove_device+0x73/0x1d0 [ndiswrapper]
[ 1661.528000]  [<f08c8000>] usb_unbind_interface+0x50/0xa0 [usbcore]
[ 1661.528000]  [<c0260f38>] __device_release_driver+0x68/0xa0
[ 1661.528000]  [<c02613a3>] device_release_driver+0x23/0x40
[ 1661.528000]  [<c026080c>] bus_remove_device+0x5c/0x90
[ 1661.528000]  [<c025e970>] device_del+0x160/0x260
[ 1661.528000]  [<f08c529e>] usb_disable_device+0x7e/0xe0 [usbcore]
[ 1661.528000]  [<f08c13a7>] usb_disconnect+0x97/0x130 [usbcore]
[ 1661.528000]  [<f08c1a4f>] hub_thread+0x26f/0xc30 [usbcore]
[ 1661.528000]  [<c02f204a>] schedule+0x2ca/0x890
[ 1661.528000]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[ 1661.528000]  [<f08c17e0>] hub_thread+0x0/0xc30 [usbcore]
[ 1661.528000]  [<c013bb12>] kthread+0x42/0x70
[ 1661.528000]  [<c013bad0>] kthread+0x0/0x70
[ 1661.528000]  [<c0105487>] kernel_thread_helper+0x7/0x10
[ 1661.528000]  =======================
[ 1661.528000] Code: 14 00 01 c0 eb 1d 8b 45 14 50 8b 4d 10 51 6a 01 68 14 01 01 0d 8b 55 e4 52 e8 b0 9d ff ff e9 8e 0d 00 00 e9 5c 0d 00 00 8b 45 e4 <c6> 80 a8 03 00 00 01 8b 4d e4 8b 91 a4 03 00 00 83 e2 01 74 52 
[ 1661.528000] EIP: [<f0b6c31d>] 0xf0b6c31d SS:ESP 0068:ee46dbb8
[ 1661.540000] note: khubd[2158] exited with preempt_count 1
[ 1661.540000] sd 0:0:0:0: [sda] Write Protect is off
[ 1661.540000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1661.548000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1661.568000] done.
[ 1661.788000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[ 1661.788000] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 21 (level, low) -> IRQ 18
[ 1661.788000] PCI: Setting latency timer of device 0000:00:14.0 to 64
[ 1661.788000] forcedeth: using HIGHDMA
[ 1662.308000] eth0: forcedeth.c: subsystem: 01462:373d bound to 0000:00:14.0
[ 1662.364000] eth0: no link during initialization.
[ 1662.368000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1663.960000] input: Power Button (FF) as /class/input/input8
[ 1663.960000] ACPI: Power Button (FF) [PWRF]
[ 1663.960000] input: Lid Switch as /class/input/input9
[ 1663.960000] ACPI: Lid Switch [LID0]
[ 1663.964000] input: Sleep Button (CM) as /class/input/input10
[ 1663.964000] ACPI: Sleep Button (CM) [SLPB]
[ 1663.964000] input: Power Button (CM) as /class/input/input11
[ 1663.964000] ACPI: Power Button (CM) [PWRB]
[ 1664.164000] ACPI: Thermal Zone [THRM] (40 C)
[ 1664.228000] ACPI: AC Adapter [ADP1] (on-line)
[ 1664.264000] ACPI: Battery Slot [BAT1] (battery present)
[ 1798.664000] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0).
[ 1798.664000] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known.
[ 1798.664000] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0).
[ 1798.664000] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known.
[ 1805.616000] atkbd.c: Unknown key pressed (translated set 2, code 0xf6 on isa0060/serio0).
[ 1805.616000] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known.
[ 1805.616000] atkbd.c: Unknown key released (translated set 2, code 0xf6 on isa0060/serio0).
[ 1805.616000] atkbd.c: Use 'setkeycodes e076 <keycode>' to make it known.
```

[I][B][U]
Again, I really appreciate any help on this. I'm at my wits end! Thanks!!![/U][/B][/I]

---

### Post by spiderbatdad on 2007-12-29
hmmm. not sure. possible the driver has problems. This has an integrated adapter?

I would try enabling eth1 as well.  what does```
sudo lshw -C Network
``` spit out?

---

### Post by PreviousN on 2007-12-29
Do you want before I try suspending or after? It'll take me a while to do both because I have to restart after getting the after suspended result. 


Thanks!

---

### Post by spiderbatdad on 2007-12-29
I would say restart. There are so many issues with hibernating and suspending I wouldn't even try to discuss that one. My solution to suspend to ram or hibernate is....don't. If your powermanagement setting are never sleep computer and sleep display after X minutes, and blank screen when lid is closed...the display still shuts down when lid is closed. That meets my needs.

---

### Post by PreviousN on 2007-12-29
Before suspending/hibernating
```

  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:db:00:71:d8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt73 driverversion=1.45+Ralink,01/12/2006, 1.00.04. ip=192.168.0.15 link=yes multicast=yes wireless=IEEE 802.11g

```

---

### Post by PreviousN on 2007-12-29
lshw -C Network after hibernating/suspending
```

*-network     
     description: Ethernet interface
     physical id: 1
     logical name: wlan0
     serial: 00:19:db:00:71:d8
     capabilities: ethernet physical
     configuration: broadcast-yes  multicast=yes

```

I would tell my dad to have it never go to sleep but the laptop is almost rarely plugged in. My dad used to have an ibook and is used to being able to just shut the lid and leave it over night. I'm sure his computer wouldn't last >2 hours with it running but the screen off. 

And, the problem is, he was able to suspend with vista. He kind of takes it as a "this doesn't work, so its not as good" thing. 

I really don't want to have my dad using vista, but if I can't get it suspending/hibernating, he may just decide to have me put it back on for him.

---

### Post by spiderbatdad on 2007-12-29
I still would configure eth1 as the interface. Thats all i can think of...looks like it fine for the moment...wlan is subject to interference that may be why it drops...unless it always happens after the same amount of time...Again on the suspend issue...IDK there are a lot of posts pertaining to specific laptops. My T-30 has no issues, but I see other T-42, T-60 etc having trouble.

---

### Post by spiderbatdad on 2007-12-29
Repost with just that issue and include your Make & Model...then search the forums...there is probably a work around or fix.

:lolflag:If he goes back to vista, he'll have woes far beyond having to plug in a power cable overnight.

---

### Post by spiderbatdad on 2007-12-29
BTW configuring eth1 might just solve he loss during suspend...

---

### Post by PreviousN on 2007-12-29
What do you mean you would use eth1 for the interface? You mean use wired? I may need some help trying to "configure eth1" - kinda confused about what you mean. Sorry. 

Also, btw...all two of those networks listed in iwlist scanning are of the same network. I use wds so that there is no drops. Also, the router is less that 20 feet away in line of sight. The third network is my personal one that I have since I'm home for christmas. The connection goes away no matter which network I'm connected to. 

I find it odd that lshw -C Network shows the same interface, yet after the hibernate the driver details are gone and the wireless capabilities aren't listed. 

I guess I somehow managed to set up NDISwrapper correctly because lshw shows ndiws. For some reason its not reloading ndiswrapper after suspend. Any ideas? 

Also, since my parents use an apple airport extreme, which has only one lan port (don't blame me...I did'nt recommend it!) and that is already in use for my mom's desktop computer...I don't think that I would be able to convince my dad to use a wired connection.

They'd have to buy a hub/switch. And I'm sure my dad would rather just use vista than spend 20-30 bucks on a whole switch. 

As for the model of the laptop...it is a:

ZT Systems serial number 202316850078 (sorry couldn't find model)

Attached is a screenshot of the system specs.

---

### Post by spiderbatdad on 2007-12-29
eth1 is the logical name of the wireless interface...just configure it graphically through system>>administration>>network. leave wlan as is for now. and add/enable eth1. I have wifi0 and eth1 both enabled and roaming enabled...but my network is not secured.

---

### Post by spiderbatdad on 2007-12-29
then check the network monitor in the panel and make sure the router is ticked.

---

### Post by spiderbatdad on 2007-12-29
I'll give some final words from my experience as well. Trying to sell or force an operating system on someone who thinks another system is better (ie. Vista) never works. He's going to blame every bug and obstacle on what he thinks is a second rate system he got talked into. Let him suffer with Vista for the next six months, then come back after Hardy is released. As long as he knows Ubuntu/Linux exists, you've done your best. He has to make the choice, or he'll never be happy.

---

### Post by PreviousN on 2007-12-29
Yeah, I guess you're right. I think I'll reinstall vista for him. One more thing though...its weird. Attached is a screenshot of after suspend. I opened up the administrative network gui and suspended it, then after suspend opened a new one. Its like the computer things that the hardware has changed or something. I know its that a driver is not being loaded.


The right side is before and the left side is after. 

Thanks for your help..

---

### Post by spiderbatdad on 2007-12-29
Wanted to give you this link...might have the key to locking down your interface:
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

