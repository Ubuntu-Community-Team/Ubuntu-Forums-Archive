---
title: "[SOLVED] PS3: How Do I Get Internet Connection?"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by tomihasa on 2008-01-27
I have installed Ubuntu 7.10 to my PlayStation 3 and I have connected it to my ADSL modem. How do I get an Internet connection to work with my setup? I have tried adding my DNS server's IP address to the Network Settings window. I have also tried setting off the "Enable roaming mode" and setting "Automatic configuration (DHCP)".

---

### Post by scorp123 on 2008-01-27
You're not providing any technically relevant info.
 
Besides ... how is the PS3 even supposed to connect to the Internet? Do you have an Ethernet connector on that thing or does it have a WLAN interface somewhere somehow? If so, did you configure the WLAN part properly, e.g. encryption keys and all that? If you have WLAN, does the "Network Manager" icon (I'm assuming you have that on the PS3 relase ... I don't know as I have only used Ubuntu on computers so far and never on a gaming console) list your WLAN or wired network?

Aside from that: Do you get an IP address? Does your Ubuntu installation even see the network interface? Open a terminal and please give the results of these commands: ```
dmesg
ifconfig -a
route -n
``` What you have to look out for: [LIST]
[*]**dmesg**:
Does it mention anything about any interfaces, e.g. "eth0", "eth1", "wlan0" or "wifi0" or anything like that?

[*]**ifconfig -a**:
Do you get an IP address?

[*]**route -n**:
Do you get any route? e.g. does the default route "0.0.0.0" point to your ADSL router's address?[/LIST]

---

### Post by tomihasa on 2008-01-28
With PS3's operating system I can connect to the Internet with wire or without wire. I have an ADSL modem (ZyXEL Prestige 660R-61) and a wireless router (D-Link DI-524UP). When using wire, PS3 is connected to the router. When using PS3 without wire, I have given the encryption key to the PS3 and it works fine that way also.

My Network Settings window lists these:

[x] Wired connection.
[ ] Modem connection.

> **scorp123 said:**
> 
[LIST][*]**dmesg**:[/LIST]
Does it mention anything about any interfaces, e.g. "eth0", "eth1", "wlan0" or "wifi0" or anything like that?


Yes, eth0 is mentioned (see print at the end of this message, if interested).

> **scorp123 said:**
> 
[LIST][*]**ifconfig -a**:[/LIST]
Do you get an IP address?


IP address 192.168.0.2 is mentioned (see print at the end of this message), but it may have something to do with my router.

> **scorp123 said:**
> 
[LIST][*]**route -n**:[/LIST]
Do you get any route? e.g. does the default route "0.0.0.0" point to your ADSL router's address?


Yes, I think so, the IP address 192.168.0.1 is mentioned (see print at the end of this message).

