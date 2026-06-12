---
title: "automount problems"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by brandon moore on 2006-03-29
hi everyone, i've been using ubuntu since january and have enjoyed my experience thus far.  the board here is great and i've found some very useful info!  today, though, i ran into a problem i can't seem to get around.

ubuntu will randomly automount my usb devices... i have an 80 GB usb drive in 2 partitions, a DVD-Writer, a USB key, and a USB printer.  only the printer works consistently.

here's my fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /documents      vfat    defaults,user,umask=000        0       0
/dev/hda1       /media/windows     ntfs    defaults,user        0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


here's dmesg with the hard drive and dvd-writer plugged in:

> brandon@brandon:~$ dmesg
67000] cs: IO port probe 0xc00-0xcf7: clean.
[4294728.068000] cs: IO port probe 0xa00-0xaff: clean.
[4294728.068000] cs: IO port probe 0xa00-0xaff: clean.
[4294729.057000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
[4294733.679000] ieee80211_crypt: registered algorithm 'WEP'
[4294751.606000] NET: Registered protocol family 10
[4294751.607000] Disabled Privacy Extensions on device c02eb280(lo)
[4294751.607000] IPv6 over IPv4 tunneling driver
[4294762.256000] eth1: no IPv6 routers present
[4294807.550000] usb 4-4: new high speed USB device using ehci_hcd and address 4[4294809.800000] usb 4-4: new high speed USB device using ehci_hcd and address 13
[4294811.050000] usb 4-4: new high speed USB device using ehci_hcd and address 18
[4294816.050000] usb 4-4: new high speed USB device using ehci_hcd and address 38
[4294816.112000] usb 4-4: device descriptor read/64, error -71
[4294816.275000] usb 4-4: device descriptor read/64, error -71
[4294816.438000] usb 4-4: new high speed USB device using ehci_hcd and address 39
[4294816.500000] usb 4-4: device descriptor read/64, error -71
[4294818.050000] usb 4-4: new high speed USB device using ehci_hcd and address 44
[4294821.300000] usb 4-4: new high speed USB device using ehci_hcd and address 57
[4294822.812000] usb 4-4: new high speed USB device using ehci_hcd and address 63
[4294823.300000] usb 4-4: new high speed USB device using ehci_hcd and address 65
[4294823.800000] usb 4-4: new high speed USB device using ehci_hcd and address 67
[4294836.300000] usb 4-4: new high speed USB device using ehci_hcd and address 117
[4294837.050000] usb 4-4: new high speed USB device using ehci_hcd and address 120
[4294839.300000] usb 4-4: new high speed USB device using ehci_hcd and address 3[4294840.300000] usb 4-4: new high speed USB device using ehci_hcd and address 7[4294843.550000] usb 4-4: new high speed USB device using ehci_hcd and address 20
[4294843.612000] usb 4-4: device descriptor read/64, error -71
[4294847.560000] usb 4-4: new high speed USB device using ehci_hcd and address 35
[4294851.300000] usb 4-4: new high speed USB device using ehci_hcd and address 50
[4294858.550000] usb 4-4: new high speed USB device using ehci_hcd and address 79
[4294859.550000] usb 4-4: new high speed USB device using ehci_hcd and address 83
[4294861.050000] usb 4-4: new high speed USB device using ehci_hcd and address 89
[4294864.550000] usb 4-4: new high speed USB device using ehci_hcd and address 103
[4294865.550000] usb 4-4: new high speed USB device using ehci_hcd and address 107
[4294867.050000] usb 4-4: new high speed USB device using ehci_hcd and address 113
[4294870.300000] usb 4-4: new high speed USB device using ehci_hcd and address 126
[4294881.300000] usb 4-4: new high speed USB device using ehci_hcd and address 6[4294884.550000] usb 4-4: new high speed USB device using ehci_hcd and address 19
[4294891.050000] usb 4-4: new high speed USB device using ehci_hcd and address 45
[4294892.050000] usb 4-4: new high speed USB device using ehci_hcd and address 49
[4294892.300000] usb 4-4: new high speed USB device using ehci_hcd and address 50
[4294893.550000] usb 4-4: new high speed USB device using ehci_hcd and address 55
[4294895.050000] usb 4-4: new high speed USB device using ehci_hcd and address 61
[4294899.304000] usb 4-4: new high speed USB device using ehci_hcd and address 78
[4294902.550000] usb 4-4: new high speed USB device using ehci_hcd and address 91
[4294902.800000] usb 4-4: new high speed USB device using ehci_hcd and address 92
[4294904.300000] usb 4-4: new high speed USB device using ehci_hcd and address 98
[4294905.050000] usb 4-4: new high speed USB device using ehci_hcd and address 101
[4294906.550000] usb 4-4: new high speed USB device using ehci_hcd and address 107
[4294907.300000] usb 4-4: new high speed USB device using ehci_hcd and address 110
[4294908.050000] usb 4-4: new high speed USB device using ehci_hcd and address 113
[4294908.550000] usb 4-4: new high speed USB device using ehci_hcd and address 115
[4294913.801000] usb 4-4: new high speed USB device using ehci_hcd and address 10
[4294913.863000] usb 4-4: device descriptor read/64, error -71
[4294916.050000] usb 4-4: new high speed USB device using ehci_hcd and address 18
[4294916.553000] usb 4-4: new high speed USB device using ehci_hcd and address 20
[4294916.800000] usb 4-4: new high speed USB device using ehci_hcd and address 21
[4294927.300000] usb 4-4: new high speed USB device using ehci_hcd and address 63
[4294929.555000] usb 4-4: new high speed USB device using ehci_hcd and address 72
[4294936.300000] usb 4-4: new high speed USB device using ehci_hcd and address 99
[4294938.550000] usb 4-4: new high speed USB device using ehci_hcd and address 108
[4294941.300000] usb 4-4: new high speed USB device using ehci_hcd and address 119
[4294944.050000] usb 4-4: new high speed USB device using ehci_hcd and address 4[4294944.559000] usb 4-4: new high speed USB device using ehci_hcd and address 6[4294947.300000] usb 4-4: new high speed USB device using ehci_hcd and address 17
[4294947.803000] usb 4-4: new high speed USB device using ehci_hcd and address 19
[4294951.800000] usb 4-4: new high speed USB device using ehci_hcd and address 35
[4294957.301000] usb 4-4: new high speed USB device using ehci_hcd and address 57
[4294961.550000] usb 4-4: new high speed USB device using ehci_hcd and address 74
[4294962.808000] usb 4-4: new high speed USB device using ehci_hcd and address 79
[4294965.050000] usb 4-4: new high speed USB device using ehci_hcd and address 88
[4294965.800000] usb 4-4: new high speed USB device using ehci_hcd and address 91
[4294973.050000] usb 4-4: new high speed USB device using ehci_hcd and address 110
[4294973.800000] usb 4-4: new high speed USB device using ehci_hcd and address 113
[4294975.550000] usb 4-4: new high speed USB device using ehci_hcd and address 120
[4294978.058000] usb 4-4: new high speed USB device using ehci_hcd and address 4[4294980.300000] usb 4-4: new high speed USB device using ehci_hcd and address 13
[4294987.550000] usb 4-4: new high speed USB device using ehci_hcd and address 42
[4294999.800000] usb 4-4: new high speed USB device using ehci_hcd and address 75
[4294999.880000] usb 4-4: device descriptor read/64, error -71
[4295003.310000] usb 4-4: new high speed USB device using ehci_hcd and address 88
[4295004.800000] usb 4-4: new high speed USB device using ehci_hcd and address 94
[4295006.311000] usb 4-4: new high speed USB device using ehci_hcd and address 100
[4295012.300000] usb 4-4: new high speed USB device using ehci_hcd and address 124
[4295019.438000] usb 2-2: new full speed USB device using uhci_hcd and address 2[4295019.867000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x413C pid 0x5008
[4295019.869000] usbcore: registered new driver usblp
[4295019.869000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[4295028.022000] usb 2-2: USB disconnect, address 2
[4295028.024000] drivers/usb/class/usblp.c: usblp0: removed
[4295031.550000] usb 4-4: new high speed USB device using ehci_hcd and address 24
[4295034.800000] usb 4-4: new high speed USB device using ehci_hcd and address 37
[4295040.550000] usb 4-4: new high speed USB device using ehci_hcd and address 60
[4295042.550000] usb 4-4: new high speed USB device using ehci_hcd and address 68
[4295044.050000] usb 4-4: new high speed USB device using ehci_hcd and address 74
[4295044.550000] usb 4-4: new high speed USB device using ehci_hcd and address 76
[4295049.860000] usb 4-3: new high speed USB device using ehci_hcd and address 104
[4295051.050000] usb 4-3: new high speed USB device using ehci_hcd and address 109
[4295052.800000] usb 4-3: new high speed USB device using ehci_hcd and address 116
[4295053.550000] usb 4-3: new high speed USB device using ehci_hcd and address 119
[4295055.050000] usb 4-3: new high speed USB device using ehci_hcd and address 125
[4295055.800000] usb 4-3: new high speed USB device using ehci_hcd and address 2[4295057.800000] usb 4-3: new high speed USB device using ehci_hcd and address 10
[4295058.550000] usb 4-3: new high speed USB device using ehci_hcd and address 13
[4295059.550000] usb 4-3: new high speed USB device using ehci_hcd and address 17
[4295062.300000] usb 4-3: new high speed USB device using ehci_hcd and address 28
[4295062.362000] usb 4-3: device descriptor read/64, error -71
[4295065.300000] usb 4-3: new high speed USB device using ehci_hcd and address 39
[4295069.300000] usb 4-3: new high speed USB device using ehci_hcd and address 55
[4295069.362000] usb 4-3: device descriptor read/64, error -71
[4295089.300000] usb 4-3: new high speed USB device using ehci_hcd and address 8[4295093.300000] usb 4-3: new high speed USB device using ehci_hcd and address 24
[4295094.050000] usb 4-3: new high speed USB device using ehci_hcd and address 27
[4295094.550000] usb 4-3: new high speed USB device using ehci_hcd and address 29
[4295097.300000] usb 4-3: new high speed USB device using ehci_hcd and address 40
[4295097.550000] usb 4-3: new high speed USB device using ehci_hcd and address 41
[4295098.300000] usb 4-3: new high speed USB device using ehci_hcd and address 44
[4295104.050000] usb 4-3: new high speed USB device using ehci_hcd and address 67
[4295104.800000] usb 4-3: new high speed USB device using ehci_hcd and address 70
[4295109.300000] usb 4-3: new high speed USB device using ehci_hcd and address 88
[4295111.050000] usb 4-3: new high speed USB device using ehci_hcd and address 95
[4295111.112000] usb 4-3: device descriptor read/64, error -71
[4295113.052000] usb 4-3: new high speed USB device using ehci_hcd and address 102
[4295114.550000] usb 4-3: new high speed USB device using ehci_hcd and address 108
[4295115.300000] usb 4-3: new high speed USB device using ehci_hcd and address 111
[4295115.800000] usb 4-3: new high speed USB device using ehci_hcd and address 113
[4295115.862000] usb 4-3: device descriptor read/64, error -71
[4295120.050000] usb 4-3: new high speed USB device using ehci_hcd and address 3[4295122.550000] usb 4-3: new high speed USB device using ehci_hcd and address 13
[4295124.550000] usb 4-3: new high speed USB device using ehci_hcd and address 21
[4295125.550000] usb 4-3: new high speed USB device using ehci_hcd and address 25
[4295127.302000] usb 4-3: new high speed USB device using ehci_hcd and address 32
[4295132.300000] usb 4-3: new high speed USB device using ehci_hcd and address 52
[4295136.300000] usb 4-3: new high speed USB device using ehci_hcd and address 68
[4295144.300000] usb 4-3: new high speed USB device using ehci_hcd and address 100
[4295147.050000] usb 4-3: new high speed USB device using ehci_hcd and address 111
[4295147.801000] usb 4-3: new high speed USB device using ehci_hcd and address 114
[4295149.550000] usb 4-3: new high speed USB device using ehci_hcd and address 121
[4295149.800000] usb 4-3: new high speed USB device using ehci_hcd and address 122
[4295151.050000] usb 4-3: new high speed USB device using ehci_hcd and address 127
[4295154.800000] usb 4-3: new high speed USB device using ehci_hcd and address 16
[4295156.050000] usb 4-3: new high speed USB device using ehci_hcd and address 21
[4295165.050000] usb 4-3: new high speed USB device using ehci_hcd and address 57
[4295170.550000] usb 4-3: new high speed USB device using ehci_hcd and address 79
[4295172.050000] usb 4-3: new high speed USB device using ehci_hcd and address 85
[4295173.800000] usb 4-3: new high speed USB device using ehci_hcd and address 92
[4295175.300000] usb 4-3: new high speed USB device using ehci_hcd and address 98
[4295177.800000] usb 4-3: new high speed USB device using ehci_hcd and address 108
[4295183.300000] usb 4-3: new high speed USB device using ehci_hcd and address 4[4295188.050000] usb 4-3: new high speed USB device using ehci_hcd and address 23
[4295196.301000] usb 4-3: new high speed USB device using ehci_hcd and address 56
[4295199.805000] usb 4-3: new high speed USB device using ehci_hcd and address 70
[4295200.050000] usb 4-3: new high speed USB device using ehci_hcd and address 71
[4295207.800000] usb 4-3: new high speed USB device using ehci_hcd and address 102
[4295210.550000] usb 4-3: new high speed USB device using ehci_hcd and address 113
[4295217.550000] usb 4-3: new high speed USB device using ehci_hcd and address 15
[4295220.804000] usb 4-3: new high speed USB device using ehci_hcd and address 28
[4295221.052000] usb 4-3: new high speed USB device using ehci_hcd and address 29
[4295227.550000] usb 4-3: new high speed USB device using ehci_hcd and address 55
[4295228.550000] usb 4-3: new high speed USB device using ehci_hcd and address 59
[4295229.050000] usb 4-3: new high speed USB device using ehci_hcd and address 61
[4295229.300000] usb 4-3: new high speed USB device using ehci_hcd and address 62
[4295229.362000] usb 4-3: device descriptor read/64, error -71
[4295230.300000] usb 4-3: new high speed USB device using ehci_hcd and address 65
[4295231.550000] usb 4-3: new high speed USB device using ehci_hcd and address 70
[4295234.300000] usb 4-3: new high speed USB device using ehci_hcd and address 81
[4295235.550000] usb 4-3: new high speed USB device using ehci_hcd and address 86
[4295238.881000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295238.881000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295239.053000] usb 4-3: new high speed USB device using ehci_hcd and address 100
[4295240.115000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295240.115000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295240.550000] usb 4-3: new high speed USB device using ehci_hcd and address 106
[4295240.612000] usb 4-3: device descriptor read/64, error -71
[4295241.804000] usb 4-3: new high speed USB device using ehci_hcd and address 110
[4295243.300000] usb 4-3: new high speed USB device using ehci_hcd and address 116
[4295245.550000] usb 4-3: new high speed USB device using ehci_hcd and address 125
[4295250.800000] usb 4-3: new high speed USB device using ehci_hcd and address 7[4295252.860000] usb 4-3: new high speed USB device using ehci_hcd and address 19
[4295253.800000] usb 4-3: new high speed USB device using ehci_hcd and address 24
[4295255.050000] usb 4-3: new high speed USB device using ehci_hcd and address 31
[4295255.112000] usb 4-3: device descriptor read/64, error -71
[4295256.610000] usb 4-3: new high speed USB device using ehci_hcd and address 39
[4295257.706000] usb 4-4: new high speed USB device using ehci_hcd and address 45
[4295257.923000] usb 4-3: new high speed USB device using ehci_hcd and address 46
[4295258.610000] usb 4-3: new high speed USB device using ehci_hcd and address 50
[4295261.705000] usb 4-4: new high speed USB device using ehci_hcd and address 68
[4295262.300000] usb 4-3: new high speed USB device using ehci_hcd and address 71
[4295264.860000] usb 4-3: new high speed USB device using ehci_hcd and address 86
[4295265.455000] usb 4-4: new high speed USB device using ehci_hcd and address 89
[4295267.360000] usb 4-3: new high speed USB device using ehci_hcd and address 100
[4295269.610000] usb 4-3: new high speed USB device using ehci_hcd and address 113
[4295270.738000] usb 4-4: new high speed USB device using ehci_hcd and address 119
[4295275.300000] usb 4-3: new high speed USB device using ehci_hcd and address 20
[4295275.517000] usb 4-4: new high speed USB device using ehci_hcd and address 21
[4295277.711000] usb 4-4: new high speed USB device using ehci_hcd and address 34
[4295277.928000] usb 4-3: new high speed USB device using ehci_hcd and address 35


I would truly love any help you may offer!

---

### Post by John.Michael.Kane on 2006-03-29
[http://tldp.org/HOWTO/Automount.html](http://tldp.org/HOWTO/Automount.html)
[http://www.linux-consulting.com/Amd_AutoFS/autofs.html](http://www.linux-consulting.com/Amd_AutoFS/autofs.html)


This may help.

---

### Post by brandon moore on 2006-03-29
i still can't get it to work... any other ideas??

---

