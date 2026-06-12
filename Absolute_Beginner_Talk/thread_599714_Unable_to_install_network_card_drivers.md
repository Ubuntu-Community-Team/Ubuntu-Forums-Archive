---
title: "Unable to install network card drivers"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2007-11-01
I'm running Xubuntu 6.06 on a Fujitsu FMV-BIBLO MF3/45 laptop (450Mhz Celeron, 64MB RAM) and it doesn't come with a built-in ethernet port but luckily I have a spare PCMIA Netgear FA411.  I googled for drivers and found [these]("http://www.opendrivers.com/freedownload/228287/netgear-fa411-network-card-driver-3.0-windows-98-me-2000-xp-linux-download.html").

Luckily they included Linux drivers!  However when I couldn't config or make the drivers.  Here are the relevant files:
Config:
```

device "88790_cs"
   class "network" module "88790_cs"

card "NETGEAR FA411 PCMCIA Mobile Adapter"
  version "NETGEAR", "FA411"
  bind "88790_cs"

```

./config gives me:
line 2: device: command not found
line 3: class: command not found
line 5: card: command not found
line 6: version: command not found

Likewise, make gives me a whole slew of error messages as well.

---

### Post by haldean on 2007-11-01
The CONFIG file there isn't a script - it's just a text file read by the compiler to tell it what to do. You just need to go into the directory and run 
```
make
sudo make install
```

EDIT:

Sorry didn't see the last bit. Could you post the errors that you get when you run 'make'? Also, which version of the driver are you trying to compile? 7.0, 6.1 and 6.2 are all in the archive.

---