Command prints below (sorry if I'm giving too much info). The end part of UUID has been removed, just in case.

```

**dmesg**
[    0.000000] Using PS3 machine description
[    0.000000] Page orders: linear mapping = 24, virtual = 12, io = 12
[    0.000000] Found initrd at 0xc000000001f6d000:0xc000000002784000
[    0.000000] Starting Linux PPC64 #1 SMP Sun Oct 14 23:42:29 GMT 2007
[    0.000000] -----------------------------------------------------
[    0.000000] ppc64_pft_size                = 0x14
[    0.000000] physicalMemorySize            = 0x8000000
[    0.000000] ppc64_caches.dcache_line_size = 0x80
[    0.000000] ppc64_caches.icache_line_size = 0x80
[    0.000000] htab_address                  = 0x0000000000000000
[    0.000000] htab_hash_mask                = 0x1fff
[    0.000000] -----------------------------------------------------
[    0.000000] Linux version 2.6.22-14-cell (buildd@ross) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:42:29 GMT 2007 (Unofficial)
[    0.000000] *** 0000 : CF000012
[    0.000000] 
[    0.000000] *** 0000 : Setup Arch
[    0.000000] [boot]0012 Setup Arch
[    0.000000] Top of RAM: 0x8000000, Total RAM: 0x8000000
[    0.000000] Memory hole size: 0MB
[    0.000000] Entering add_active_range(0, 0, 32768) 0 entries of 256 used
[    0.000000] PS3 firmware version 2.1.0
[    0.000000] ps3fb videomemory: 18874368 bytes at c000000000900000
[    0.000000] ps3flash bounce buffer: 262144 bytes at c0000000008c0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->    32768
[    0.000000]   Normal      32768 ->    32768
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    32768
[    0.000000] On node 0 totalpages: 32768
[    0.000000]   DMA zone: 448 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 32320 pages, LIFO batch:7
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] *** 0000 : CF000015
[    0.000000] 
[    0.000000] *** 0000 : Setup Done
[    0.000000] [boot]0015 Setup Done
[    0.000000] Built 1 zonelists.  Total pages: 32320
[    0.000000] Kernel command line: root=UUID=... video=ps3fb:mode:133 quiet splash 
[    0.000000] ps3_init_IRQ:744: ppe_id 1, thread_id 0, bmp 8a4f00h
[    0.000000] ps3_init_IRQ:744: ppe_id 1, thread_id 1, bmp 8abf00h
[    0.000000] PID hash table entries: 512 (order: 9, 4096 bytes)
[    0.000000] time_init: decrementer frequency = 79.800000 MHz
[    0.000000] time_init: processor frequency   = 3192.000000 MHz
[   43.023147] Console: colour dummy device 80x25
[   43.023361] Dentry cache hash table entries: 16384 (order: 5, 131072 bytes)
[   43.023571] Inode-cache hash table entries: 8192 (order: 4, 65536 bytes)
[   43.023653] freeing bootmem node 0
[   43.038178] Memory: 94964k/131072k available (5452k kernel code, 36108k reserved, 740k data, 606k bss, 292k init)
[   43.038885] SLUB: Genslabs=25, HWalign=128, Order=0-1, MinObjects=4, CPUs=2, Nodes=16
[   43.039139] Calibrating delay loop... 158.72 BogoMIPS (lpj=317440)
[   43.116955] Security Framework v1.0.0 initialized
[   43.117036] SELinux:  Disabled at boot.
[   43.117413] Mount-cache hash table entries: 256
[   43.120900] ps3_host_map:670: hwirq 7, virq 16
[   43.120914] ps3_virq_setup:194: outlet 7 => cpu 1, virq 16
[   43.120925] ps3_chip_mask:107: thread_id 1, virq 16
[   43.120958] ps3_chip_unmask:128: thread_id 1, virq 16
[   43.120974] ps3_host_map:670: hwirq 11, virq 17
[   43.120980] Processor 1 found.
[   43.120986] ps3_virq_setup:194: outlet 11 => cpu 1, virq 17
[   43.120994] ps3_chip_mask:107: thread_id 1, virq 17
[   43.121005] ps3_chip_unmask:128: thread_id 1, virq 17
[   43.121021] ps3_host_map:670: hwirq 15, virq 18
[   43.121037] ps3_virq_setup:194: outlet 15 => cpu 1, virq 18
[   43.121053] ps3_chip_mask:107: thread_id 1, virq 18
[   43.121071] ps3_chip_unmask:128: thread_id 1, virq 18
[   43.121093] ps3_host_map:670: hwirq 19, virq 19
[   43.121109] ps3_virq_setup:194: outlet 19 => cpu 1, virq 19
[   43.121124] ps3_chip_mask:107: thread_id 1, virq 19
[   43.121143] ps3_chip_unmask:128: thread_id 1, virq 19
[   43.121161] ps3_register_ipi_debug_brk:689: cpu 1, virq 19, mask 100000000000h
[   43.121188] Brought up 2 CPUs
[   43.121205] ps3_host_map:670: hwirq 23, virq 23
[   43.121212] ps3_virq_setup:194: outlet 23 => cpu 0, virq 23
[   43.121218] ps3_chip_mask:107: thread_id 0, virq 23
[   43.121227] ps3_chip_unmask:128: thread_id 0, virq 23
[   43.121237] ps3_host_map:670: hwirq 35, virq 35
[   43.121243] ps3_virq_setup:194: outlet 35 => cpu 0, virq 35
[   43.121249] ps3_chip_mask:107: thread_id 0, virq 35
[   43.121257] ps3_chip_unmask:128: thread_id 0, virq 35
[   43.121267] ps3_host_map:670: hwirq 36, virq 36
[   43.121273] ps3_virq_setup:194: outlet 36 => cpu 0, virq 36
[   43.121279] ps3_chip_mask:107: thread_id 0, virq 36
[   43.121287] ps3_chip_unmask:128: thread_id 0, virq 36
[   43.121297] ps3_host_map:670: hwirq 37, virq 37
[   43.121303] ps3_virq_setup:194: outlet 37 => cpu 0, virq 37
[   43.121309] ps3_chip_mask:107: thread_id 0, virq 37
[   43.121316] ps3_chip_unmask:128: thread_id 0, virq 37
[   43.121323] ps3_register_ipi_debug_brk:689: cpu 0, virq 37, mask 4000000h
[   43.134480] migration_cost=1
[   43.205330]  -> ps3_system_bus_init:486
[   43.205408]  <- ps3_system_bus_init:496
[   43.205531] NET: Registered protocol family 16
[   43.205840] *** 0000 : Linux ppc64
[   43.205843] 
[   43.205847] *** 0000 : #1 SMP Sun Oct 14 23:42:29 GMT 2007
[   43.206086] PCI: Probing PCI hardware
[   43.206092] PCI: Probing PCI hardware done
[   43.206098] Registering pmac pic with sysfs...
[   43.207646]  -> ps3av_module_init:997
[   43.207653]  -> ps3_system_bus_driver_register:763: ps3_av
[   43.207744]  <- ps3_system_bus_driver_register:767: ps3_av
[   43.207750]  <- ps3av_module_init:1007
[   43.207802] NET: Registered protocol family 8
[   43.207808] NET: Registered protocol family 20
[   43.208648] NET: Registered protocol family 2
[   43.256701] IP route cache hash table entries: 1024 (order: 1, 8192 bytes)
[   43.256859] TCP established hash table entries: 4096 (order: 4, 98304 bytes)
[   43.256971] TCP bind hash table entries: 4096 (order: 4, 65536 bytes)
[   43.257088] TCP: Hash tables configured (established 4096 bind 4096)
[   43.257094] TCP reno registered
[   43.272945] checking if image is initramfs... it is
[   44.723446] Freeing initrd memory: 8284k freed
[   44.724994] IBM eBus Device Driver
[   44.725284] ps3_host_map:670: hwirq 39, virq 39
[   44.725293] ps3_virq_setup:194: outlet 39 => cpu 0, virq 39
[   44.725299] ps3_chip_mask:107: thread_id 0, virq 39
[   44.725312] ps3_host_map:670: hwirq 40, virq 40
[   44.725319] ps3_virq_setup:194: outlet 40 => cpu 0, virq 40
[   44.725325] ps3_chip_mask:107: thread_id 0, virq 40
[   44.725334] ps3_host_map:670: hwirq 41, virq 41
[   44.725340] ps3_virq_setup:194: outlet 41 => cpu 0, virq 41
[   44.725346] ps3_chip_mask:107: thread_id 0, virq 41
[   44.725376] ps3_chip_unmask:128: thread_id 0, virq 39
[   44.725390] ps3_chip_unmask:128: thread_id 0, virq 40
[   44.725402] ps3_chip_unmask:128: thread_id 0, virq 41
[   44.725548] ps3_host_map:670: hwirq 43, virq 43
[   44.725555] ps3_virq_setup:194: outlet 43 => cpu 0, virq 43
[   44.725561] ps3_chip_mask:107: thread_id 0, virq 43
[   44.725571] ps3_host_map:670: hwirq 44, virq 44
[   44.725577] ps3_virq_setup:194: outlet 44 => cpu 0, virq 44
[   44.725583] ps3_chip_mask:107: thread_id 0, virq 44
[   44.725592] ps3_host_map:670: hwirq 45, virq 45
[   44.725598] ps3_virq_setup:194: outlet 45 => cpu 0, virq 45
[   44.725604] ps3_chip_mask:107: thread_id 0, virq 45
[   44.725623] ps3_chip_unmask:128: thread_id 0, virq 43
[   44.725636] ps3_chip_unmask:128: thread_id 0, virq 44
[   44.725647] ps3_chip_unmask:128: thread_id 0, virq 45
[   44.725781] ps3_host_map:670: hwirq 47, virq 47
[   44.725788] ps3_virq_setup:194: outlet 47 => cpu 0, virq 47
[   44.725794] ps3_chip_mask:107: thread_id 0, virq 47
[   44.725804] ps3_host_map:670: hwirq 48, virq 48
[   44.725810] ps3_virq_setup:194: outlet 48 => cpu 0, virq 48
[   44.725816] ps3_chip_mask:107: thread_id 0, virq 48
[   44.725825] ps3_host_map:670: hwirq 49, virq 49
[   44.725831] ps3_virq_setup:194: outlet 49 => cpu 0, virq 49
[   44.725837] ps3_chip_mask:107: thread_id 0, virq 49
[   44.725855] ps3_chip_unmask:128: thread_id 0, virq 47
[   44.725869] ps3_chip_unmask:128: thread_id 0, virq 48
[   44.725880] ps3_chip_unmask:128: thread_id 0, virq 49
[   44.726010] ps3_host_map:670: hwirq 51, virq 51
[   44.726017] ps3_virq_setup:194: outlet 51 => cpu 0, virq 51
[   44.726023] ps3_chip_mask:107: thread_id 0, virq 51
[   44.726033] ps3_host_map:670: hwirq 52, virq 52
[   44.726039] ps3_virq_setup:194: outlet 52 => cpu 0, virq 52
[   44.726045] ps3_chip_mask:107: thread_id 0, virq 52
[   44.726054] ps3_host_map:670: hwirq 53, virq 53
[   44.726060] ps3_virq_setup:194: outlet 53 => cpu 0, virq 53
[   44.726066] ps3_chip_mask:107: thread_id 0, virq 53
[   44.726083] ps3_chip_unmask:128: thread_id 0, virq 51
[   44.726101] ps3_chip_unmask:128: thread_id 0, virq 52
[   44.726113] ps3_chip_unmask:128: thread_id 0, virq 53
[   44.726253] ps3_host_map:670: hwirq 55, virq 55
[   44.726260] ps3_virq_setup:194: outlet 55 => cpu 0, virq 55
[   44.726266] ps3_chip_mask:107: thread_id 0, virq 55
[   44.726276] ps3_host_map:670: hwirq 56, virq 56
[   44.726282] ps3_virq_setup:194: outlet 56 => cpu 0, virq 56
[   44.726288] ps3_chip_mask:107: thread_id 0, virq 56
[   44.726297] ps3_host_map:670: hwirq 57, virq 57
[   44.726303] ps3_virq_setup:194: outlet 57 => cpu 0, virq 57
[   44.726309] ps3_chip_mask:107: thread_id 0, virq 57
[   44.726327] ps3_chip_unmask:128: thread_id 0, virq 55
[   44.726338] ps3_chip_unmask:128: thread_id 0, virq 56
[   44.726350] ps3_chip_unmask:128: thread_id 0, virq 57
[   44.726479] ps3_host_map:670: hwirq 59, virq 59
[   44.726486] ps3_virq_setup:194: outlet 59 => cpu 0, virq 59
[   44.726493] ps3_chip_mask:107: thread_id 0, virq 59
[   44.726505] ps3_host_map:670: hwirq 60, virq 60
[   44.726511] ps3_virq_setup:194: outlet 60 => cpu 0, virq 60
[   44.726517] ps3_chip_mask:107: thread_id 0, virq 60
[   44.726526] ps3_host_map:670: hwirq 61, virq 61
[   44.726532] ps3_virq_setup:194: outlet 61 => cpu 0, virq 61
[   44.726538] ps3_chip_mask:107: thread_id 0, virq 61
[   44.726557] ps3_chip_unmask:128: thread_id 0, virq 59
[   44.726569] ps3_chip_unmask:128: thread_id 0, virq 60
[   44.726586] ps3_chip_unmask:128: thread_id 0, virq 61
[   44.726861]  -> ps3_storage_wait_for_device:296: bus_id 4, dev_id 1, dev_type 14
[   44.727042] ps3_system_bus_match:354: dev=4(vuart_01), drv=4(ps3_av): match
[   44.727053]  -> ps3_system_bus_probe:365: vuart_01
[   44.727074] ps3_host_map:670: hwirq 62, virq 62
[   44.727081] ps3_virq_setup:194: outlet 62 => cpu 0, virq 62
[   44.727087] ps3_chip_mask:107: thread_id 0, virq 62
[   44.727097] ps3_chip_unmask:128: thread_id 0, virq 62
[   44.727118] ps3_av vuart_01:  -> ps3av_probe:897
[   44.727124] ps3_av vuart_01:   timeout=5000
[   44.727161] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   44.727176] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   44.727181] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   44.727227] ps3_system_bus_match:354: dev=8(sb_01), drv=4(ps3_av): miss
[   44.727265]  -> ps3_storage_wait_for_device:296: bus_id 4, dev_id 3, dev_type 5
[   44.727399] ps3_system_bus_match:354: dev=7(sb_02), drv=4(ps3_av): miss
[   44.727427]  -> ps3_storage_wait_for_device:296: bus_id 4, dev_id 2, dev_type 0
[   44.727557] ps3_system_bus_match:354: dev=6(sb_03), drv=4(ps3_av): miss
[   44.756635] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   44.756644] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   44.756658] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   44.756664] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   44.788632] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   44.788639] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   44.788650] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   44.788655] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   44.820629] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   44.820637] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   44.820648] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   44.820654] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   44.852629] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   44.852637] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   44.852647] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   44.852653] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   44.884630] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   44.884639] ps3_av vuart_01:  <- ps3av_probe:948
[   44.884644]  <- ps3_system_bus_probe:376: vuart_01
[   44.884813] ps3_system_bus_match:354: dev=5(vuart_02), drv=4(ps3_av): miss
[   44.884906] ps3_system_bus_match:354: dev=10(ioc0_01), drv=4(ps3_av): miss
[   44.885031] ps3_system_bus_match:354: dev=3(sb_04), drv=4(ps3_av): miss
[   44.885155] ps3_system_bus_match:354: dev=1(sb_05), drv=4(ps3_av): miss
[   44.885253] ps3_system_bus_match:354: dev=2(sb_06), drv=4(ps3_av): miss
[   44.885365] ps3_system_bus_match:354: dev=1(sb_07), drv=4(ps3_av): miss
[   44.885473] ps3_system_bus_match:354: dev=2(sb_08), drv=4(ps3_av): miss
[   44.885572] ps3_system_bus_match:354: dev=9(ioc0_02), drv=4(ps3_av): miss
[   44.885795] audit: initializing netlink socket (disabled)
[   44.885820] audit(1201517347.868:1): initialized
[   44.885958] Total HugeTLB memory allocated, 0
[   44.892314] VFS: Disk quotas dquot_6.5.1
[   44.892453] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   44.892898] io scheduler noop registered
[   44.892905] io scheduler anticipatory registered
[   44.892911] io scheduler deadline registered
[   44.893174] io scheduler cfq registered (default)
[   44.893943]  -> ps3_system_bus_driver_register:763: ps3fb
[   44.894018] ps3_system_bus_match:354: dev=8(sb_01), drv=10(ps3fb): miss
[   44.894027] ps3_system_bus_match:354: dev=7(sb_02), drv=10(ps3fb): miss
[   44.894035] ps3_system_bus_match:354: dev=6(sb_03), drv=10(ps3fb): miss
[   44.894045] ps3_system_bus_match:354: dev=5(vuart_02), drv=10(ps3fb): miss
[   44.894053] ps3_system_bus_match:354: dev=10(ioc0_01), drv=10(ps3fb): match
[   44.894064]  -> ps3_system_bus_probe:365: ioc0_01
[   44.908448] ps3_host_map:670: hwirq 2, virq 20
[   44.908457] ps3_virq_setup:194: outlet 2 => cpu 0, virq 20
[   44.908464] ps3_chip_mask:107: thread_id 0, virq 20
[   44.908477] ps3_chip_unmask:128: thread_id 0, virq 20
[   44.917155] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   44.917178] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   44.917183] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   44.948633] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   44.948642] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   44.948653] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   44.948657] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   44.980646] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   44.984656] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   44.984683] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   44.984692] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   45.013836] Console: switching to colour frame buffer device 240x67
[   45.016655] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   45.046026] fb0: PS3 frame buffer device, using 18432 KiB of video memory
[   45.046091]  <- ps3_system_bus_probe:376: ioc0_01
[   45.046104] ps3_system_bus_match:354: dev=3(sb_04), drv=10(ps3fb): miss
[   45.046113] ps3_system_bus_match:354: dev=1(sb_05), drv=10(ps3fb): miss
[   45.046121] ps3_system_bus_match:354: dev=2(sb_06), drv=10(ps3fb): miss
[   45.046129] ps3_system_bus_match:354: dev=1(sb_07), drv=10(ps3fb): miss
[   45.046137] ps3_system_bus_match:354: dev=2(sb_08), drv=10(ps3fb): miss
[   45.046145] ps3_system_bus_match:354: dev=9(ioc0_02), drv=10(ps3fb): miss
[   45.046160]  <- ps3_system_bus_driver_register:767: ps3fb
[   45.121603] vio_register_driver: driver hvc_console registering
[   45.121691] HVSI: registered 0 devices
[   45.124180] Generic RTC Driver v1.07
[   45.124279] TX39/49 Serial driver version 1.09
[   45.124677] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   45.124699] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   45.124705] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   45.126112] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   45.126517] input: Macintosh mouse button emulation as /class/input/input0
[   45.126843] mice: PS/2 mouse device common for all mice
[   45.127035]  -> ps3_system_bus_driver_register:763: ps3_sys_manager
[   45.127109] ps3_system_bus_match:354: dev=8(sb_01), drv=5(ps3_sys_manager): miss
[   45.127118] ps3_system_bus_match:354: dev=7(sb_02), drv=5(ps3_sys_manager): miss
[   45.127127] ps3_system_bus_match:354: dev=6(sb_03), drv=5(ps3_sys_manager): miss
[   45.127137] ps3_system_bus_match:354: dev=5(vuart_02), drv=5(ps3_sys_manager): match
[   45.127149]  -> ps3_system_bus_probe:365: vuart_02
[   45.127175]  <- ps3_system_bus_probe:376: vuart_02
[   45.127186] ps3_system_bus_match:354: dev=3(sb_04), drv=5(ps3_sys_manager): miss
[   45.127194] ps3_system_bus_match:354: dev=1(sb_05), drv=5(ps3_sys_manager): miss
[   45.127203] ps3_system_bus_match:354: dev=2(sb_06), drv=5(ps3_sys_manager): miss
[   45.127211] ps3_system_bus_match:354: dev=1(sb_07), drv=5(ps3_sys_manager): miss
[   45.127220] ps3_system_bus_match:354: dev=2(sb_08), drv=5(ps3_sys_manager): miss
[   45.127228] ps3_system_bus_match:354: dev=9(ioc0_02), drv=5(ps3_sys_manager): miss
[   45.127238]  <- ps3_system_bus_driver_register:767: ps3_sys_manager
[   45.127573] TCP cubic registered
[   45.127607] NET: Registered protocol family 1
[   45.127854] Freeing unused kernel memory: 292k freed
[   45.160643] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   45.160654] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   45.160673] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   45.160679] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   45.196641] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   45.196654] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   45.196671] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   45.196676] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   45.228641] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   45.532643] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   45.532672] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   45.532683] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   45.768633] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   45.992695] ps3fb: mmap framebuffer P(910000)->V(f6dec000)
[   46.997987] AppArmor: AppArmor initialized<5>audit(1201517349.980:2):  type=1505 info="AppArmor initialized" pid=1158
[   47.044659] fuse init (API version 7.8)
[   47.073643] Failure registering capabilities with primary security module.
[   47.272637] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   47.272656] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   47.272663] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   47.304640] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   47.304658] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   47.304678] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   47.304684] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   47.336644] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   47.568812] ps3disk_init:384: registered block device major 254
[   47.568821]  -> ps3_system_bus_driver_register:763: ps3disk
[   47.568936] ps3_system_bus_match:354: dev=8(sb_01), drv=6(ps3disk): miss
[   47.568945] ps3_system_bus_match:354: dev=7(sb_02), drv=6(ps3disk): miss
[   47.568953] ps3_system_bus_match:354: dev=6(sb_03), drv=6(ps3disk): match
[   47.568965]  -> ps3_system_bus_probe:365: sb_03
[   47.569176] ps3_host_map:670: hwirq 4, virq 21
[   47.569184] ps3_virq_setup:194: outlet 4 => cpu 0, virq 21
[   47.569191] ps3_chip_mask:107: thread_id 0, virq 21
[   47.569207] ps3_sb_event_receive_port_setup:417: interrupt_id 0, virq 21
[   47.569216] ps3_chip_unmask:128: thread_id 0, virq 21
[   47.569232]  -> dma_sb_region_create:656:
[   47.569549] ps3disk sb_03: First accessible region has index 3 start 57168648 size 20971512
[   47.569693]  ps3da: ps3da1 ps3da2 < ps3da5 >
[   47.570646]  <- ps3_system_bus_probe:376: sb_03
[   47.570663] ps3_system_bus_match:354: dev=3(sb_04), drv=6(ps3disk): miss
[   47.570672] ps3_system_bus_match:354: dev=1(sb_05), drv=6(ps3disk): miss
[   47.570680] ps3_system_bus_match:354: dev=2(sb_06), drv=6(ps3disk): miss
[   47.570688] ps3_system_bus_match:354: dev=1(sb_07), drv=6(ps3disk): miss
[   47.570696] ps3_system_bus_match:354: dev=2(sb_08), drv=6(ps3disk): miss
[   47.570705] ps3_system_bus_match:354: dev=9(ioc0_02), drv=6(ps3disk): miss
[   47.570730]  <- ps3_system_bus_driver_register:767: ps3disk
[   47.602286] SCSI subsystem initialized
[   47.604540]  -> ps3_system_bus_driver_register:763: ps3rom
[   47.604675] ps3_system_bus_match:354: dev=8(sb_01), drv=7(ps3rom): miss
[   47.604685] ps3_system_bus_match:354: dev=7(sb_02), drv=7(ps3rom): match
[   47.604697]  -> ps3_system_bus_probe:365: sb_02
[   47.604728] ps3_host_map:670: hwirq 5, virq 22
[   47.604735] ps3_virq_setup:194: outlet 5 => cpu 0, virq 22
[   47.604742] ps3_chip_mask:107: thread_id 0, virq 22
[   47.604756] ps3_sb_event_receive_port_setup:417: interrupt_id 0, virq 22
[   47.604765] ps3_chip_unmask:128: thread_id 0, virq 22
[   47.604780]  -> dma_sb_region_create:656:
[   47.604996] scsi0 : ps3rom
[   47.605949]  <- ps3_system_bus_probe:376: sb_02
[   47.606119] ps3_system_bus_match:354: dev=3(sb_04), drv=7(ps3rom): miss
[   47.606128] ps3_system_bus_match:354: dev=1(sb_05), drv=7(ps3rom): miss
[   47.606136] ps3_system_bus_match:354: dev=2(sb_06), drv=7(ps3rom): miss
[   47.606149] ps3_system_bus_match:354: dev=1(sb_07), drv=7(ps3rom): miss
[   47.606157] ps3_system_bus_match:354: dev=2(sb_08), drv=7(ps3rom): miss
[   47.606165] ps3_system_bus_match:354: dev=9(ioc0_02), drv=7(ps3rom): miss
[   47.606194]  <- ps3_system_bus_driver_register:767: ps3rom
[   47.608731] scsi 0:0:0:0: CD-ROM            SONY     PS-SYSTEM   302R 4094 PQ: 0 ANSI: 0
[   47.790507] usbcore: registered new interface driver usbfs
[   47.790648] usbcore: registered new interface driver hub
[   47.790801] usbcore: registered new device driver usb
[   47.794500] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   47.794509]  -> ps3_system_bus_driver_register:763: ps3-ohci-driver
[   47.794611] ps3_system_bus_match:354: dev=8(sb_01), drv=2(ps3-ohci-driver): miss
[   47.794629] ps3_system_bus_match:354: dev=3(sb_04), drv=2(ps3-ohci-driver): miss
[   47.794637] ps3_system_bus_match:354: dev=1(sb_05), drv=2(ps3-ohci-driver): miss
[   47.794646] ps3_system_bus_match:354: dev=2(sb_06), drv=2(ps3-ohci-driver): match
[   47.794658]  -> ps3_system_bus_probe:365: sb_06
[   47.794686] dma_sb_region_create_linear:987: forcing 16M pages for linear map
[   47.794691]  -> dma_sb_region_create:656:
[   47.794796] ps3_host_map:670: hwirq 6, virq 24
[   47.794804] ps3_virq_setup:194: outlet 6 => cpu 0, virq 24
[   47.794810] ps3_chip_mask:107: thread_id 0, virq 24
[   47.794838] ps3-ohci-driver sb_06: PS3 OHCI Host Controller
[   47.795030] ps3-ohci-driver sb_06: new USB bus registered, assigned bus number 1
[   47.795083] ps3_chip_unmask:128: thread_id 0, virq 24
[   47.795100] ps3-ohci-driver sb_06: irq 24, io mem 0x4000002a0000
[   48.100539] usb usb1: configuration #1 chosen from 1 choice
[   48.100706] hub 1-0:1.0: USB hub found
[   48.100730] hub 1-0:1.0: 2 ports detected
[   48.360977]  <- ps3_system_bus_probe:376: sb_06
[   48.361015] ps3_system_bus_match:354: dev=1(sb_07), drv=2(ps3-ohci-driver): miss
[   48.361024] ps3_system_bus_match:354: dev=2(sb_08), drv=2(ps3-ohci-driver): match
[   48.361036]  -> ps3_system_bus_probe:365: sb_08
[   48.361055] dma_sb_region_create_linear:987: forcing 16M pages for linear map
[   48.361060]  -> dma_sb_region_create:656:
[   48.361158] ps3_host_map:670: hwirq 8, virq 25
[   48.361165] ps3_virq_setup:194: outlet 8 => cpu 0, virq 25
[   48.361172] ps3_chip_mask:107: thread_id 0, virq 25
[   48.361195] ps3-ohci-driver sb_08: PS3 OHCI Host Controller
[   48.361352] ps3-ohci-driver sb_08: new USB bus registered, assigned bus number 2
[   48.361391] ps3_chip_unmask:128: thread_id 0, virq 25
[   48.361405] ps3-ohci-driver sb_08: irq 25, io mem 0x4000002b0000
[   48.668491] usb usb2: configuration #1 chosen from 1 choice
[   48.668645] hub 2-0:1.0: USB hub found
[   48.668666] hub 2-0:1.0: 2 ports detected
[   48.672642] usb 1-2: new full speed USB device using ps3-ohci-driver and address 2
[   48.878003] usb 1-2: configuration #1 chosen from 1 choice
[   48.879808] hub 1-2:1.0: USB hub found
[   48.881678] hub 1-2:1.0: 4 ports detected
[   48.928952]  <- ps3_system_bus_probe:376: sb_08
[   48.928964] ps3_system_bus_match:354: dev=9(ioc0_02), drv=2(ps3-ohci-driver): miss
[   48.928996]  <- ps3_system_bus_driver_register:767: ps3-ohci-driver
[   48.942911]  -> ps3_system_bus_driver_register:763: ps3-ehci-driver
[   48.942995] ps3_system_bus_match:354: dev=8(sb_01), drv=1(ps3-ehci-driver): miss
[   48.943012] ps3_system_bus_match:354: dev=3(sb_04), drv=1(ps3-ehci-driver): miss
[   48.943020] ps3_system_bus_match:354: dev=1(sb_05), drv=1(ps3-ehci-driver): match
[   48.943032]  -> ps3_system_bus_probe:365: sb_05
[   48.943049] dma_sb_region_create_linear:987: forcing 16M pages for linear map
[   48.943055]  -> dma_sb_region_create:656:
[   48.943165] ps3_host_map:670: hwirq 9, virq 26
[   48.943172] ps3_virq_setup:194: outlet 9 => cpu 0, virq 26
[   48.943179] ps3_chip_mask:107: thread_id 0, virq 26
[   48.943207] ps3-ehci-driver sb_05: PS3 EHCI Host Controller
[   48.943343] ps3-ehci-driver sb_05: new USB bus registered, assigned bus number 3
[   48.964662] ps3_chip_unmask:128: thread_id 0, virq 26
[   48.964681] ps3-ehci-driver sb_05: irq 26, io mem 0x4000002c0000
[   48.964704] ps3-ehci-driver sb_05: USB 0.0 started, EHCI 1.00, driver 10 Dec 2004
[   48.965063] usb usb3: configuration #1 chosen from 1 choice
[   48.965190] hub 3-0:1.0: USB hub found
[   48.965208] hub 3-0:1.0: 2 ports detected
[   48.997020] usb 1-2: USB disconnect, address 2
[   49.068886]  <- ps3_system_bus_probe:376: sb_05
[   49.068899] ps3_system_bus_match:354: dev=1(sb_07), drv=1(ps3-ehci-driver): match
[   49.068911]  -> ps3_system_bus_probe:365: sb_07
[   49.068920] dma_sb_region_create_linear:987: forcing 16M pages for linear map
[   49.068925]  -> dma_sb_region_create:656:
[   49.069032] ps3_host_map:670: hwirq 10, virq 27
[   49.069039] ps3_virq_setup:194: outlet 10 => cpu 0, virq 27
[   49.069046] ps3_chip_mask:107: thread_id 0, virq 27
[   49.069070] ps3-ehci-driver sb_07: PS3 EHCI Host Controller
[   49.069200] ps3-ehci-driver sb_07: new USB bus registered, assigned bus number 4
[   49.092635] ps3_chip_unmask:128: thread_id 0, virq 27
[   49.092653] ps3-ehci-driver sb_07: irq 27, io mem 0x4000002d0000
[   49.092668] ps3-ehci-driver sb_07: USB 0.0 started, EHCI 1.00, driver 10 Dec 2004
[   49.092998] usb usb4: configuration #1 chosen from 1 choice
[   49.093117] hub 4-0:1.0: USB hub found
[   49.093135] hub 4-0:1.0: 2 ports detected
[   49.196912]  <- ps3_system_bus_probe:376: sb_07
[   49.196924] ps3_system_bus_match:354: dev=9(ioc0_02), drv=1(ps3-ehci-driver): miss
[   49.196942]  <- ps3_system_bus_driver_register:767: ps3-ehci-driver
[   49.496677] usb 3-2: new high speed USB device using ps3-ehci-driver and address 2
[   49.631105] usb 3-2: configuration #1 chosen from 1 choice
[   49.631536] hub 3-2:1.0: USB hub found
[   49.631925] hub 3-2:1.0: 4 ports detected
[   49.976666] usb 4-2: new high speed USB device using ps3-ehci-driver and address 2
[   50.058466] kjournald starting.  Commit interval 5 seconds
[   50.058520] EXT3-fs: mounted filesystem with ordered data mode.
[   50.141987] usb 4-2: configuration #1 chosen from 1 choice
[   50.344985] usb 3-2.1: new low speed USB device using ps3-ehci-driver and address 3
[   50.443199] usb 3-2.1: configuration #1 chosen from 1 choice
[   50.644939] usb 3-2.2: new low speed USB device using ps3-ehci-driver and address 4
[   50.741175] usb 3-2.2: configuration #1 chosen from 1 choice
[   61.581004]  -> ps3_system_bus_driver_register:763: ps3_gelic_driver
[   61.585501] ps3_system_bus_match:354: dev=8(sb_01), drv=3(ps3_gelic_driver): miss
[   61.585532] ps3_system_bus_match:354: dev=3(sb_04), drv=3(ps3_gelic_driver): match
[   61.585553]  -> ps3_system_bus_probe:365: sb_04
[   61.585638] dma_sb_region_create_linear:987: forcing 16M pages for linear map
[   61.585650]  -> dma_sb_region_create:656:
[   61.585774] ps3_gelic_driver sb_04: MAC addr 00:1d:0d:16:8f:5b
[   61.585805] ps3_gelic_driver sb_04: firmware is too old for wireless.
[   61.586873]  <- ps3_system_bus_probe:376: sb_04
[   61.586896] ps3_system_bus_match:354: dev=9(ioc0_02), drv=3(ps3_gelic_driver): miss
[   61.586937]  <- ps3_system_bus_driver_register:767: ps3_gelic_driver
[   63.810287]  -> ps3_system_bus_driver_register:763: ps3flash
[   63.816539] ps3_system_bus_match:354: dev=8(sb_01), drv=8(ps3flash): match
[   63.816566]  -> ps3_system_bus_probe:365: sb_01
[   63.816607] ps3_host_map:670: hwirq 12, virq 28
[   63.816648] ps3_virq_setup:194: outlet 12 => cpu 0, virq 28
[   63.816659] ps3_chip_mask:107: thread_id 0, virq 28
[   63.816684] ps3_sb_event_receive_port_setup:417: interrupt_id 0, virq 28
[   63.816700] ps3_chip_unmask:128: thread_id 0, virq 28
[   63.816723]  -> dma_sb_region_create:656:
[   63.822582] ps3flash sb_01: First accessible region has index 5 start 473600 size 8192
[   63.830024] ps3flash sb_01: ps3flash_probe:351: registered misc device 63
[   63.830040]  <- ps3_system_bus_probe:376: sb_01
[   63.830083] ps3_system_bus_match:354: dev=9(ioc0_02), drv=8(ps3flash): miss
[   63.830153]  <- ps3_system_bus_driver_register:767: ps3flash
[   64.304039] usbcore: registered new interface driver hiddev
[   64.314550] input: NOVATEK USB Keyboard as /class/input/input1
[   64.315128] input: USB HID v1.10 Keyboard [NOVATEK USB Keyboard] on usb-sb_05-2.1
[   64.321597] input: NOVATEK USB Keyboard as /class/input/input2
[   64.323030] input,hiddev96: USB HID v1.10 Device [NOVATEK USB Keyboard] on usb-sb_05-2.1
[   64.325690] input: Logitech Optical USB Mouse as /class/input/input3
[   64.326752] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-sb_05-2.2
[   64.326803] usbcore: registered new interface driver usbhid
[   64.326819] /build/buildd/linux-source-2.6.22-2.6.22/debian/build/custom-source-cell/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   64.623240] usbcore: registered new interface driver xpad
[   64.623258] /build/buildd/linux-source-2.6.22-2.6.22/debian/build/custom-source-cell/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   64.976945] Bluetooth: Core ver 2.11
[   64.977105] NET: Registered protocol family 31
[   64.977116] Bluetooth: HCI device and connection manager initialized
[   64.977149] Bluetooth: HCI socket layer initialized
[   64.982729] sr0: scsi3-mmc drive: 0x/0x cd/rw xa/form2 cdda tray
[   64.982763] Uniform CD-ROM driver Revision: 3.20
[   64.983060] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   65.060364] Bluetooth: HCI USB driver ver 2.9
[   65.062158] usbcore: registered new interface driver hci_usb
[   65.183387] ps3_host_map:670: hwirq 13, virq 29
[   65.183403] ps3_virq_setup:194: outlet 13 => cpu 0, virq 29
[   65.183416] ps3_chip_mask:107: thread_id 0, virq 29
[   65.183441] ps3_sb_event_receive_port_setup:417: interrupt_id 0, virq 29
[   65.183459] ps3_chip_unmask:128: thread_id 0, virq 29
[   65.336909] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   66.806473]  -> ps3_system_bus_driver_register:763: snd_ps3
[   66.806563] ps3_system_bus_match:354: dev=9(ioc0_02), drv=9(snd_ps3): match
[   66.806578]  -> ps3_system_bus_probe:365: ioc0_02
[   66.806724] ps3_host_map:670: hwirq 63, virq 63
[   66.806735] ps3_virq_setup:194: outlet 63 => cpu 0, virq 63
[   66.806744] ps3_chip_mask:107: thread_id 0, virq 63
[   66.806764] ps3_chip_unmask:128: thread_id 0, virq 63
[   66.806975] snd_ps3_driver_probe: null vaddr=c000000007ca8000 dma=0x10000
[   66.806998] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   66.807023] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   66.807030] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   66.836647] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   66.836660] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   66.836678] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   66.836684] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   66.868632] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   66.868641] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   66.868653] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   66.868658] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   66.900631] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   66.900640] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   66.900653] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   66.900658] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   66.932632] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   66.932648] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   66.932661] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   66.932667] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   66.964630] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   66.964639] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   66.964651] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   66.964656] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   66.996631] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   66.996642] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   66.996658] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   66.996665] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   67.028631] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   67.028640] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   67.028651] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   67.028657] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   67.060631] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   67.060640] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   67.060652] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   67.060657] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   67.092631] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   67.092640] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   67.092651] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   67.092656] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   67.124628] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   67.124636] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   67.124648] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   67.124654] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   67.156629] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   67.156639] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   67.156654] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   67.156661] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   67.188629] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   67.189646] PS3 sound started. start_delay=2000ms
[   67.189656]  <- ps3_system_bus_probe:376: ioc0_02
[   67.189705]  <- ps3_system_bus_driver_register:767: snd_ps3
[   67.583939] NET: Registered protocol family 17
[   68.452450] loop: module loaded
[   68.800489] Adding 489940k swap on /dev/ps3da5.  Priority:-1 extents:1 across:489940k
[   69.215734] EXT3 FS on ps3da1, internal journal
[   75.080916] ioctl32(hald-probe-hidd:3785): Unknown cmd fd(4) cmd(41004806){t:'H';sz:256} arg(ff8a589c) on /dev/usb/hiddev0
[   75.596240] lp: driver loaded but no devices found
[   75.895138] ppdev: user-space parallel port driver
[   76.378702] audit(1201517380.201:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=3831 profile="/usr/sbin/cupsd"
[   76.797093] Failure registering capabilities with primary security module.
[   77.256833] Bluetooth: L2CAP ver 2.8
[   77.256845] Bluetooth: L2CAP socket layer initialized
[   77.530164] Bluetooth: RFCOMM socket layer initialized
[   77.530984] Bluetooth: RFCOMM TTY layer initialized
[   77.530998] Bluetooth: RFCOMM ver 1.8
[   77.866578] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   77.866605] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   77.866613] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   77.896639] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   77.896649] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   77.896662] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   77.896667] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   77.928632] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   77.928660] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   77.928674] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   77.928685] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   77.992647] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   78.096633] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   78.096653] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   78.096659] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   78.128638] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   78.128649] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   78.128772] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   78.128778] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   78.160632] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   78.160644] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   78.160656] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   78.160662] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   78.192642] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   78.496637] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   78.496728] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   78.496734] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   78.656636] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   80.160638] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   80.160658] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   80.160665] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   80.192651] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   80.192665] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   80.192681] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   80.192687] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   80.232652] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   81.005095] ps3fb: mmap framebuffer P(910000)->V(f6de2000)
[   81.005175] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   81.005198] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   81.005207] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   81.040639] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   81.040648] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   81.040661] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   81.040666] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   81.072632] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   83.541718] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   83.541910] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   83.541916] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   83.572634] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   83.572642] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   83.572653] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   83.572658] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   83.604632] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.356251] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   88.356281] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   88.356291] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.384652] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.384680] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   88.384705] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   88.384721] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.420654] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.420781] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   88.420815] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   88.420825] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.456659] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.468737] snd_ps3_set_avsetting: called freq=44100 width=16
[   88.468763] snd_ps3_set_avsetting: before freq=3 width=1
[   88.468775] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   88.468873] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   88.468883] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.500646] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.500663] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   88.500686] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   88.500693] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.536654] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.536751] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   88.536955] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   88.536963] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.536973] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.537013] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   88.537088] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   88.537099] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.572659] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.572691] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   88.572717] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   88.572733] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.604647] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.605543] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   88.605576] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   88.605583] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.636655] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.637494] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   88.637528] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   88.637539] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.668649] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.669607] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   88.669639] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   88.669650] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.700650] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.701533] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   88.701565] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   88.701576] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.740732] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.741620] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   88.741825] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   88.741834] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.772639] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.773205] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   88.773225] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   88.773230] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.804636] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.805155] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   88.805174] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   88.805179] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.836635] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   88.836712] snd_ps3_set_avsetting: after freq=2 width=1
[   88.836722] <3>snd_ps3_delay_to_bytes: time=2000 rate=44100 bytes=88200, frames=88200, ret=352800
[   88.836734] snd_ps3_pcm_prepare: vaddr=c000000007db0000 bus=0x0
[   91.429016] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   91.429049] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   91.429057] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   91.460637] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   91.460653] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   91.460670] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   91.460677] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   91.492647] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   91.492667] ps3_av vuart_01:  -> ps3av_vuart_write:191
[   91.492685] ps3_av vuart_01:  <- ps3av_vuart_write:193
[   91.492693] ps3_av vuart_01:  -> ps3av_vuart_read:203
[   91.524657] ps3_av vuart_01:  -> ps3av_vuart_read:203
[  108.943757] NET: Registered protocol family 10
[  108.944160] lo: Disabled Privacy Extensions
[  118.956628] eth0: no IPv6 routers present
[  786.273930] ps3_av vuart_01:  -> ps3av_vuart_write:191
[  786.273966] ps3_av vuart_01:  <- ps3av_vuart_write:193
[  786.273976] ps3_av vuart_01:  -> ps3av_vuart_read:203
[  786.304650] ps3_av vuart_01:  -> ps3av_vuart_read:203
[  786.305390] ps3_av vuart_01:  -> ps3av_vuart_write:191
[  786.305414] ps3_av vuart_01:  <- ps3av_vuart_write:193
[  786.305420] ps3_av vuart_01:  -> ps3av_vuart_read:203
[  786.336651] ps3_av vuart_01:  -> ps3av_vuart_read:203
[  786.337227] ps3_av vuart_01:  -> ps3av_vuart_write:191
[  786.337248] ps3_av vuart_01:  <- ps3av_vuart_write:193
[  786.337254] ps3_av vuart_01:  -> ps3av_vuart_read:203
[  786.368652] ps3_av vuart_01:  -> ps3av_vuart_read:203
[  786.478172] snd_ps3_set_avsetting: called freq=44100 width=16
[  786.478185] snd_ps3_set_avsetting: before freq=2 width=1
[  786.478192] snd_ps3_pcm_prepare: vaddr=c000000007db0000 bus=0x0
[  794.407785] ps3_av vuart_01:  -> ps3av_vuart_write:191
[  794.407820] ps3_av vuart_01:  <- ps3av_vuart_write:193
[  794.407829] ps3_av vuart_01:  -> ps3av_vuart_read:203
[  794.441650] ps3_av vuart_01:  -> ps3av_vuart_read:203
[  794.442062] ps3_av vuart_01:  -> ps3av_vuart_write:191
[  794.442089] ps3_av vuart_01:  <- ps3av_vuart_write:193
[  794.442096] ps3_av vuart_01:  -> ps3av_vuart_read:203
[  794.472652] ps3_av vuart_01:  -> ps3av_vuart_read:203
[  794.473070] ps3_av vuart_01:  -> ps3av_vuart_write:191
[  794.473098] ps3_av vuart_01:  <- ps3av_vuart_write:193
[  794.473108] ps3_av vuart_01:  -> ps3av_vuart_read:203
[  794.504640] ps3_av vuart_01:  -> ps3av_vuart_read:203

```

```

**ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:1D:0D:16:8F:5B  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:dff:fe16:8f5b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1710 errors:0 dropped:854 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20720 (20.2 KB)  TX bytes:101090 (98.7 KB)
          Interrupt:29 

lo        Link encap:Local Loopback  
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

```

**route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0

```

---

### Post by mikeyphi on 2008-01-28
> **tomihasa said:**
> I have installed Ubuntu 7.10 to my PlayStation 3 and I have connected it to my ADSL modem. How do I get an Internet connection to work with my setup? I have tried adding my DNS server's IP address to the Network Settings window. I have also tried setting off the "Enable roaming mode" and setting "Automatic configuration (DHCP)".

From the outputs you've posted - it seems as though your router has recognised the wired connection to your PS3 and allocated it an address.
You should be able to access the Internet - question: what are you using for the Internet, a browser or something else?

---

### Post by tomihasa on 2008-01-28
> **mikeyphi said:**
> From the outputs you've posted - it seems as though your router has recognised the wired connection to your PS3 and allocated it an address.
You should be able to access the Internet - question: what are you using for the Internet, a browser or something else?

I have used Mozilla Firefox, Add/Remove Programs and ping. Print outs:

Mozilla Firefox 2.0.0.6 when visiting [http://www.yahoo.com/](http://www.yahoo.com/) gives me this page:

```
Server not found

Firefox can't find the server at [www.yahoo.com](www.yahoo.com).

    *   Check the address for typing errors such as
          ww.example.com instead of
          [www.example.com](www.example.com)

    *   If you are unable to load any pages, check your computer's 
network
          connection.

    *   If your computer or network is protected by a firewall or proxy, 
make sure
          that Firefox is permitted to access the Web.
```

Add/Remove Applications says:

```
"The list of available applications is out of date"
"To reload the list you need a working internet connection."
```

Ping tells me (with the first ping I waited, with the second ping I pressed Control+c at some point):

```

tomi@localhost:~$ ping www.google.com
ping: unknown host www.google.com
tomi@localhost:~$ ping 64.233.161.107
PING 64.233.161.107 (64.233.161.107) 56(84) bytes of data.

--- 64.233.161.107 ping statistics ---
191 packets transmitted, 0 received, 100% packet loss, time 190010ms

```

---

### Post by scorp123 on 2008-01-28
Hmmm ... Does your ADSL router automatically establish the connection to the Internet? Or do you have to do something special on your computer (when you connect from your computer that is) before the connection can be established?

Also ... Does your router have a web interface of some sorts? Maybe there is more information available why the connection to the Internet is not established? Can you please take a look? e.g.  [http://192.168.0.1](http://192.168.0.1)  .... (I am guessing here ...)

---

### Post by tomihasa on 2008-01-29
I haven't rebooted my router for a while (it has no on/off button, so I unplug and plug it back again lazily), so I decided to be thorough and turned off my ADSL modem, router and PS3 for about a minute (I think I've read somewhere you need to keep your router/modem turned off for about a minute to make sure the memory is wiped or something), restarted them, and now the connection is working!

---

### Post by scorp123 on 2008-01-29
> **tomihasa said:**
>  and now the connection is working! OK, ... as for your outdated packages, you should now be able to execute an update. This should happen automatically (via GNOME's "Update Manager"), but in case you want to do it manually: ```
sudo apt-get update
sudo apt-get upgrade
```

---

