---
title: "Dynex Driver"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by PNP on 2007-07-14
Greetings,

My ethernet on my Latitude D600 recently stopped working.  I purchased a Dynex DX-E201 pcmcia card to use instead.  There appear to be Linux files on the cd, but Ubuntu does not recognize the card.  Any help getting it working?

In the Linux folder on the cd there are the files:
Copying.txt
dxe201.c
kern_compat.h
Makefile

Thanks in advance.
-PNP

---

### Post by starsky on 2007-07-14
hi there :)

ok that's all we need.

go to that directory 
$ cd that_LINUX_folder

Then do this -
$ make

If this reports error, then do this -
$ make all
(ONE of the step above will produce a ".ko" file in your current directory)

If this reports error, post back here what the problem is (the output).

If it doesn't report error, then do this -

$ sudo insmod that_dot_ko_file.ko


post back :)

---

### Post by PNP on 2007-07-14
seth@seth-laptop:~/Desktop/LINUX$ make
gcc -DMODULE -Wall -Wstrict-prototypes -O6 -I/usr/src/linux/include -c dxe201.c
dxe201.c:91:26: error: linux/config.h: No such file or directory
dxe201.c:99:27: error: linux/version.h: No such file or directory
dxe201.c:100:26: error: linux/module.h: No such file or directory
dxe201.c:105:26: error: linux/kernel.h: No such file or directory
dxe201.c:106:26: error: linux/string.h: No such file or directory
dxe201.c:107:25: error: linux/timer.h: No such file or directory
dxe201.c:108:25: error: linux/errno.h: No such file or directory
dxe201.c:109:26: error: linux/ioport.h: No such file or directory
dxe201.c:110:26: error: linux/malloc.h: No such file or directory
dxe201.c:111:29: error: linux/interrupt.h: No such file or directory
dxe201.c:112:23: error: linux/pci.h: No such file or directory
dxe201.c:113:29: error: linux/netdevice.h: No such file or directory
dxe201.c:114:31: error: linux/etherdevice.h: No such file or directory
dxe201.c:115:26: error: linux/skbuff.h: No such file or directory
dxe201.c:116:70: error: asm/processor.h: No such file or directory
dxe201.c:117:24: error: asm/bitops.h: No such file or directory
dxe201.c:118:20: error: asm/io.h: No such file or directory
In file included from dxe201.c:130:
kern_compat.h:78:26: error: linux/bios32.h: No such file or directory
In file included from dxe201.c:130:
kern_compat.h: In function ‘pci_drv_register’:
kern_compat.h:338: warning: implicit declaration of function ‘pcibios_present’
kern_compat.h:339: error: ‘ENODEV’ undeclared (first use in this function)
kern_compat.h:339: error: (Each undeclared identifier is reported only once
kern_compat.h:339: error: for each function it appears in.)
kern_compat.h:342: error: ‘u32’ undeclared (first use in this function)
kern_compat.h:342: error: expected ‘;’ before ‘pci_id’
kern_compat.h:343: error: ‘u16’ undeclared (first use in this function)
kern_compat.h:343: error: expected ‘;’ before ‘pci_command’
kern_compat.h:347: error: expected ‘;’ before ‘pci_busaddr’
kern_compat.h:348: error: ‘u8’ undeclared (first use in this function)
kern_compat.h:348: error: expected ‘;’ before ‘pci_irq_line’
kern_compat.h:350: warning: implicit declaration of function ‘pcibios_find_class’
kern_compat.h:352: error: ‘PCIBIOS_SUCCESSFUL’ undeclared (first use in this function)
kern_compat.h:354: warning: implicit declaration of function ‘pcibios_read_config_dword’
kern_compat.h:355: error: ‘PCI_VENDOR_ID’ undeclared (first use in this function)
kern_compat.h:355: error: ‘pci_id’ undeclared (first use in this function)
kern_compat.h:357: error: ‘PCI_SUBSYSTEM_ID’ undeclared (first use in this function)
kern_compat.h:357: error: ‘subsys_id’ undeclared (first use in this function)
kern_compat.h:359: error: ‘PCI_REVISION_ID’ undeclared (first use in this function)
kern_compat.h:359: error: ‘pci_class_rev’ undeclared (first use in this function)
kern_compat.h:373: warning: implicit declaration of function ‘pcibios_read_config_byte’
kern_compat.h:374: error: ‘PCI_INTERRUPT_LINE’ undeclared (first use in this function)
kern_compat.h:374: error: ‘pci_irq_line’ undeclared (first use in this function)
kern_compat.h:378: error: ‘pci_busaddr’ undeclared (first use in this function)
kern_compat.h:390: warning: implicit declaration of function ‘printk’
kern_compat.h:390: error: ‘KERN_INFO’ undeclared (first use in this function)
kern_compat.h:390: error: expected ‘)’ before string constant
kern_compat.h:393: error: ‘PCI_BASE_ADDRESS_SPACE_IO’ undeclared (first use in this function)
kern_compat.h:394: error: ‘PCI_BASE_ADDRESS_IO_MASK’ undeclared (first use in this function)
kern_compat.h:395: warning: implicit declaration of function ‘check_region’
kern_compat.h:397: error: ‘PCI_BASE_ADDRESS_MEM_MASK’ undeclared (first use in this function)
kern_compat.h:397: warning: implicit declaration of function ‘vremap’
kern_compat.h:399: error: expected ‘)’ before string constant
kern_compat.h:406: warning: implicit declaration of function ‘pcibios_read_config_word’
kern_compat.h:407: error: ‘PCI_COMMAND’ undeclared (first use in this function)
kern_compat.h:407: error: ‘pci_command’ undeclared (first use in this function)
kern_compat.h:408: error: ‘new_command’ undeclared (first use in this function)
kern_compat.h:410: error: expected ‘)’ before string constant
kern_compat.h:413: warning: implicit declaration of function ‘pcibios_write_config_word’
kern_compat.h:420: error: ‘PCI_COMMAND_MASTER’ undeclared (first use in this function)
kern_compat.h:422: error: expected ‘;’ before ‘pci_latency’
kern_compat.h:424: error: ‘PCI_LATENCY_TIMER’ undeclared (first use in this function)
kern_compat.h:424: error: ‘pci_latency’ undeclared (first use in this function)
kern_compat.h:426: error: expected ‘)’ before string constant
kern_compat.h:429: warning: implicit declaration of function ‘pcibios_write_config_byte’
kern_compat.h:440: error: ‘MOD_INC_USE_COUNT’ undeclared (first use in this function)
kern_compat.h: In function ‘pci_drv_unregister’:
kern_compat.h:451: error: ‘NULL’ undeclared (first use in this function)
kern_compat.h:453: error: ‘MOD_DEC_USE_COUNT’ undeclared (first use in this function)
kern_compat.h: In function ‘pci_find_capability’:
kern_compat.h:464: error: ‘u16’ undeclared (first use in this function)
kern_compat.h:464: error: expected ‘;’ before ‘pci_status’
kern_compat.h:465: error: ‘u8’ undeclared (first use in this function)
kern_compat.h:465: error: expected ‘;’ before ‘pci_cap_idx’
kern_compat.h:468: error: ‘PCI_STATUS’ undeclared (first use in this function)
kern_compat.h:468: error: ‘pci_status’ undeclared (first use in this function)
kern_compat.h:471: error: ‘pci_cap_idx’ undeclared (first use in this function)
kern_compat.h:473: error: ‘cap_type’ undeclared (first use in this function)
kern_compat.h: In function ‘acpi_wake’:
kern_compat.h:488: error: ‘u32’ undeclared (first use in this function)
kern_compat.h:488: error: expected ‘;’ before ‘base’
kern_compat.h:489: error: ‘u16’ undeclared (first use in this function)
kern_compat.h:489: error: expected ‘;’ before ‘pci_command’
kern_compat.h:490: error: ‘u8’ undeclared (first use in this function)
kern_compat.h:490: error: expected ‘;’ before ‘pci_latency’
kern_compat.h:495: error: ‘pwr_command’ undeclared (first use in this function)
kern_compat.h:498: error: ‘PCI_COMMAND’ undeclared (first use in this function)
kern_compat.h:498: error: ‘pci_command’ undeclared (first use in this function)
kern_compat.h:500: error: ‘PCI_BASE_ADDRESS_0’ undeclared (first use in this function)
kern_compat.h:500: error: ‘base’ undeclared (first use in this function)
kern_compat.h:502: error: ‘PCI_ROM_ADDRESS’ undeclared (first use in this function)
kern_compat.h:502: error: ‘romaddr’ undeclared (first use in this function)
kern_compat.h:503: error: ‘PCI_LATENCY_TIMER’ undeclared (first use in this function)
kern_compat.h:503: error: ‘pci_latency’ undeclared (first use in this function)
kern_compat.h:504: error: ‘PCI_CACHE_LINE_SIZE’ undeclared (first use in this function)
kern_compat.h:504: error: ‘pci_cacheline’ undeclared (first use in this function)
kern_compat.h:505: error: ‘PCI_INTERRUPT_LINE’ undeclared (first use in this function)
kern_compat.h:505: error: ‘irq’ undeclared (first use in this function)
kern_compat.h:510: warning: implicit declaration of function ‘pcibios_write_config_dword’
kern_compat.h: In function ‘acpi_set_pwr_state’:
kern_compat.h:522: error: ‘u16’ undeclared (first use in this function)
kern_compat.h:522: error: expected ‘;’ before ‘pwr_command’
kern_compat.h:527: error: ‘pwr_command’ undeclared (first use in this function)
dxe201.c: At top level:
dxe201.c:219: error: ‘PCI_CLASS_NETWORK_ETHERNET’ undeclared here (not in a function)
dxe201.c:307: error: field ‘stats’ has incomplete type
dxe201.c:308: error: field ‘timer’ has incomplete type
dxe201.c:349: warning: ‘struct pt_regs’ declared inside parameter list
dxe201.c:349: warning: its scope is only this definition or declaration, which is probably not what you want
dxe201.c:351: warning: ‘struct ifreq’ declared inside parameter list
dxe201.c:353: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ether_crc’
dxe201.c:358: error: ‘NULL’ undeclared here (not in a function)
dxe201.c: In function ‘rtl8139_probe1’:
dxe201.c:379: warning: implicit declaration of function ‘init_etherdev’
dxe201.c:379: warning: assignment makes pointer from integer without a cast
dxe201.c:381: error: ‘KERN_INFO’ undeclared (first use in this function)
dxe201.c:381: error: expected ‘)’ before string constant
dxe201.c:385: warning: implicit declaration of function ‘outb’
dxe201.c:390: error: ‘u16’ undeclared (first use in this function)
dxe201.c:390: error: expected expression before ‘)’ token
dxe201.c:390: error: dereferencing pointer to incomplete type
dxe201.c:391: error: too few arguments to function ‘read_eeprom’
dxe201.c:388: warning: unused variable ‘addr_len’
dxe201.c:395: error: dereferencing pointer to incomplete type
dxe201.c:396: error: dereferencing pointer to incomplete type
dxe201.c:399: warning: implicit declaration of function ‘kmalloc’
dxe201.c:399: error: ‘GFP_KERNEL’ undeclared (first use in this function)
dxe201.c:399: warning: assignment makes pointer from integer without a cast
dxe201.c:405: warning: implicit declaration of function ‘request_region’
dxe201.c:405: error: dereferencing pointer to incomplete type
dxe201.c:407: error: dereferencing pointer to incomplete type
dxe201.c:408: error: dereferencing pointer to incomplete type
dxe201.c:410: error: dereferencing pointer to incomplete type
dxe201.c:411: warning: implicit declaration of function ‘memset’
dxe201.c:411: warning: incompatible implicit declaration of built-in function ‘memset’
dxe201.c:431: error: expected ‘)’ before string constant
dxe201.c:436: error: expected ‘)’ before string constant
dxe201.c:461: error: expected ‘)’ before string constant
dxe201.c:467: error: expected ‘)’ before string constant
dxe201.c:476: error: dereferencing pointer to incomplete type
dxe201.c:477: error: dereferencing pointer to incomplete type
dxe201.c:478: error: dereferencing pointer to incomplete type
dxe201.c:479: error: dereferencing pointer to incomplete type
dxe201.c:480: error: dereferencing pointer to incomplete type
dxe201.c:481: error: dereferencing pointer to incomplete type
dxe201.c: In function ‘read_eeprom’:
dxe201.c:522: warning: implicit declaration of function ‘inl’
dxe201.c:532: warning: implicit declaration of function ‘inb’
dxe201.c: In function ‘mdio_read’:
dxe201.c:575: error: dereferencing pointer to incomplete type
dxe201.c:582: warning: implicit declaration of function ‘inw’
dxe201.c:582: error: dereferencing pointer to incomplete type
dxe201.c: In function ‘mdio_write’:
dxe201.c:608: error: dereferencing pointer to incomplete type
dxe201.c:614: warning: implicit declaration of function ‘outw’
dxe201.c:614: error: dereferencing pointer to incomplete type
dxe201.c: In function ‘rtl8129_open’:
dxe201.c:640: error: dereferencing pointer to incomplete type
dxe201.c:641: error: dereferencing pointer to incomplete type
dxe201.c:647: error: ‘MOD_INC_USE_COUNT’ undeclared (first use in this function)
dxe201.c:648: warning: implicit declaration of function ‘request_irq’
dxe201.c:648: error: dereferencing pointer to incomplete type
dxe201.c:648: error: ‘SA_SHIRQ’ undeclared (first use in this function)
dxe201.c:648: error: dereferencing pointer to incomplete type
dxe201.c:649: error: ‘MOD_DEC_USE_COUNT’ undeclared (first use in this function)
dxe201.c:650: error: ‘EAGAIN’ undeclared (first use in this function)
dxe201.c:659: error: ‘GFP_KERNEL’ undeclared (first use in this function)
dxe201.c:659: warning: assignment makes pointer from integer without a cast
dxe201.c:662: error: ‘KERN_ERR’ undeclared (first use in this function)
dxe201.c:662: error: expected ‘)’ before string constant
dxe201.c:665: error: ‘ENOMEM’ undeclared (first use in this function)
dxe201.c:680: warning: implicit declaration of function ‘outl’
dxe201.c:680: error: ‘u32’ undeclared (first use in this function)
dxe201.c:680: error: expected expression before ‘)’ token
dxe201.c:680: error: dereferencing pointer to incomplete type
dxe201.c:681: error: expected expression before ‘)’ token
dxe201.c:681: error: dereferencing pointer to incomplete type
dxe201.c:690: error: ‘u16’ undeclared (first use in this function)
dxe201.c:690: error: expected ‘;’ before ‘mii_reg5’
dxe201.c:691: error: ‘mii_reg5’ undeclared (first use in this function)
dxe201.c:697: error: ‘KERN_INFO’ undeclared (first use in this function)
dxe201.c:697: error: expected ‘)’ before string constant
dxe201.c:708: warning: implicit declaration of function ‘virt_to_bus’
dxe201.c:716: error: dereferencing pointer to incomplete type
dxe201.c:717: error: dereferencing pointer to incomplete type
dxe201.c:718: error: dereferencing pointer to incomplete type
dxe201.c:725: error: ‘KERN_DEBUG’ undeclared (first use in this function)
dxe201.c:725: error: expected ‘)’ before string constant
dxe201.c:732: warning: implicit declaration of function ‘init_timer’
dxe201.c:733: error: ‘jiffies’ undeclared (first use in this function)
dxe201.c:733: error: ‘HZ’ undeclared (first use in this function)
dxe201.c:736: warning: implicit declaration of function ‘add_timer’
dxe201.c: In function ‘rtl_hw_start’:
dxe201.c:744: error: dereferencing pointer to incomplete type
dxe201.c:745: error: dereferencing pointer to incomplete type
dxe201.c:755: error: ‘u32’ undeclared (first use in this function)
dxe201.c:755: error: expected expression before ‘)’ token
dxe201.c:755: error: dereferencing pointer to incomplete type
dxe201.c:756: error: expected expression before ‘)’ token
dxe201.c:756: error: dereferencing pointer to incomplete type
dxe201.c: In function ‘rtl8129_timer’:
dxe201.c:788: error: dereferencing pointer to incomplete type
dxe201.c:789: error: dereferencing pointer to incomplete type
dxe201.c:790: error: ‘HZ’ undeclared (first use in this function)
dxe201.c:797: error: ‘KERN_INFO’ undeclared (first use in this function)
dxe201.c:797: error: expected ‘)’ before string constant
dxe201.c:808: error: dereferencing pointer to incomplete type
dxe201.c:809: error: ‘KERN_ERR’ undeclared (first use in this function)
dxe201.c:809: error: expected ‘)’ before string constant
dxe201.c:811: error: dereferencing pointer to incomplete type
dxe201.c:814: error: dereferencing pointer to incomplete type
dxe201.c:814: error: ‘jiffies’ undeclared (first use in this function)
dxe201.c:814: error: dereferencing pointer to incomplete type
dxe201.c:887: error: ‘KERN_DEBUG’ undeclared (first use in this function)
dxe201.c:887: error: expected ‘)’ before string constant
dxe201.c:890: error: expected ‘)’ before string constant
dxe201.c:892: error: expected ‘)’ before string constant
dxe201.c:896: error: expected ‘)’ before string constant
dxe201.c: In function ‘rtl8129_tx_timeout’:
dxe201.c:906: error: dereferencing pointer to incomplete type
dxe201.c:907: error: dereferencing pointer to incomplete type
dxe201.c:911: error: ‘KERN_ERR’ undeclared (first use in this function)
dxe201.c:911: error: expected ‘)’ before string constant
dxe201.c:919: error: ‘KERN_DEBUG’ undeclared (first use in this function)
dxe201.c:919: error: expected ‘)’ before string constant
dxe201.c:922: error: expected ‘)’ before string constant
dxe201.c:925: error: expected ‘)’ before string constant
dxe201.c:935: warning: implicit declaration of function ‘dev_kfree_skb’
dxe201.c:935: error: ‘FREE_WRITE’ undeclared (first use in this function)
dxe201.c:941: error: dereferencing pointer to incomplete type
dxe201.c: In function ‘rtl8129_init_ring’:
dxe201.c:950: error: dereferencing pointer to incomplete type
dxe201.c: In function ‘rtl8129_start_xmit’:
dxe201.c:966: error: dereferencing pointer to incomplete type
dxe201.c:967: error: dereferencing pointer to incomplete type
dxe201.c:972: warning: implicit declaration of function ‘set_bit’
dxe201.c:972: error: dereferencing pointer to incomplete type
dxe201.c:973: error: ‘jiffies’ undeclared (first use in this function)
dxe201.c:973: error: dereferencing pointer to incomplete type
dxe201.c:973: error: ‘HZ’ undeclared (first use in this function)
dxe201.c:982: error: dereferencing pointer to incomplete type
dxe201.c:983: warning: implicit declaration of function ‘memcpy’
dxe201.c:983: warning: incompatible implicit declaration of built-in function ‘memcpy’
dxe201.c:983: error: dereferencing pointer to incomplete type
dxe201.c:983: error: dereferencing pointer to incomplete type
dxe201.c:986: error: dereferencing pointer to incomplete type
dxe201.c:988: error: dereferencing pointer to incomplete type
dxe201.c:988: error: ‘ETH_ZLEN’ undeclared (first use in this function)
dxe201.c:988: error: dereferencing pointer to incomplete type
dxe201.c:995: warning: implicit declaration of function ‘clear_bit’
dxe201.c:995: error: dereferencing pointer to incomplete type
dxe201.c:999: error: dereferencing pointer to incomplete type
dxe201.c:1004: error: dereferencing pointer to incomplete type
dxe201.c:1006: error: ‘KERN_DEBUG’ undeclared (first use in this function)
dxe201.c:1006: error: expected ‘)’ before string constant
dxe201.c: At top level:
dxe201.c:1014: warning: ‘struct pt_regs’ declared inside parameter list
dxe201.c:1015: error: conflicting types for ‘rtl8129_interrupt’
dxe201.c:349: error: previous declaration of ‘rtl8129_interrupt’ was here
dxe201.c: In function ‘rtl8129_interrupt’:
dxe201.c:1017: error: dereferencing pointer to incomplete type
dxe201.c:1019: error: dereferencing pointer to incomplete type
dxe201.c:1024: error: dereferencing pointer to incomplete type
dxe201.c:1025: error: ‘KERN_ERR’ undeclared (first use in this function)
dxe201.c:1025: error: expected ‘)’ before string constant
dxe201.c:1027: error: dereferencing pointer to incomplete type
dxe201.c:1067: error: ‘KERN_DEBUG’ undeclared (first use in this function)
dxe201.c:1067: error: expected ‘)’ before string constant
dxe201.c:1091: error: ‘KERN_NOTICE’ undeclared (first use in this function)
dxe201.c:1091: error: expected ‘)’ before string constant
dxe201.c:1119: error: ‘FREE_WRITE’ undeclared (first use in this function)
dxe201.c:1121: warning: implicit declaration of function ‘test_bit’
dxe201.c:1124: error: dereferencing pointer to incomplete type
dxe201.c:1125: warning: implicit declaration of function ‘mark_bh’
dxe201.c:1125: error: ‘NET_BH’ undeclared (first use in this function)
dxe201.c:1132: error: expected ‘)’ before string constant
dxe201.c:1144: error: expected ‘)’ before string constant
dxe201.c:1178: error: ‘u32’ undeclared (first use in this function)
dxe201.c:1178: error: expected ‘;’ before ‘pci_cmd_status’
dxe201.c:1179: error: ‘PCI_COMMAND’ undeclared (first use in this function)
dxe201.c:1179: error: ‘pci_cmd_status’ undeclared (first use in this function)
dxe201.c:1181: error: expected ‘)’ before string constant
dxe201.c:1186: error: ‘KERN_WARNING’ undeclared (first use in this function)
dxe201.c:1186: error: expected ‘)’ before string constant
dxe201.c:1196: error: expected ‘)’ before string constant
dxe201.c:1200: error: dereferencing pointer to incomplete type
dxe201.c: In function ‘rtl8129_rx’:
dxe201.c:1211: error: dereferencing pointer to incomplete type
dxe201.c:1212: error: dereferencing pointer to incomplete type
dxe201.c:1214: error: ‘u16’ undeclared (first use in this function)
dxe201.c:1214: error: expected ‘;’ before ‘cur_rx’
dxe201.c:1217: error: ‘KERN_DEBUG’ undeclared (first use in this function)
dxe201.c:1217: error: expected ‘)’ before string constant
dxe201.c:1223: error: ‘cur_rx’ undeclared (first use in this function)
dxe201.c:1224: error: ‘u32’ undeclared (first use in this function)
dxe201.c:1224: error: expected ‘;’ before ‘rx_status’
dxe201.c:1225: error: ‘rx_status’ undeclared (first use in this function)
dxe201.c:1229: error: expected ‘)’ before string constant
dxe201.c:1232: error: expected ‘)’ before string constant
dxe201.c:1239: error: expected ‘)’ before string constant
dxe201.c:1243: error: ‘KERN_NOTICE’ undeclared (first use in this function)
dxe201.c:1243: error: expected ‘)’ before string constant
dxe201.c:1264: warning: implicit declaration of function ‘dev_alloc_skb’
dxe201.c:1264: warning: assignment makes pointer from integer without a cast
dxe201.c:1266: error: ‘KERN_WARNING’ undeclared (first use in this function)
dxe201.c:1266: error: expected ‘)’ before string constant
dxe201.c:1273: error: dereferencing pointer to incomplete type
dxe201.c:1274: warning: implicit declaration of function ‘skb_reserve’
dxe201.c:1278: warning: incompatible implicit declaration of built-in function ‘memcpy’
dxe201.c:1278: warning: implicit declaration of function ‘skb_put’
dxe201.c:1279: warning: passing argument 1 of ‘memcpy’ makes pointer from integer without a cast
dxe201.c:1281: warning: passing argument 1 of ‘memcpy’ makes pointer from integer without a cast
dxe201.c:1284: error: expected ‘)’ before string constant
dxe201.c:1289: warning: incompatible implicit declaration of built-in function ‘memset’
dxe201.c:1292: warning: implicit declaration of function ‘eth_copy_and_sum’
dxe201.c:1296: error: dereferencing pointer to incomplete type
dxe201.c:1296: warning: implicit declaration of function ‘eth_type_trans’
dxe201.c:1297: warning: implicit declaration of function ‘netif_rx’
dxe201.c:1308: error: expected ‘)’ before string constant
dxe201.c: In function ‘rtl8129_close’:
dxe201.c:1319: error: dereferencing pointer to incomplete type
dxe201.c:1320: error: dereferencing pointer to incomplete type
dxe201.c:1323: error: dereferencing pointer to incomplete type
dxe201.c:1324: error: dereferencing pointer to incomplete type
dxe201.c:1327: error: ‘KERN_DEBUG’ undeclared (first use in this function)
dxe201.c:1327: error: expected ‘)’ before string constant
dxe201.c:1340: warning: implicit declaration of function ‘del_timer’
dxe201.c:1342: warning: implicit declaration of function ‘free_irq’
dxe201.c:1342: error: dereferencing pointer to incomplete type
dxe201.c:1346: error: ‘FREE_WRITE’ undeclared (first use in this function)
dxe201.c:1349: warning: implicit declaration of function ‘kfree’
dxe201.c:1356: error: ‘MOD_DEC_USE_COUNT’ undeclared (first use in this function)
dxe201.c: At top level:
dxe201.c:1361: warning: ‘struct ifreq’ declared inside parameter list
dxe201.c:1362: error: conflicting types for ‘mii_ioctl’
dxe201.c:351: error: previous declaration of ‘mii_ioctl’ was here
dxe201.c: In function ‘mii_ioctl’:
dxe201.c:1363: error: dereferencing pointer to incomplete type
dxe201.c:1364: error: ‘u16’ undeclared (first use in this function)
dxe201.c:1364: error: ‘data’ undeclared (first use in this function)
dxe201.c:1364: error: expected expression before ‘)’ token
dxe201.c:1367: error: ‘SIOCDEVPRIVATE’ undeclared (first use in this function)
dxe201.c:1374: warning: implicit declaration of function ‘suser’
dxe201.c:1375: error: ‘EPERM’ undeclared (first use in this function)
dxe201.c:1379: error: ‘EOPNOTSUPP’ undeclared (first use in this function)
dxe201.c: In function ‘rtl8129_get_stats’:
dxe201.c:1386: error: dereferencing pointer to incomplete type
dxe201.c:1387: error: dereferencing pointer to incomplete type
dxe201.c:1389: error: dereferencing pointer to incomplete type
dxe201.c: At top level:
dxe201.c:1401: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ether_crc’
dxe201.c: In function ‘set_rx_mode’:
dxe201.c:1423: error: dereferencing pointer to incomplete type
dxe201.c:1424: error: dereferencing pointer to incomplete type
dxe201.c:1425: error: ‘u32’ undeclared (first use in this function)
dxe201.c:1425: error: expected ‘;’ before ‘mc_filter’
dxe201.c:1429: error: ‘KERN_DEBUG’ undeclared (first use in this function)
dxe201.c:1429: error: expected ‘)’ before string constant
dxe201.c:1433: error: dereferencing pointer to incomplete type
dxe201.c:1433: error: ‘IFF_PROMISC’ undeclared (first use in this function)
dxe201.c:1435: error: ‘KERN_NOTICE’ undeclared (first use in this function)
dxe201.c:1435: error: expected ‘)’ before string constant
dxe201.c:1437: error: ‘mc_filter’ undeclared (first use in this function)
dxe201.c:1438: error: dereferencing pointer to incomplete type
dxe201.c:1439: error: dereferencing pointer to incomplete type
dxe201.c:1439: error: ‘IFF_ALLMULTI’ undeclared (first use in this function)
dxe201.c:1447: error: dereferencing pointer to incomplete type
dxe201.c:1447: error: dereferencing pointer to incomplete type
dxe201.c:1448: error: dereferencing pointer to incomplete type
dxe201.c:1449: warning: implicit declaration of function ‘ether_crc’
dxe201.c:1449: error: ‘ETH_ALEN’ undeclared (first use in this function)
dxe201.c:1449: error: dereferencing pointer to incomplete type
dxe201.c: In function ‘rtl_pwr_event’:
dxe201.c:1462: error: dereferencing pointer to incomplete type
dxe201.c:1463: error: dereferencing pointer to incomplete type
dxe201.c:1466: error: dereferencing pointer to incomplete type
dxe201.c:1469: error: ‘MOD_INC_USE_COUNT’ undeclared (first use in this function)
dxe201.c:1484: error: dereferencing pointer to incomplete type
dxe201.c:1484: error: ‘IFF_UP’ undeclared (first use in this function)
dxe201.c:1485: warning: implicit declaration of function ‘dev_close’
dxe201.c:1486: error: dereferencing pointer to incomplete type
dxe201.c:1486: error: ‘IFF_RUNNING’ undeclared (first use in this function)
dxe201.c:1488: warning: implicit declaration of function ‘unregister_netdev’
dxe201.c:1489: warning: implicit declaration of function ‘release_region’
dxe201.c:1489: error: dereferencing pointer to incomplete type
dxe201.c:1494: error: dereferencing pointer to incomplete type
dxe201.c:1503: error: ‘MOD_DEC_USE_COUNT’ undeclared (first use in this function)
dxe201.c: In function ‘init_module’:
dxe201.c:1594: error: ‘KERN_INFO’ undeclared (first use in this function)
dxe201.c:1594: error: expected ‘)’ before string constant
dxe201.c: In function ‘cleanup_module’:
dxe201.c:1614: error: dereferencing pointer to incomplete type
dxe201.c:1616: error: dereferencing pointer to incomplete type
make: *** [dxe201.o] Error 1
seth@seth-laptop:~/Desktop/LINUX$ make all
make: *** No rule to make target `all'.  Stop.

---

### Post by PNP on 2007-07-14
I did, however, copy the LINUX folder from the installation cd to my desktop.  Should I be using it directly off of the cd?  If so, how do I access the cd through terminal (sorry, i'm new to this).

---

### Post by starsky on 2007-07-14
> **PNP said:**
> I did, however, copy the LINUX folder from the installation cd to my desktop.  Should I be using it directly off of the cd?  If so, how do I access the cd through terminal (sorry, i'm new to this).

no that should be ok. :)

ok do this -

$ sudo apt-get install linux-headers-386

then after that -
$ make

post back :)

---

### Post by PNP on 2007-07-14
seth@seth-laptop:~$ sudo apt-get install linux-headers-386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lm-sensors
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-2.6.20-16-386
The following NEW packages will be installed:
  linux-headers-2.6.20-16-386 linux-headers-386
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 860kB of archives.
After unpacking 7291kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main linux-headers-2.6.20-16-386 2.6.20-16.29 [836kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main linux-headers-386 2.6.20.16.28.1 [24.5kB]
Fetched 860kB in 2s (407kB/s)        
Selecting previously deselected package linux-headers-2.6.20-16-386.
(Reading database ... 110842 files and directories currently installed.)
Unpacking linux-headers-2.6.20-16-386 (from .../linux-headers-2.6.20-16-386_2.6.20-16.29_i386.deb) ...
Selecting previously deselected package linux-headers-386.
Unpacking linux-headers-386 (from .../linux-headers-386_2.6.20.16.28.1_i386.deb) ...
Setting up linux-headers-2.6.20-16-386 (2.6.20-16.29) ...
Setting up linux-headers-386 (2.6.20.16.28.1) ...
seth@seth-laptop:~$ cd ~/Desktop/LINUX
seth@seth-laptop:~/Desktop/LINUX$ make
gcc -DMODULE -Wall -Wstrict-prototypes -O6 -I/usr/src/linux/include -c dxe201.c
dxe201.c:91:26: error: linux/config.h: No such file or directory
dxe201.c:99:27: error: linux/version.h: No such file or directory
dxe201.c:100:26: error: linux/module.h: No such file or directory
dxe201.c:105:26: error: linux/kernel.h: No such file or directory
dxe201.c:106:26: error: linux/string.h: No such file or directory
dxe201.c:107:25: error: linux/timer.h: No such file or directory
dxe201.c:108:25: error: linux/errno.h: No such file or directory
dxe201.c:109:26: error: linux/ioport.h: No such file or directory
dxe201.c:110:26: error: linux/malloc.h: No such file or directory
dxe201.c:111:29: error: linux/interrupt.h: No such file or directory
dxe201.c:112:23: error: linux/pci.h: No such file or directory
dxe201.c:113:29: error: linux/netdevice.h: No such file or directory
dxe201.c:114:31: error: linux/etherdevice.h: No such file or directory
dxe201.c:115:26: error: linux/skbuff.h: No such file or directory
dxe201.c:116:70: error: asm/processor.h: No such file or directory
dxe201.c:117:24: error: asm/bitops.h: No such file or directory
dxe201.c:118:20: error: asm/io.h: No such file or directory
In file included from dxe201.c:130:
kern_compat.h:78:26: error: linux/bios32.h: No such file or directory
In file included from dxe201.c:130:
kern_compat.h: In function ‘pci_drv_register’:
kern_compat.h:338: warning: implicit declaration of function ‘pcibios_present’
kern_compat.h:339: error: ‘ENODEV’ undeclared (first use in this function)
kern_compat.h:339: error: (Each undeclared identifier is reported only once
kern_compat.h:339: error: for each function it appears in.)
kern_compat.h:342: error: ‘u32’ undeclared (first use in this function)
kern_compat.h:342: error: expected ‘;’ before ‘pci_id’
kern_compat.h:343: error: ‘u16’ undeclared (first use in this function)
kern_compat.h:343: error: expected ‘;’ before ‘pci_command’
kern_compat.h:347: error: expected ‘;’ before ‘pci_busaddr’
kern_compat.h:348: error: ‘u8’ undeclared (first use in this function)
kern_compat.h:348: error: expected ‘;’ before ‘pci_irq_line’
kern_compat.h:350: warning: implicit declaration of function ‘pcibios_find_class’
kern_compat.h:352: error: ‘PCIBIOS_SUCCESSFUL’ undeclared (first use in this function)
kern_compat.h:354: warning: implicit declaration of function ‘pcibios_read_config_dword’
kern_compat.h:355: error: ‘PCI_VENDOR_ID’ undeclared (first use in this function)
kern_compat.h:355: error: ‘pci_id’ undeclared (first use in this function)
kern_compat.h:357: error: ‘PCI_SUBSYSTEM_ID’ undeclared (first use in this function)
kern_compat.h:357: error: ‘subsys_id’ undeclared (first use in this function)
kern_compat.h:359: error: ‘PCI_REVISION_ID’ undeclared (first use in this function)
kern_compat.h:359: error: ‘pci_class_rev’ undeclared (first use in this function)
kern_compat.h:373: warning: implicit declaration of function ‘pcibios_read_config_byte’
kern_compat.h:374: error: ‘PCI_INTERRUPT_LINE’ undeclared (first use in this function)
kern_compat.h:374: error: ‘pci_irq_line’ undeclared (first use in this function)
kern_compat.h:378: error: ‘pci_busaddr’ undeclared (first use in this function)
kern_compat.h:390: warning: implicit declaration of function ‘printk’
kern_compat.h:390: error: ‘KERN_INFO’ undeclared (first use in this function)
kern_compat.h:390: error: expected ‘)’ before string constant
kern_compat.h:393: error: ‘PCI_BASE_ADDRESS_SPACE_IO’ undeclared (first use in this function)
kern_compat.h:394: error: ‘PCI_BASE_ADDRESS_IO_MASK’ undeclared (first use in this function)
kern_compat.h:395: warning: implicit declaration of function ‘check_region’
kern_compat.h:397: error: ‘PCI_BASE_ADDRESS_MEM_MASK’ undeclared (first use in this function)
kern_compat.h:397: warning: implicit declaration of function ‘vremap’
kern_compat.h:399: error: expected ‘)’ before string constant
kern_compat.h:406: warning: implicit declaration of function ‘pcibios_read_config_word’
kern_compat.h:407: error: ‘PCI_COMMAND’ undeclared (first use in this function)
kern_compat.h:407: error: ‘pci_command’ undeclared (first use in this function)
kern_compat.h:408: error: ‘new_command’ undeclared (first use in this function)
kern_compat.h:410: error: expected ‘)’ before string constant
kern_compat.h:413: warning: implicit declaration of function ‘pcibios_write_config_word’
kern_compat.h:420: error: ‘PCI_COMMAND_MASTER’ undeclared (first use in this function)
kern_compat.h:422: error: expected ‘;’ before ‘pci_latency’
kern_compat.h:424: error: ‘PCI_LATENCY_TIMER’ undeclared (first use in this function)
kern_compat.h:424: error: ‘pci_latency’ undeclared (first use in this function)
kern_compat.h:426: error: expected ‘)’ before string constant
kern_compat.h:429: warning: implicit declaration of function ‘pcibios_write_config_byte’
kern_compat.h:440: error: ‘MOD_INC_USE_COUNT’ undeclared (first use in this function)
kern_compat.h: In function ‘pci_drv_unregister’:
kern_compat.h:451: error: ‘NULL’ undeclared (first use in this function)
kern_compat.h:453: error: ‘MOD_DEC_USE_COUNT’ undeclared (first use in this function)
kern_compat.h: In function ‘pci_find_capability’:
kern_compat.h:464: error: ‘u16’ undeclared (first use in this function)
kern_compat.h:464: error: expected ‘;’ before ‘pci_status’
kern_compat.h:465: error: ‘u8’ undeclared (first use in this function)
kern_compat.h:465: error: expected ‘;’ before ‘pci_cap_idx’
kern_compat.h:468: error: ‘PCI_STATUS’ undeclared (first use in this function)
kern_compat.h:468: error: ‘pci_status’ undeclared (first use in this function)
kern_compat.h:471: error: ‘pci_cap_idx’ undeclared (first use in this function)
kern_compat.h:473: error: ‘cap_type’ undeclared (first use in this function)
kern_compat.h: In function ‘acpi_wake’:
kern_compat.h:488: error: ‘u32’ undeclared (first use in this function)
kern_compat.h:488: error: expected ‘;’ before ‘base’
kern_compat.h:489: error: ‘u16’ undeclared (first use in this function)
kern_compat.h:489: error: expected ‘;’ before ‘pci_command’
kern_compat.h:490: error: ‘u8’ undeclared (first use in this function)
kern_compat.h:490: error: expected ‘;’ before ‘pci_latency’
kern_compat.h:495: error: ‘pwr_command’ undeclared (first use in this function)
kern_compat.h:498: error: ‘PCI_COMMAND’ undeclared (first use in this function)
kern_compat.h:498: error: ‘pci_command’ undeclared (first use in this function)
kern_compat.h:500: error: ‘PCI_BASE_ADDRESS_0’ undeclared (first use in this function)
kern_compat.h:500: error: ‘base’ undeclared (first use in this function)
kern_compat.h:502: error: ‘PCI_ROM_ADDRESS’ undeclared (first use in this function)
kern_compat.h:502: error: ‘romaddr’ undeclared (first use in this function)
kern_compat.h:503: error: ‘PCI_LATENCY_TIMER’ undeclared (first use in this function)
kern_compat.h:503: error: ‘pci_latency’ undeclared (first use in this function)
kern_compat.h:504: error: ‘PCI_CACHE_LINE_SIZE’ undeclared (first use in this function)
kern_compat.h:504: error: ‘pci_cacheline’ undeclared (first use in this function)
kern_compat.h:505: error: ‘PCI_INTERRUPT_LINE’ undeclared (first use in this function)
kern_compat.h:505: error: ‘irq’ undeclared (first use in this function)
kern_compat.h:510: warning: implicit declaration of function ‘pcibios_write_config_dword’
kern_compat.h: In function ‘acpi_set_pwr_state’:
kern_compat.h:522: error: ‘u16’ undeclared (first use in this function)
kern_compat.h:522: error: expected ‘;’ before ‘pwr_command’
kern_compat.h:527: error: ‘pwr_command’ undeclared (first use in this function)
dxe201.c: At top level:
dxe201.c:219: error: ‘PCI_CLASS_NETWORK_ETHERNET’ undeclared here (not in a function)
dxe201.c:307: error: field ‘stats’ has incomplete type
dxe201.c:308: error: field ‘timer’ has incomplete type
dxe201.c:349: warning: ‘struct pt_regs’ declared inside parameter list
dxe201.c:349: warning: its scope is only this definition or declaration, which is probably not what you want
dxe201.c:351: warning: ‘struct ifreq’ declared inside parameter list
dxe201.c:353: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ether_crc’
dxe201.c:358: error: ‘NULL’ undeclared here (not in a function)
dxe201.c: In function ‘rtl8139_probe1’:
dxe201.c:379: warning: implicit declaration of function ‘init_etherdev’
dxe201.c:379: warning: assignment makes pointer from integer without a cast
dxe201.c:381: error: ‘KERN_INFO’ undeclared (first use in this function)
dxe201.c:381: error: expected ‘)’ before string constant
dxe201.c:385: warning: implicit declaration of function ‘outb’
dxe201.c:390: error: ‘u16’ undeclared (first use in this function)
dxe201.c:390: error: expected expression before ‘)’ token
dxe201.c:390: error: dereferencing pointer to incomplete type
dxe201.c:391: error: too few arguments to function ‘read_eeprom’
dxe201.c:388: warning: unused variable ‘addr_len’
dxe201.c:395: error: dereferencing pointer to incomplete type
dxe201.c:396: error: dereferencing pointer to incomplete type
dxe201.c:399: warning: implicit declaration of function ‘kmalloc’
dxe201.c:399: error: ‘GFP_KERNEL’ undeclared (first use in this function)
dxe201.c:399: warning: assignment makes pointer from integer without a cast
dxe201.c:405: warning: implicit declaration of function ‘request_region’
dxe201.c:405: error: dereferencing pointer to incomplete type
dxe201.c:407: error: dereferencing pointer to incomplete type
dxe201.c:408: error: dereferencing pointer to incomplete type
dxe201.c:410: error: dereferencing pointer to incomplete type
dxe201.c:411: warning: implicit declaration of function ‘memset’
dxe201.c:411: warning: incompatible implicit declaration of built-in function ‘memset’
dxe201.c:431: error: expected ‘)’ before string constant
dxe201.c:436: error: expected ‘)’ before string constant
dxe201.c:461: error: expected ‘)’ before string constant
dxe201.c:467: error: expected ‘)’ before string constant
dxe201.c:476: error: dereferencing pointer to incomplete type
dxe201.c:477: error: dereferencing pointer to incomplete type
dxe201.c:478: error: dereferencing pointer to incomplete type
dxe201.c:479: error: dereferencing pointer to incomplete type
dxe201.c:480: error: dereferencing pointer to incomplete type
dxe201.c:481: error: dereferencing pointer to incomplete type
dxe201.c: In function ‘read_eeprom’:
dxe201.c:522: warning: implicit declaration of function ‘inl’
dxe201.c:532: warning: implicit declaration of function ‘inb’
dxe201.c: In function ‘mdio_read’:
dxe201.c:575: error: dereferencing pointer to incomplete type
dxe201.c:582: warning: implicit declaration of function ‘inw’
dxe201.c:582: error: dereferencing pointer to incomplete type
dxe201.c: In function ‘mdio_write’:
dxe201.c:608: error: dereferencing pointer to incomplete type
dxe201.c:614: warning: implicit declaration of function ‘outw’
dxe201.c:614: error: dereferencing pointer to incomplete type
dxe201.c: In function ‘rtl8129_open’:
dxe201.c:640: error: dereferencing pointer to incomplete type
dxe201.c:641: error: dereferencing pointer to incomplete type
dxe201.c:647: error: ‘MOD_INC_USE_COUNT’ undeclared (first use in this function)
dxe201.c:648: warning: implicit declaration of function ‘request_irq’
dxe201.c:648: error: dereferencing pointer to incomplete type
dxe201.c:648: error: ‘SA_SHIRQ’ undeclared (first use in this function)
dxe201.c:648: error: dereferencing pointer to incomplete type
dxe201.c:649: error: ‘MOD_DEC_USE_COUNT’ undeclared (first use in this function)
dxe201.c:650: error: ‘EAGAIN’ undeclared (first use in this function)
dxe201.c:659: error: ‘GFP_KERNEL’ undeclared (first use in this function)
dxe201.c:659: warning: assignment makes pointer from integer without a cast
dxe201.c:662: error: ‘KERN_ERR’ undeclared (first use in this function)
dxe201.c:662: error: expected ‘)’ before string constant
dxe201.c:665: error: ‘ENOMEM’ undeclared (first use in this function)
dxe201.c:680: warning: implicit declaration of function ‘outl’
dxe201.c:680: error: ‘u32’ undeclared (first use in this function)
dxe201.c:680: error: expected expression before ‘)’ token
dxe201.c:680: error: dereferencing pointer to incomplete type
dxe201.c:681: error: expected expression before ‘)’ token
dxe201.c:681: error: dereferencing pointer to incomplete type
dxe201.c:690: error: ‘u16’ undeclared (first use in this function)
dxe201.c:690: error: expected ‘;’ before ‘mii_reg5’
dxe201.c:691: error: ‘mii_reg5’ undeclared (first use in this function)
dxe201.c:697: error: ‘KERN_INFO’ undeclared (first use in this function)
dxe201.c:697: error: expected ‘)’ before string constant
dxe201.c:708: warning: implicit declaration of function ‘virt_to_bus’
dxe201.c:716: error: dereferencing pointer to incomplete type
dxe201.c:717: error: dereferencing pointer to incomplete type
dxe201.c:718: error: dereferencing pointer to incomplete type
dxe201.c:725: error: ‘KERN_DEBUG’ undeclared (first use in this function)
dxe201.c:725: error: expected ‘)’ before string constant
dxe201.c:732: warning: implicit declaration of function ‘init_timer’
dxe201.c:733: error: ‘jiffies’ undeclared (first use in this function)
dxe201.c:733: error: ‘HZ’ undeclared (first use in this function)
dxe201.c:736: warning: implicit declaration of function ‘add_timer’
dxe201.c: In function ‘rtl_hw_start’:
dxe201.c:744: error: dereferencing pointer to incomplete type
dxe201.c:745: error: dereferencing pointer to incomplete type
dxe201.c:755: error: ‘u32’ undeclared (first use in this function)
dxe201.c:755: error: expected expression before ‘)’ token
dxe201.c:755: error: dereferencing pointer to incomplete type
dxe201.c:756: error: expected expression before ‘)’ token
dxe201.c:756: error: dereferencing pointer to incomplete type
dxe201.c: In function ‘rtl8129_timer’:
dxe201.c:788: error: dereferencing pointer to incomplete type
dxe201.c:789: error: dereferencing pointer to incomplete type
dxe201.c:790: error: ‘HZ’ undeclared (first use in this function)
dxe201.c:797: error: ‘KERN_INFO’ undeclared (first use in this function)
dxe201.c:797: error: expected ‘)’ before string constant
dxe201.c:808: error: dereferencing pointer to incomplete type
dxe201.c:809: error: ‘KERN_ERR’ undeclared (first use in this function)
dxe201.c:809: error: expected ‘)’ before string constant
dxe201.c:811: error: dereferencing pointer to incomplete type
dxe201.c:814: error: dereferencing pointer to incomplete type
dxe201.c:814: error: ‘jiffies’ undeclared (first use in this function)
dxe201.c:814: error: dereferencing pointer to incomplete type
dxe201.c:887: error: ‘KERN_DEBUG’ undeclared (first use in this function)
dxe201.c:887: error: expected ‘)’ before string constant
dxe201.c:890: error: expected ‘)’ before string constant
dxe201.c:892: error: expected ‘)’ before string constant
dxe201.c:896: error: expected ‘)’ before string constant
dxe201.c: In function ‘rtl8129_tx_timeout’:
dxe201.c:906: error: dereferencing pointer to incomplete type
dxe201.c:907: error: dereferencing pointer to incomplete type
dxe201.c:911: error: ‘KERN_ERR’ undeclared (first use in this function)
dxe201.c:911: error: expected ‘)’ before string constant
dxe201.c:919: error: ‘KERN_DEBUG’ undeclared (first use in this function)
dxe201.c:919: error: expected ‘)’ before string constant
dxe201.c:922: error: expected ‘)’ before string constant
dxe201.c:925: error: expected ‘)’ before string constant
dxe201.c:935: warning: implicit declaration of function ‘dev_kfree_skb’
dxe201.c:935: error: ‘FREE_WRITE’ undeclared (first use in this function)
dxe201.c:941: error: dereferencing pointer to incomplete type
dxe201.c: In function ‘rtl8129_init_ring’:
dxe201.c:950: error: dereferencing pointer to incomplete type
dxe201.c: In function ‘rtl8129_start_xmit’:
dxe201.c:966: error: dereferencing pointer to incomplete type
dxe201.c:967: error: dereferencing pointer to incomplete type
dxe201.c:972: warning: implicit declaration of function ‘set_bit’
dxe201.c:972: error: dereferencing pointer to incomplete type
dxe201.c:973: error: ‘jiffies’ undeclared (first use in this function)
dxe201.c:973: error: dereferencing pointer to incomplete type
dxe201.c:973: error: ‘HZ’ undeclared (first use in this function)
dxe201.c:982: error: dereferencing pointer to incomplete type
dxe201.c:983: warning: implicit declaration of function ‘memcpy’
dxe201.c:983: warning: incompatible implicit declaration of built-in function ‘memcpy’
dxe201.c:983: error: dereferencing pointer to incomplete type
dxe201.c:983: error: dereferencing pointer to incomplete type
dxe201.c:986: error: dereferencing pointer to incomplete type
dxe201.c:988: error: dereferencing pointer to incomplete type
dxe201.c:988: error: ‘ETH_ZLEN’ undeclared (first use in this function)
dxe201.c:988: error: dereferencing pointer to incomplete type
dxe201.c:995: warning: implicit declaration of function ‘clear_bit’
dxe201.c:995: error: dereferencing pointer to incomplete type
dxe201.c:999: error: dereferencing pointer to incomplete type
dxe201.c:1004: error: dereferencing pointer to incomplete type
dxe201.c:1006: error: ‘KERN_DEBUG’ undeclared (first use in this function)
dxe201.c:1006: error: expected ‘)’ before string constant
dxe201.c: At top level:
dxe201.c:1014: warning: ‘struct pt_regs’ declared inside parameter list
dxe201.c:1015: error: conflicting types for ‘rtl8129_interrupt’
dxe201.c:349: error: previous declaration of ‘rtl8129_interrupt’ was here
dxe201.c: In function ‘rtl8129_interrupt’:
dxe201.c:1017: error: dereferencing pointer to incomplete type
dxe201.c:1019: error: dereferencing pointer to incomplete type
dxe201.c:1024: error: dereferencing pointer to incomplete type
dxe201.c:1025: error: ‘KERN_ERR’ undeclared (first use in this function)
dxe201.c:1025: error: expected ‘)’ before string constant
dxe201.c:1027: error: dereferencing pointer to incomplete type
dxe201.c:1067: error: ‘KERN_DEBUG’ undeclared (first use in this function)
dxe201.c:1067: error: expected ‘)’ before string constant
dxe201.c:1091: error: ‘KERN_NOTICE’ undeclared (first use in this function)
dxe201.c:1091: error: expected ‘)’ before string constant
dxe201.c:1119: error: ‘FREE_WRITE’ undeclared (first use in this function)
dxe201.c:1121: warning: implicit declaration of function ‘test_bit’
dxe201.c:1124: error: dereferencing pointer to incomplete type
dxe201.c:1125: warning: implicit declaration of function ‘mark_bh’
dxe201.c:1125: error: ‘NET_BH’ undeclared (first use in this function)
dxe201.c:1132: error: expected ‘)’ before string constant
dxe201.c:1144: error: expected ‘)’ before string constant
dxe201.c:1178: error: ‘u32’ undeclared (first use in this function)
dxe201.c:1178: error: expected ‘;’ before ‘pci_cmd_status’
dxe201.c:1179: error: ‘PCI_COMMAND’ undeclared (first use in this function)
dxe201.c:1179: error: ‘pci_cmd_status’ undeclared (first use in this function)
dxe201.c:1181: error: expected ‘)’ before string constant
dxe201.c:1186: error: ‘KERN_WARNING’ undeclared (first use in this function)
dxe201.c:1186: error: expected ‘)’ before string constant
dxe201.c:1196: error: expected ‘)’ before string constant
dxe201.c:1200: error: dereferencing pointer to incomplete type
dxe201.c: In function ‘rtl8129_rx’:
dxe201.c:1211: error: dereferencing pointer to incomplete type
dxe201.c:1212: error: dereferencing pointer to incomplete type
dxe201.c:1214: error: ‘u16’ undeclared (first use in this function)
dxe201.c:1214: error: expected ‘;’ before ‘cur_rx’
dxe201.c:1217: error: ‘KERN_DEBUG’ undeclared (first use in this function)
dxe201.c:1217: error: expected ‘)’ before string constant
dxe201.c:1223: error: ‘cur_rx’ undeclared (first use in this function)
dxe201.c:1224: error: ‘u32’ undeclared (first use in this function)
dxe201.c:1224: error: expected ‘;’ before ‘rx_status’
dxe201.c:1225: error: ‘rx_status’ undeclared (first use in this function)
dxe201.c:1229: error: expected ‘)’ before string constant
dxe201.c:1232: error: expected ‘)’ before string constant
dxe201.c:1239: error: expected ‘)’ before string constant
dxe201.c:1243: error: ‘KERN_NOTICE’ undeclared (first use in this function)
dxe201.c:1243: error: expected ‘)’ before string constant
dxe201.c:1264: warning: implicit declaration of function ‘dev_alloc_skb’
dxe201.c:1264: warning: assignment makes pointer from integer without a cast
dxe201.c:1266: error: ‘KERN_WARNING’ undeclared (first use in this function)
dxe201.c:1266: error: expected ‘)’ before string constant
dxe201.c:1273: error: dereferencing pointer to incomplete type
dxe201.c:1274: warning: implicit declaration of function ‘skb_reserve’
dxe201.c:1278: warning: incompatible implicit declaration of built-in function ‘memcpy’
dxe201.c:1278: warning: implicit declaration of function ‘skb_put’
dxe201.c:1279: warning: passing argument 1 of ‘memcpy’ makes pointer from integer without a cast
dxe201.c:1281: warning: passing argument 1 of ‘memcpy’ makes pointer from integer without a cast
dxe201.c:1284: error: expected ‘)’ before string constant
dxe201.c:1289: warning: incompatible implicit declaration of built-in function ‘memset’
dxe201.c:1292: warning: implicit declaration of function ‘eth_copy_and_sum’
dxe201.c:1296: error: dereferencing pointer to incomplete type
dxe201.c:1296: warning: implicit declaration of function ‘eth_type_trans’
dxe201.c:1297: warning: implicit declaration of function ‘netif_rx’
dxe201.c:1308: error: expected ‘)’ before string constant
dxe201.c: In function ‘rtl8129_close’:
dxe201.c:1319: error: dereferencing pointer to incomplete type
dxe201.c:1320: error: dereferencing pointer to incomplete type
dxe201.c:1323: error: dereferencing pointer to incomplete type
dxe201.c:1324: error: dereferencing pointer to incomplete type
dxe201.c:1327: error: ‘KERN_DEBUG’ undeclared (first use in this function)
dxe201.c:1327: error: expected ‘)’ before string constant
dxe201.c:1340: warning: implicit declaration of function ‘del_timer’
dxe201.c:1342: warning: implicit declaration of function ‘free_irq’
dxe201.c:1342: error: dereferencing pointer to incomplete type
dxe201.c:1346: error: ‘FREE_WRITE’ undeclared (first use in this function)
dxe201.c:1349: warning: implicit declaration of function ‘kfree’
dxe201.c:1356: error: ‘MOD_DEC_USE_COUNT’ undeclared (first use in this function)
dxe201.c: At top level:
dxe201.c:1361: warning: ‘struct ifreq’ declared inside parameter list
dxe201.c:1362: error: conflicting types for ‘mii_ioctl’
dxe201.c:351: error: previous declaration of ‘mii_ioctl’ was here
dxe201.c: In function ‘mii_ioctl’:
dxe201.c:1363: error: dereferencing pointer to incomplete type
dxe201.c:1364: error: ‘u16’ undeclared (first use in this function)
dxe201.c:1364: error: ‘data’ undeclared (first use in this function)
dxe201.c:1364: error: expected expression before ‘)’ token
dxe201.c:1367: error: ‘SIOCDEVPRIVATE’ undeclared (first use in this function)
dxe201.c:1374: warning: implicit declaration of function ‘suser’
dxe201.c:1375: error: ‘EPERM’ undeclared (first use in this function)
dxe201.c:1379: error: ‘EOPNOTSUPP’ undeclared (first use in this function)
dxe201.c: In function ‘rtl8129_get_stats’:
dxe201.c:1386: error: dereferencing pointer to incomplete type
dxe201.c:1387: error: dereferencing pointer to incomplete type
dxe201.c:1389: error: dereferencing pointer to incomplete type
dxe201.c: At top level:
dxe201.c:1401: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ether_crc’
dxe201.c: In function ‘set_rx_mode’:
dxe201.c:1423: error: dereferencing pointer to incomplete type
dxe201.c:1424: error: dereferencing pointer to incomplete type
dxe201.c:1425: error: ‘u32’ undeclared (first use in this function)
dxe201.c:1425: error: expected ‘;’ before ‘mc_filter’
dxe201.c:1429: error: ‘KERN_DEBUG’ undeclared (first use in this function)
dxe201.c:1429: error: expected ‘)’ before string constant
dxe201.c:1433: error: dereferencing pointer to incomplete type
dxe201.c:1433: error: ‘IFF_PROMISC’ undeclared (first use in this function)
dxe201.c:1435: error: ‘KERN_NOTICE’ undeclared (first use in this function)
dxe201.c:1435: error: expected ‘)’ before string constant
dxe201.c:1437: error: ‘mc_filter’ undeclared (first use in this function)
dxe201.c:1438: error: dereferencing pointer to incomplete type
dxe201.c:1439: error: dereferencing pointer to incomplete type
dxe201.c:1439: error: ‘IFF_ALLMULTI’ undeclared (first use in this function)
dxe201.c:1447: error: dereferencing pointer to incomplete type
dxe201.c:1447: error: dereferencing pointer to incomplete type
dxe201.c:1448: error: dereferencing pointer to incomplete type
dxe201.c:1449: warning: implicit declaration of function ‘ether_crc’
dxe201.c:1449: error: ‘ETH_ALEN’ undeclared (first use in this function)
dxe201.c:1449: error: dereferencing pointer to incomplete type
dxe201.c: In function ‘rtl_pwr_event’:
dxe201.c:1462: error: dereferencing pointer to incomplete type
dxe201.c:1463: error: dereferencing pointer to incomplete type
dxe201.c:1466: error: dereferencing pointer to incomplete type
dxe201.c:1469: error: ‘MOD_INC_USE_COUNT’ undeclared (first use in this function)
dxe201.c:1484: error: dereferencing pointer to incomplete type
dxe201.c:1484: error: ‘IFF_UP’ undeclared (first use in this function)
dxe201.c:1485: warning: implicit declaration of function ‘dev_close’
dxe201.c:1486: error: dereferencing pointer to incomplete type
dxe201.c:1486: error: ‘IFF_RUNNING’ undeclared (first use in this function)
dxe201.c:1488: warning: implicit declaration of function ‘unregister_netdev’
dxe201.c:1489: warning: implicit declaration of function ‘release_region’
dxe201.c:1489: error: dereferencing pointer to incomplete type
dxe201.c:1494: error: dereferencing pointer to incomplete type
dxe201.c:1503: error: ‘MOD_DEC_USE_COUNT’ undeclared (first use in this function)
dxe201.c: In function ‘init_module’:
dxe201.c:1594: error: ‘KERN_INFO’ undeclared (first use in this function)
dxe201.c:1594: error: expected ‘)’ before string constant
dxe201.c: In function ‘cleanup_module’:
dxe201.c:1614: error: dereferencing pointer to incomplete type
dxe201.c:1616: error: dereferencing pointer to incomplete type
make: *** [dxe201.o] Error 1
seth@seth-laptop:~/Desktop/LINUX$ make all
make: *** No rule to make target `all'.  Stop.