### Post by AncientPC on 2007-11-01
```
cc1: error: /usr/src/linux/pcmcia-cs-3.1.19/include/linux/modversions.h: No such file or directory
88790.c:51:26: error: linux/module.h: No such file or directory
88790.c:52:26: error: linux/kernel.h: No such file or directory
88790.c:53:25: error: linux/sched.h: No such file or directory
88790.c:54:22: error: linux/fs.h: No such file or directory
88790.c:55:25: error: linux/types.h: No such file or directory
88790.c:56:26: error: linux/ptrace.h: No such file or directory
88790.c:57:26: error: linux/string.h: No such file or directory
88790.c:58:24: error: asm/system.h: No such file or directory
88790.c:59:25: error: asm/uaccess.h: No such file or directory
88790.c:60:24: error: asm/bitops.h: No such file or directory
88790.c:61:20: error: asm/io.h: No such file or directory
88790.c:62:21: error: asm/irq.h: No such file or directory
88790.c:63:25: error: linux/delay.h: No such file or directory
88790.c:64:25: error: linux/errno.h: No such file or directory
88790.c:65:25: error: linux/fcntl.h: No such file or directory
88790.c:66:22: error: linux/in.h: No such file or directory
88790.c:67:29: error: linux/interrupt.h: No such file or directory
88790.c:68:24: error: linux/init.h: No such file or directory
88790.c:70:29: error: linux/netdevice.h: No such file or directory
88790.c:71:31: error: linux/etherdevice.h: No such file or directory
In file included from 88790.c:74:
88790.h:10:26: error: linux/config.h: No such file or directory
88790.h:11:28: error: linux/if_ether.h: No such file or directory
88790.h:12:26: error: linux/ioport.h: No such file or directory
88790.h:13:26: error: linux/skbuff.h: No such file or directory
In file included from 88790.c:74:
88790.h:146: warning: 'struct device' declared inside parameter list
88790.h:146: warning: its scope is only this definition or declaration, which is probably not what you want
88790.h:147: warning: 'struct device' declared inside parameter list
88790.h:148: warning: 'struct device' declared inside parameter list
88790.h:149: warning: 'struct device' declared inside parameter list
88790.h:150: warning: 'struct pt_regs' declared inside parameter list
88790.h:159: warning: 'struct device' declared inside parameter list
88790.h:160: warning: 'struct device' declared inside parameter list
88790.h:161: warning: 'struct device' declared inside parameter list
88790.h:162: warning: 'struct sk_buff' declared inside parameter list
88790.h:162: warning: 'struct device' declared inside parameter list
88790.h:178: error: field 'stat' has incomplete type
88790.h:179: error: expected specifier-qualifier-list before 'u32'
88790.c:107: warning: 'struct device' declared inside parameter list
88790.c:108: warning: 'struct device' declared inside parameter list
88790.c:109: warning: 'struct device' declared inside parameter list
88790.c:110: warning: 'struct device' declared inside parameter list
88790.c:114: warning: 'struct device' declared inside parameter list
88790.c:115: warning: 'struct device' declared inside parameter list
88790.c:116: warning: 'struct device' declared inside parameter list
88790.c:135: warning: 'struct device' declared inside parameter list
88790.c:142: warning: 'struct device' declared inside parameter list
88790.c:149: warning: 'struct device' declared inside parameter list
88790.c:153: warning: 'struct device' declared inside parameter list
88790.c:157: warning: 'struct device' declared inside parameter list
88790.c:161: warning: 'struct device' declared inside parameter list
88790.c:165: warning: 'struct device' declared inside parameter list
88790.c:203: warning: 'struct device' declared inside parameter list
88790.c:204: error: conflicting types for 'ei_open'
88790.h:148: error: previous declaration of 'ei_open' was here
88790.c: In function 'ei_open':
88790.c:206: error: dereferencing pointer to incomplete type
88790.c:209: error: 'NULL' undeclared (first use in this function)
88790.c:209: error: (Each undeclared identifier is reported only once
88790.c:209: error: for each function it appears in.)
88790.c:211: error: 'KERN_NOTICE' undeclared (first use in this function)
88790.c:211: error: expected ')' before string constant
88790.c:212: error: 'KERN_EMERG' undeclared (first use in this function)
88790.c:212: error: expected ')' before string constant
88790.c:213: error: 'ENXIO' undeclared (first use in this function)
88790.c:221: error: 'struct ei_device' has no member named 'page_lock'
88790.c:223: warning: passing argument 1 of 'AXSearchPhy' from incompatible pointer type
88790.c:227: warning: passing argument 1 of 'AXInitPhy' from incompatible pointer type
88790.c:230: error: 'struct ei_device' has no member named 'fgMediaLinkFail'
88790.c:232: warning: passing argument 1 of 'AXGetPhyCapability' from incompatible pointer type
88790.c:235: warning: passing argument 1 of 'NS8390_init' from incompatible pointer type
88790.c:239: error: 'KERN_INFO' undeclared (first use in this function)
88790.c:239: error: expected ')' before string constant
88790.c:240: error: dereferencing pointer to incomplete type
88790.c:241: error: 'struct ei_device' has no member named 'page_lock'
88790.c: At top level:
88790.c:247: warning: 'struct device' declared inside parameter list
88790.c:248: error: conflicting types for 'ei_close'
88790.h:149: error: previous declaration of 'ei_close' was here
88790.c: In function 'ei_close':
88790.c:249: error: dereferencing pointer to incomplete type
88790.c:256: error: 'struct ei_device' has no member named 'page_lock'
88790.c:257: warning: passing argument 1 of 'NS8390_init' from incompatible pointer type
88790.c:258: error: 'struct ei_device' has no member named 'page_lock'
88790.c:259: error: dereferencing pointer to incomplete type
88790.c: At top level:
88790.c:263: warning: 'struct device' declared inside parameter list
88790.c:263: warning: 'struct sk_buff' declared inside parameter list
88790.c: In function 'ei_start_xmit':
88790.c:265: error: dereferencing pointer to incomplete type
88790.c:266: error: dereferencing pointer to incomplete type
88790.c:277: error: dereferencing pointer to incomplete type
88790.c:281: error: 'jiffies' undeclared (first use in this function)
88790.c:281: error: dereferencing pointer to incomplete type
88790.c:288: error: 'struct ei_device' has no member named 'page_lock'
88790.c:290: error: 'HZ' undeclared (first use in this function)
88790.c:292: error: 'struct ei_device' has no member named 'page_lock'
88790.c:298: error: dereferencing pointer to incomplete type
88790.c:300: error: 'struct ei_device' has no member named 'page_lock'
88790.c:301: error: 'KERN_WARNING' undeclared (first use in this function)
88790.c:301: error: expected ')' before string constant
88790.c:311: error: 'KERN_DEBUG' undeclared (first use in this function)
88790.c:311: error: expected ')' before string constant
88790.c:326: error: 'struct ei_device' has no member named 'page_lock'
88790.c:330: error: dereferencing pointer to incomplete type
88790.c:331: error: 'struct ei_device' has no member named 'page_lock'
88790.c:334: warning: passing argument 1 of 'ei_local->reset_8390' from incompatible pointer type
88790.c:335: warning: passing argument 1 of 'NS8390_init' from incompatible pointer type
88790.c:337: error: 'struct ei_device' has no member named 'page_lock'
88790.c:338: error: dereferencing pointer to incomplete type
88790.c:339: error: dereferencing pointer to incomplete type
88790.c:342: error: dereferencing pointer to incomplete type
88790.c:349: error: 'struct ei_device' has no member named 'page_lock'
88790.c:351: error: 'struct ei_device' has no member named 'page_lock'
88790.c:358: error: dereferencing pointer to incomplete type
88790.c:360: error: 'struct ei_device' has no member named 'page_lock'
88790.c:362: error: dereferencing pointer to incomplete type
88790.c:364: error: expected ')' before string constant
88790.c:366: error: 'struct ei_device' has no member named 'page_lock'
88790.c:367: error: dereferencing pointer to incomplete type
88790.c:374: error: 'ETH_ZLEN' undeclared (first use in this function)
88790.c:391: error: expected ')' before string constant
88790.c:399: error: expected ')' before string constant
88790.c:405: error: expected ')' before string constant
88790.c:408: error: dereferencing pointer to incomplete type
88790.c:410: error: 'struct ei_device' has no member named 'page_lock'
88790.c:411: error: dereferencing pointer to incomplete type
88790.c:422: error: dereferencing pointer to incomplete type
88790.c:422: warning: passing argument 1 of 'ei_local->block_output' from incompatible pointer type
88790.c:426: warning: passing argument 1 of 'NS8390_trigger_send' from incompatible pointer type
88790.c:427: error: dereferencing pointer to incomplete type
88790.c:441: error: dereferencing pointer to incomplete type
88790.c:463: error: 'struct ei_device' has no member named 'page_lock'
88790.c:464: error: dereferencing pointer to incomplete type
88790.c: At top level:
88790.c:475: warning: 'struct pt_regs' declared inside parameter list
88790.c:476: error: conflicting types for 'ei_interrupt'
88790.h:150: error: previous declaration of 'ei_interrupt' was here
88790.c: In function 'ei_interrupt':
88790.c:483: error: 'NULL' undeclared (first use in this function)
88790.c:489: error: dereferencing pointer to incomplete type
88790.c:490: error: dereferencing pointer to incomplete type
88790.c:496: error: 'struct ei_device' has no member named 'page_lock'
88790.c:498: error: dereferencing pointer to incomplete type
88790.c:505: error: dereferencing pointer to incomplete type
88790.c:508: error: 'struct ei_device' has no member named 'page_lock'
88790.c:513: error: dereferencing pointer to incomplete type
88790.c:518: error: 'KERN_DEBUG' undeclared (first use in this function)
88790.c:518: error: expected ')' before string constant
88790.c:525: error: dereferencing pointer to incomplete type
88790.c:527: error: 'KERN_WARNING' undeclared (first use in this function)
88790.c:527: error: expected ')' before string constant
88790.c:538: warning: passing argument 1 of 'ei_rx_overrun' from incompatible pointer type
88790.c:542: warning: passing argument 1 of 'ei_receive' from incompatible pointer type
88790.c:546: warning: passing argument 1 of 'ei_tx_intr' from incompatible pointer type
88790.c:548: warning: passing argument 1 of 'ei_tx_err' from incompatible pointer type
88790.c:572: error: expected ')' before string constant
88790.c:576: error: expected ')' before string constant
88790.c:580: error: dereferencing pointer to incomplete type
88790.c:581: error: 'struct ei_device' has no member named 'page_lock'
88790.c: At top level:
88790.c:596: warning: 'struct device' declared inside parameter list
88790.c:597: error: conflicting types for 'ei_tx_err'
88790.c:108: error: previous declaration of 'ei_tx_err' was here
88790.c: In function 'ei_tx_err':
88790.c:598: error: dereferencing pointer to incomplete type
88790.c:599: error: dereferencing pointer to incomplete type
88790.c:621: warning: passing argument 1 of 'ei_tx_intr' from incompatible pointer type
88790.c: At top level:
88790.c:634: warning: 'struct device' declared inside parameter list
88790.c:635: error: conflicting types for 'ei_tx_intr'
88790.c:107: error: previous declaration of 'ei_tx_intr' was here
88790.c: In function 'ei_tx_intr':
88790.c:636: error: dereferencing pointer to incomplete type
88790.c:637: error: dereferencing pointer to incomplete type
88790.c:653: error: 'KERN_ERR' undeclared (first use in this function)
88790.c:653: error: expected ')' before string constant
88790.c:656: error: dereferencing pointer to incomplete type
88790.c:660: warning: passing argument 1 of 'NS8390_trigger_send' from incompatible pointer type
88790.c:661: error: dereferencing pointer to incomplete type
88790.c:661: error: 'jiffies' undeclared (first use in this function)
88790.c:673: error: dereferencing pointer to incomplete type
88790.c:677: warning: passing argument 1 of 'NS8390_trigger_send' from incompatible pointer type
88790.c:678: error: dereferencing pointer to incomplete type
88790.c:685: error: 'KERN_WARNING' undeclared (first use in this function)
88790.c:685: error: expected ')' before string constant
88790.c:718: error: 'NET_BH' undeclared (first use in this function)
88790.c: At top level:
88790.c:724: warning: 'struct device' declared inside parameter list
88790.c:725: error: conflicting types for 'ei_receive'
88790.c:109: error: previous declaration of 'ei_receive' was here
88790.c: In function 'ei_receive':
88790.c:726: error: dereferencing pointer to incomplete type
88790.c:727: error: dereferencing pointer to incomplete type
88790.c:751: error: 'KERN_ERR' undeclared (first use in this function)
88790.c:751: error: expected ')' before string constant
88790.c:758: warning: passing argument 1 of 'ei_local->get_8390_hdr' from incompatible pointer type
88790.c:781: error: 'KERN_DEBUG' undeclared (first use in this function)
88790.c:781: error: expected ')' before string constant
88790.c:791: warning: assignment makes pointer from integer without a cast
88790.c:792: error: 'NULL' undeclared (first use in this function)
88790.c:795: error: expected ')' before string constant
88790.c:803: error: dereferencing pointer to incomplete type
88790.c:805: warning: passing argument 1 of 'ei_local->block_input' from incompatible pointer type
88790.c:805: warning: passing argument 3 of 'ei_local->block_input' from incompatible pointer type
88790.c:806: error: dereferencing pointer to incomplete type
88790.c:817: error: expected ')' before string constant
88790.c:829: error: dereferencing pointer to incomplete type
88790.c: At top level:
88790.c:853: warning: 'struct device' declared inside parameter list
88790.c:854: error: conflicting types for 'ei_rx_overrun'
88790.c:110: error: previous declaration of 'ei_rx_overrun' was here
88790.c: In function 'ei_rx_overrun':
88790.c:855: error: dereferencing pointer to incomplete type
88790.c:857: error: dereferencing pointer to incomplete type
88790.c:867: error: 'KERN_DEBUG' undeclared (first use in this function)
88790.c:867: error: expected ')' before string constant
88790.c:907: warning: passing argument 1 of 'ei_receive' from incompatible pointer type
88790.c:913: error: 'struct ei_device' has no member named 'NicTransmitConfig'
88790.c: At top level:
88790.c:922: warning: 'struct device' declared inside parameter list
88790.c: In function 'get_stats':
88790.c:924: error: dereferencing pointer to incomplete type
88790.c:925: error: dereferencing pointer to incomplete type
88790.c:929: error: dereferencing pointer to incomplete type
88790.c:932: error: 'struct ei_device' has no member named 'page_lock'
88790.c:937: error: 'struct ei_device' has no member named 'page_lock'
88790.c: At top level:
88790.c:946: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'update_crc'
88790.c:968: error: expected ')' before '*' token
88790.c:997: warning: 'struct device' declared inside parameter list
88790.c:998: error: conflicting types for 'do_set_multicast_list'
88790.c:116: error: previous declaration of 'do_set_multicast_list' was here
88790.c: In function 'do_set_multicast_list':
88790.c:999: error: dereferencing pointer to incomplete type
88790.c:1001: error: dereferencing pointer to incomplete type
88790.c:1003: error: dereferencing pointer to incomplete type
88790.c:1003: error: 'IFF_PROMISC' undeclared (first use in this function)
88790.c:1003: error: 'IFF_ALLMULTI' undeclared (first use in this function)
88790.c:1005: warning: incompatible implicit declaration of built-in function 'memset'
88790.c:1006: error: dereferencing pointer to incomplete type
88790.c:1010: warning: incompatible implicit declaration of built-in function 'memset'
88790.c:1025: error: dereferencing pointer to incomplete type
88790.c:1038: error: dereferencing pointer to incomplete type
88790.c:1040: error: dereferencing pointer to incomplete type
88790.c:1040: error: dereferencing pointer to incomplete type
88790.c: At top level:
88790.c:1052: warning: 'struct device' declared inside parameter list
88790.c:1053: error: conflicting types for 'set_multicast_list'
88790.c:115: error: previous declaration of 'set_multicast_list' was here
88790.c: In function 'set_multicast_list':
88790.c:1055: error: dereferencing pointer to incomplete type
88790.c:1057: error: 'struct ei_device' has no member named 'page_lock'
88790.c:1058: warning: passing argument 1 of 'do_set_multicast_list' from incompatible pointer type
88790.c:1059: error: 'struct ei_device' has no member named 'page_lock'
88790.c: At top level:
88790.c:1067: warning: 'struct device' declared inside parameter list
88790.c:1068: error: conflicting types for 'ethdev_init'
88790.h:146: error: previous declaration of 'ethdev_init' was here
88790.c: In function 'ethdev_init':
88790.c:1070: error: 'KERN_INFO' undeclared (first use in this function)
88790.c:1070: error: expected ')' before string constant
88790.c:1072: error: dereferencing pointer to incomplete type
88790.c:1072: error: 'NULL' undeclared (first use in this function)
88790.c:1076: error: dereferencing pointer to incomplete type
88790.c:1076: error: 'GFP_KERNEL' undeclared (first use in this function)
88790.c:1077: error: dereferencing pointer to incomplete type
88790.c:1078: error: 'ENOMEM' undeclared (first use in this function)
88790.c:1079: warning: incompatible implicit declaration of built-in function 'memset'
88790.c:1079: error: dereferencing pointer to incomplete type
88790.c:1080: error: dereferencing pointer to incomplete type
88790.c:1081: error: 'struct ei_device' has no member named 'page_lock'
88790.c:1084: error: dereferencing pointer to incomplete type
88790.c:1085: error: dereferencing pointer to incomplete type
88790.c:1086: error: dereferencing pointer to incomplete type
88790.c: At top level:
88790.c:1102: warning: 'struct device' declared inside parameter list
88790.c:1103: error: conflicting types for 'NS8390_init'
88790.h:147: error: previous declaration of 'NS8390_init' was here
88790.c: In function 'NS8390_init':
88790.c:1104: error: dereferencing pointer to incomplete type
88790.c:1105: error: dereferencing pointer to incomplete type
88790.c:1136: error: dereferencing pointer to incomplete type
88790.c:1137: error: dereferencing pointer to incomplete type
88790.c:1138: error: 'KERN_ERR' undeclared (first use in this function)
88790.c:1138: error: expected ')' before string constant
88790.c:1144: error: dereferencing pointer to incomplete type
88790.c:1145: error: dereferencing pointer to incomplete type
88790.c:1154: error: 'struct ei_device' has no member named 'NicTransmitConfig'
88790.c:1157: warning: passing argument 1 of 'do_set_multicast_list' from incompatible pointer type
88790.c: At top level:
88790.c:1166: warning: 'struct device' declared inside parameter list
88790.c:1167: error: conflicting types for 'NS8390_trigger_send'
88790.c:114: error: previous declaration of 'NS8390_trigger_send' was here
88790.c: In function 'NS8390_trigger_send':
88790.c:1168: error: dereferencing pointer to incomplete type
88790.c:1169: error: dereferencing pointer to incomplete type
88790.c:1175: error: 'KERN_WARNING' undeclared (first use in this function)
88790.c:1175: error: expected ')' before string constant
88790.c: At top level:
88790.c:1274: warning: 'struct device' declared inside parameter list
88790.c:1275: error: conflicting types for 'A19xWriteMii'
88790.c:135: error: previous declaration of 'A19xWriteMii' was here
88790.c: In function 'A19xWriteMii':
88790.c:1281: error: dereferencing pointer to incomplete type
88790.c:1282: error: dereferencing pointer to incomplete type
88790.c: At top level:
88790.c:1332: warning: 'struct device' declared inside parameter list
88790.c:1333: error: conflicting types for 'MiiReadRegister'
88790.c:142: error: previous declaration of 'MiiReadRegister' was here
88790.c: In function 'MiiReadRegister':
88790.c:1343: warning: passing argument 1 of 'A19xWriteMii' from incompatible pointer type
88790.c:1344: warning: passing argument 1 of 'A19xWriteMii' from incompatible pointer type
88790.c:1345: warning: passing argument 1 of 'A19xWriteMii' from incompatible pointer type
88790.c:1346: error: dereferencing pointer to incomplete type
88790.c:1346: error: dereferencing pointer to incomplete type
88790.c:1348: error: dereferencing pointer to incomplete type
88790.c:1353: error: dereferencing pointer to incomplete type
88790.c:1353: error: dereferencing pointer to incomplete type
88790.c:1354: error: dereferencing pointer to incomplete type
88790.c:1360: error: dereferencing pointer to incomplete type
88790.c:1361: error: dereferencing pointer to incomplete type
88790.c:1363: error: dereferencing pointer to incomplete type
88790.c:1366: error: dereferencing pointer to incomplete type
88790.c:1366: error: dereferencing pointer to incomplete type
88790.c: At top level:
88790.c:1382: warning: 'struct device' declared inside parameter list
88790.c:1383: error: conflicting types for 'MiiWriteRegister'
88790.c:149: error: previous declaration of 'MiiWriteRegister' was here
88790.c: In function 'MiiWriteRegister':
88790.c:1390: warning: passing argument 1 of 'A19xWriteMii' from incompatible pointer type
88790.c:1391: warning: passing argument 1 of 'A19xWriteMii' from incompatible pointer type
88790.c:1392: warning: passing argument 1 of 'A19xWriteMii' from incompatible pointer type
88790.c:1393: error: dereferencing pointer to incomplete type
88790.c:1393: error: dereferencing pointer to incomplete type
88790.c: At top level:
88790.c:1458: warning: 'struct device' declared inside parameter list
88790.c:1459: error: conflicting types for 'AXSearchPhy'
88790.c:153: error: previous declaration of 'AXSearchPhy' was here
88790.c: In function 'AXSearchPhy':
88790.c:1460: error: dereferencing pointer to incomplete type
88790.c:1475: warning: passing argument 1 of 'MiiReadRegister' from incompatible pointer type
88790.c:1480: warning: passing argument 1 of 'MiiReadRegister' from incompatible pointer type
88790.c:1487: error: 'struct ei_device' has no member named 'uPhyAddr'
88790.c:1494: warning: passing argument 1 of 'MiiReadRegister' from incompatible pointer type
88790.c:1500: warning: passing argument 1 of 'MiiReadRegister' from incompatible pointer type
88790.c:1501: error: 'struct ei_device' has no member named 'ulPhyId'
88790.c: At top level:
88790.c:1512: warning: 'struct device' declared inside parameter list
88790.c:1513: error: conflicting types for 'AXInitPhy'
88790.c:157: error: previous declaration of 'AXInitPhy' was here
88790.c: In function 'AXInitPhy':
88790.c:1514: error: dereferencing pointer to incomplete type
88790.c:1516: error: 'struct ei_device' has no member named 'uPhyAddr'
88790.c:1524: warning: passing argument 1 of 'MiiWriteRegister' from incompatible pointer type
88790.c:1533: warning: passing argument 1 of 'MiiReadRegister' from incompatible pointer type
88790.c:1536: error: 'struct ei_device' has no member named 'uForcedConnectionType'
88790.c:1537: error: 'struct ei_device' has no member named 'uForcedConnectionType'
88790.c:1544: error: 'struct ei_device' has no member named 'NicTransmitConfig'
88790.c:1551: error: 'struct ei_device' has no member named 'NicTransmitConfig'
88790.c:1554: error: 'struct ei_device' has no member named 'uForcedConnectionType'
88790.c:1557: error: 'struct ei_device' has no member named 'uConnectionType'
88790.c:1557: error: 'struct ei_device' has no member named 'uForcedConnectionType'
88790.c:1558: error: 'struct ei_device' has no member named 'uConnectionType'
88790.c:1565: warning: passing argument 1 of 'MiiWriteRegister' from incompatible pointer type
88790.c:1581: warning: passing argument 1 of 'MiiWriteRegister' from incompatible pointer type
88790.c:1589: warning: passing argument 1 of 'MiiReadRegister' from incompatible pointer type
88790.c:1591: error: 'KERN_INFO' undeclared (first use in this function)
88790.c:1591: error: expected ')' before string constant
88790.c: At top level:
88790.c:1658: warning: 'struct device' declared inside parameter list
88790.c:1659: error: conflicting types for 'MediaModeChanged'
88790.c:161: error: previous declaration of 'MediaModeChanged' was here
88790.c: In function 'MediaModeChanged':
88790.c:1660: error: dereferencing pointer to incomplete type
88790.c:1664: error: 'KERN_INFO' undeclared (first use in this function)
88790.c:1664: error: expected ')' before string constant
88790.c:1665: error: expected ')' before string constant
88790.c:1666: error: 'struct ei_device' has no member named 'ulPhyId'
88790.c:1670: error: expected ')' before string constant
88790.c:1671: error: 'struct ei_device' has no member named 'uPhyAddr'
88790.c:1671: warning: passing argument 1 of 'MiiReadRegister' from incompatible pointer type
88790.c:1690: error: expected ')' before string constant
88790.c:1691: error: 'struct ei_device' has no member named 'uPhyAddr'
88790.c:1691: warning: passing argument 1 of 'MiiReadRegister' from incompatible pointer type
88790.c:1704: error: expected ')' before string constant
88790.c:1710: error: 'struct ei_device' has no member named 'uPhyAddr'
88790.c:1713: warning: passing argument 1 of 'MiiReadRegister' from incompatible pointer type
88790.c:1716: error: 'struct ei_device' has no member named 'uPhyAddr'
88790.c:1719: warning: passing argument 1 of 'MiiReadRegister' from incompatible pointer type
88790.c:1720: error: expected ')' before string constant
88790.c:1721: error: expected ')' before string constant
88790.c:1723: error: expected ')' before string constant
88790.c:1729: error: 'struct ei_device' has no member named 'ulPhyId'
88790.c:1734: error: 'struct ei_device' has no member named 'uPhyAddr'
88790.c:1734: warning: passing argument 1 of 'MiiReadRegister' from incompatible pointer type
88790.c:1741: error: 'struct ei_device' has no member named 'uPhyAddr'
88790.c:1741: warning: passing argument 1 of 'MiiReadRegister' from incompatible pointer type
88790.c:1748: error: 'struct ei_device' has no member named 'uPhyAddr'
88790.c:1748: warning: passing argument 1 of 'MiiReadRegister' from incompatible pointer type
88790.c:1761: error: 'struct ei_device' has no member named 'uPhyAddr'
88790.c:1761: warning: passing argument 1 of 'MiiReadRegister' from incompatible pointer type
88790.c:1769: error: 'struct ei_device' has no member named 'uPhyAddr'
88790.c:1769: warning: passing argument 1 of 'MiiReadRegister' from incompatible pointer type
88790.c:1771: error: 'struct ei_device' has no member named 'uPhyAddr'
88790.c:1771: warning: passing argument 1 of 'MiiReadRegister' from incompatible pointer type
88790.c:1783: error: 'struct ei_device' has no member named 'uConnectionMode'
88790.c:1785: error: 'struct ei_device' has no member named 'uConnectionMode'
88790.c:1789: error: expected ')' before string constant
88790.c:1790: error: 'struct ei_device' has no member named 'NicTransmitConfig'
88790.c:1793: error: expected ')' before string constant
88790.c:1794: error: 'struct ei_device' has no member named 'NicTransmitConfig'
88790.c: At top level:
88790.c:1803: warning: 'struct device' declared inside parameter list
88790.c:1804: error: conflicting types for 'AXGetPhyCapability'
88790.c:165: error: previous declaration of 'AXGetPhyCapability' was here
88790.c: In function 'AXGetPhyCapability':
88790.c:1805: error: dereferencing pointer to incomplete type
88790.c:1812: error: 'struct ei_device' has no member named 'fgWorkBusy'
88790.c:1814: error: 'struct ei_device' has no member named 'fgWorkBusy'
88790.c:1820: error: 'struct ei_device' has no member named 'uPhyAddr'
88790.c:1823: warning: passing argument 1 of 'MiiReadRegister' from incompatible pointer type
88790.c:1827: error: 'struct ei_device' has no member named 'uPhyAddr'
88790.c:1830: warning: passing argument 1 of 'MiiReadRegister' from incompatible pointer type
88790.c:1837: error: 'struct ei_device' has no member named 'fgMediaLinkFail'
88790.c:1839: error: 'struct ei_device' has no member named 'fgMediaLinkFail'
88790.c:1849: error: 'struct ei_device' has no member named 'uForcedConnectionType'
88790.c:1852: warning: passing argument 1 of 'MediaModeChanged' from incompatible pointer type
make: *** [88790.o] Error 1

```

---

### Post by haldean on 2007-11-01
Ah. I *think* that means you need to install your linux source package for that to compile. Run
```
uname -a
```and look for this bit:
```
Linux mater **2.6.22**-14-386 #1 Sun Oct 14 22:36:54 GMT 2007 i686 GNU/Linux
```(numbers might be different for you)
Then run:
```
sudo apt-get install linux-source-<numbers-from-above>
```replacing <numbers-from-above> with the numbers from uname. After a very long download (~45 MB) do the following:
```
cd /usr/src
sudo tar -xjvf linux-source-<numbers-from-above>* (this will take a long time!)
sudo ln -s linux-source-<numbers-from-above> linux

```then try again!

---