---

### Post by starsky on 2007-07-14
hmm... try this

$ cd /usr/src;

$ sudo ln -s /usr/src/linux-headers-$(uname -r)/ linux

(this will give you with this output)
ln: creating symbolic link `linux' to `/usr/src/linux-headers-2.6.20-16-386/'

after that proceed again with the same method.
also could you attache your Makefile ? thanks

Post back :)

---

### Post by PNP on 2007-07-14
Hmm... same result.  No sense in posting the errors again.
It says I can't upload the file: Invalid File

Driver is available here:

[http://www.dynexproducts.com/t-drivers.aspx](http://www.dynexproducts.com/t-drivers.aspx)

---

### Post by starsky on 2007-07-15
that's a windows driver. I need the .tar.gz or .zip file instead that has the source in it.

---

### Post by PNP on 2007-07-15
This is in a txt file on the cd... but im not certain of the files to use and i dont know how to compile:

Linux driver for kernel 2.2.X



Installation on Linux:

----------------------

1. Compile the source code :



 ->Copy the source code DXE201 (Ver 1.11a above) to a directory

   and execute

   "gcc -DCARDBUS -DMODULE -D_KERNEL_ -Wall -Wstrict-prototypes -O6 -c 

   DXE201 -o DXE201.o -I/usr/src/linux/pcmcia-cs-3.0.9/include/

   pcmcia/"

   

   The directory "pcmcia-cs-3.0.9" stands for the card service version you 

   use. Please change it to the version on your system in order to include 

   proper .h file. The final file is DXE201.o



2. Copy driver :



 ->Copy the file "DXE201.o" to "/lib/modules/2.2.14-5.0/pcmcia"

 

   The directory "2.2.14-5.0" stands for the Linux kernel version you use.



3. Edit config:

 ->Add 5 lines to the file "/etc/pcmcia/config"

   

   #

   # Device driver definitions

   #

  

   device "DXE201"                                   (==>Add 1/5)

     class "network" module "cb_enabler", "DXE201"   (==>Add 2/5) 





   :

   :



   #

   # CardBus Cards

   #



   card "Dynex DX-E201 CardBus PC Card"                                      (==>Add 3/5)

     manfid 0x0149, 0x0000                           (==>Add 4/5)

     bind "DXE201"                                    (==>Add 5/5)



   

   The values 0x0149, 0x0000 are JEDEC ID and can be read by typing 

   "cardctl ident" on console with one card on socket.

	          



4. Edit linuxconf

 ->Type "linuxconf" and choose "Config"-->"Networking"-->"Client tasks"-->

   "Basic host information". Select an adapter, enable it, and type 

   "DXE201" on "Kernel module" and "eth0" (or eth1, eth2) on 

   "Net device". Click on "Accept" button and "Act/change" button.





5. Restart the computer.



6. More information about kernel compile:

   [http://metalab.unc.edu/mdw/HOWTO/Kernel-HOWTO.html](http://metalab.unc.edu/mdw/HOWTO/Kernel-HOWTO.html)

  

   More information about install: man pcmcia

---

### Post by starsky on 2007-07-15
try running just that -

```


gcc -DCARDBUS -DMODULE -D_KERNEL_ -Wall -Wstrict-prototypes -O6 -c

DXE201 -o DXE201.o -I/usr/src/linux/pcmcia-cs-3.0.9/include/

pcmcia


```

Also, if this doesn't work, move this thread to hardware forum where people who has used this card or knows about this card will be able to answer your question. 

Also, note that this driver was probably compiled under Linux 2.2 kernel which is like going back to dinosaure age. 
Insist your vendor to release a newer driver for linux 2.6 kernel.

Sorry couldn't help you much.

---

