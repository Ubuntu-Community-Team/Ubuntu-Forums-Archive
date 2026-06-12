---
title: "I know you've heard this before, but my wireless isn't working."
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by cwmaxson on 2006-05-23
Sorry to have to post this, but my wireless isn't working.  I am a total linux noob, and have gotten everything else to work fine.

Here is my IWCONFIG:
eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
I try to activate, and it won't.  I am using a compaq presario 2200 with a little button that turns on/off the card in windows.  I was wondering if this is a bit of proprietery crap or not.  I have used ndiswrapper to install the same driver I use in windows, thinking this should work, and it registers fine.  Anyways, Help would be appreciated.

PS Sorry if I didn't ask the right question, I'm not the nerd that my girlfriend thinks I am.

---

### Post by popkid on 2006-05-23
Hi, what release of Ubuntu are you using, Breezy or Dapper?

---

### Post by cwmaxson on 2006-05-23
Dapper

---

### Post by popkid on 2006-05-23
Ok, in dapper there is a linux driver for your chipset: bcm43xx

This has some advantages over ndiswrapper as you can use network manager tool to give better integration and control, but it also has some disadvantages (only works at 11MB/s currently....)

Anyway, one problem can be that ndiswrapper and bcm43xx are both trying to use your wireless chip...

if you type lsmod in a terminal window, is bcm43xx listed? or just ndiswrapper?

pK

---

### Post by cwmaxson on 2006-05-23
lsmod reveals bcm43xx used by 0, and I don't see ndiswrapper anywhere.

I uninstalled ndiswrapper and I still can't seem to accomplish much.

---

### Post by popkid on 2006-05-23
Ok, sounds like bcm43xx is being loaded at bootup by modprobe, for now I think trying to get you up and running under ndiswrapper is probably easier since you've got this far, it's not too difficult to switch to bcm43xx if you want to later.

In the terminal type:  modprobe -r bcm43xx
then: modprobe ndiswrapper
then : ndiswrapper -l

then try: iwconfig

and see what you get

also try: dmesg 
to see if there is any clue as to what is going on

Also, have you got any encryption set up on your wireless access point? i.e. WEP,WPA-PSK etc...

pK

---

### Post by cwmaxson on 2006-05-23
Ok, so I've gotten this far before, and I get
for ndiswrapper -l:
drivers/hardware present
for iwconfig:
eth0, sit0, etc - no wireless detected, but either no reference to eth1 or eth1 gives what I posted earlier.

As far as dmesg:
[4294693.101000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
shows up alot

also
[4301562.444000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available  or load failed.
[4301627.590000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[4301638.543000] eth0: no IPv6 routers present
[4301685.171000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available  or load failed.
[4301694.759000] ACPI: PCI interrupt for device 0000:02:06.0 disabled
[4301694.790000] ieee80211_crypt: unregistered algorithm 'NULL'
[4301709.199000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[4301709.213000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1792); check system log for messages from 'loadndisdriver'
[4301709.214000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization fai led
[4301735.668000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[4301735.674000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'strrchr '
[4301735.674000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmFreeC ontiguousMemorySpecifyCache'
[4301735.674000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmAlloc ateContiguousMemorySpecifyCache'
[4301735.674000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmGetPh ysicalAddress'
[4301735.674000] ndiswrapper (load_sys_files:218): couldn't prepare driver 'bcmw l5'
[4301735.675000] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (652 80); check system log for messages from 'loadndisdriver'

It seems like the ndiswrapper route won't even get my wireless recognized, whereas the bcm43xx will.  The problem is I can't seem to then activate the card.

Thanks Heaps for the assistance, does this help?

Also, I don't have my WPA on right now, but it usually is.

---

### Post by popkid on 2006-05-23
No problem, I've been through all these hoops before and know how frustrating it can be...

the bcm43xx lines in dmesg are from when it was still active and are normal (you need to put card firmware in a folder for it to access, its just complaining it hasn't got it) you don't need to worry about them for now as you've disabled bcm43xx.

sounds like ndiswrapper isn't reading the driver correctly...

what does 

tail -50 /var/log/syslog

give?

oh and leaving wpa off for now is not a bad plan, adds another level of complication!

pK

---

### Post by cwmaxson on 2006-05-23
May 23 18:05:45 localhost NetworkManager: <WARNING>^I nm_device_802_11_wireless_ scan (): could not trigger wireless scan on device eth1: No such device
May 23 18:05:46 localhost gconfd (root-5000): starting (version 2.14.0), pid 500 0 user 'root'
May 23 18:05:46 localhost gconfd (root-5000): Resolved address "xml:readonly:/et c/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 23 18:05:46 localhost gconfd (root-5000): Resolved address "xml:readwrite:/r oot/.gconf" to a writable configuration source at position 1
May 23 18:05:46 localhost gconfd (root-5000): Resolved address "xml:readonly:/et c/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 23 18:05:46 localhost gconfd (root-5000): Resolved address "xml:readonly:/va r/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 23 18:05:46 localhost gconfd (root-5000): Resolved address "xml:readonly:/va r/lib/gconf/defaults" to a read-only configuration source at position 4
May 23 18:05:50 localhost dhclient: No DHCPOFFERS received.
May 23 18:05:50 localhost dhclient: No working leases in persistent database - s leeping.
May 23 18:05:50 localhost ntpdate[5081]: step time server 82.211.81.145 offset 0 .002318 sec
May 23 18:05:52 localhost dhclient: Internet Systems Consortium DHCP Client V3.0 .3
May 23 18:05:52 localhost dhclient: Copyright 2004-2005 Internet Systems Consort ium.
May 23 18:05:52 localhost dhclient: All rights reserved.
May 23 18:05:52 localhost dhclient: For info, please visit [http://www.isc.org/pr](http://www.isc.org/pr) oducts/DHCP
May 23 18:05:52 localhost dhclient:
May 23 18:05:52 localhost firmware_helper[5095]: main: error loading '/lib/firmw are/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:06.0' with driver  'bcm43xx'
May 23 18:05:52 localhost kernel: [4294763.248000] bcm43xx: Error: Microcode "bc m43xx_microcode5.fw" not available or load failed.
May 23 18:05:52 localhost firmware_helper[5098]: main: error loading '/lib/firmw are/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:06.0' with driver  'bcm43xx'
May 23 18:05:52 localhost kernel: [4294763.259000] bcm43xx: Error: Microcode "bc m43xx_microcode5.fw" not available or load failed.
May 23 18:05:53 localhost dhclient: Listening on LPF/eth1/00:90:4b:b5:f9:43
May 23 18:05:53 localhost dhclient: Sending on   LPF/eth1/00:90:4b:b5:f9:43
May 23 18:05:53 localhost dhclient: Sending on   Socket/fallback
May 23 18:05:53 localhost dhclient: receive_packet failed on eth1: Network is do wn
May 23 18:05:54 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port  67 interval 7
May 23 18:05:54 localhost dhclient: send_packet: Network is down
May 23 18:06:01 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port  67 interval 20
May 23 18:06:01 localhost dhclient: send_packet: Network is down
May 23 18:06:05 localhost firmware_helper[5134]: main: error loading '/lib/firmw are/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:06.0' with driver  'bcm43xx'
May 23 18:06:05 localhost kernel: [4294776.208000] bcm43xx: Error: Microcode "bc m43xx_microcode5.fw" not available or load failed.
May 23 18:06:08 localhost NetworkManager: <WARNING>^I nm_device_802_11_wireless_ scan (): could not trigger wireless scan on device eth1: No such device
May 23 18:06:21 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port  67 interval 15
May 23 18:06:21 localhost dhclient: send_packet: Network is down
May 23 18:06:28 localhost firmware_helper[5153]: main: error loading '/lib/firmw are/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:06.0' with driver  'bcm43xx'
May 23 18:06:28 localhost kernel: [4294799.045000] bcm43xx: Error: Microcode "bc m43xx_microcode5.fw" not available or load failed.
May 23 18:06:31 localhost NetworkManager: <WARNING>^I nm_device_802_11_wireless_ scan (): could not trigger wireless scan on device eth1: No such device
May 23 18:06:36 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port  67 interval 18
May 23 18:06:36 localhost dhclient: send_packet: Network is down
May 23 18:06:51 localhost firmware_helper[5167]: main: error loading '/lib/firmw are/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:06.0' with driver  'bcm43xx'
May 23 18:06:51 localhost kernel: [4294821.899000] bcm43xx: Error: Microcode "bc m43xx_microcode5.fw" not available or load failed.
May 23 18:06:54 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port  67 interval 1
May 23 18:06:54 localhost dhclient: send_packet: Network is down
May 23 18:06:54 localhost NetworkManager: <WARNING>^I nm_device_802_11_wireless_ scan (): could not trigger wireless scan on device eth1: No such device
May 23 18:06:55 localhost dhclient: No DHCPOFFERS received.
May 23 18:06:55 localhost dhclient: No working leases in persistent database - s leeping.
May 23 18:07:14 localhost firmware_helper[5186]: main: error loading '/lib/firmw are/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:06.0' with driver  'bcm43xx'
May 23 18:07:14 localhost kernel: [4294844.789000] bcm43xx: Error: Microcode "bc m43xx_microcode5.fw" not available or load failed.
May 23 18:07:17 localhost NetworkManager: <WARNING>^I nm_device_802_11_wireless_ scan (): could not trigger wireless scan on device eth1: No such device
May 23 18:09:17 localhost firmware_helper[5249]: main: error loading '/lib/firmw are/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:06.0' with driver  'bcm43xx'
May 23 18:09:17 localhost kernel: [4294967.650000] bcm43xx: Error: Microcode "bc m43xx_microcode5.fw" not available or load failed.
May 23 18:09:20 localhost NetworkManager: <WARNING>^I nm_device_802_11_wireless_ scan (): could not trigger wireless scan on device eth1: No such device

Ummm, have no clue what all this says.

Here it is with ndiswrapper at the helm:
May 23 18:06:21 localhost dhclient: send_packet: Network is down
May 23 18:06:28 localhost firmware_helper[5153]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:06.0' with driver 'bcm43xx'
May 23 18:06:28 localhost kernel: [4294799.045000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
May 23 18:06:31 localhost NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth1: No such device
May 23 18:06:36 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
May 23 18:06:36 localhost dhclient: send_packet: Network is down
May 23 18:06:51 localhost firmware_helper[5167]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:06.0' with driver 'bcm43xx'
May 23 18:06:51 localhost kernel: [4294821.899000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
May 23 18:06:54 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
May 23 18:06:54 localhost dhclient: send_packet: Network is down
May 23 18:06:54 localhost NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth1: No such device
May 23 18:06:55 localhost dhclient: No DHCPOFFERS received.
May 23 18:06:55 localhost dhclient: No working leases in persistent database - sleeping.
May 23 18:07:14 localhost firmware_helper[5186]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:06.0' with driver 'bcm43xx'
May 23 18:07:14 localhost kernel: [4294844.789000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
May 23 18:07:17 localhost NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth1: No such device
May 23 18:09:17 localhost firmware_helper[5249]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:06.0' with driver 'bcm43xx'
May 23 18:09:17 localhost kernel: [4294967.650000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
May 23 18:09:20 localhost NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth1: No such device
May 23 18:11:20 localhost firmware_helper[5356]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:06.0' with driver 'bcm43xx'
May 23 18:11:20 localhost kernel: [4295090.485000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
May 23 18:11:22 localhost NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth1: No such device
May 23 18:12:26 localhost kernel: [4295156.660000] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
May 23 18:12:26 localhost kernel: [4295156.660000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
May 23 18:12:26 localhost kernel: [4295156.740000] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
May 23 18:12:26 localhost kernel: [4295156.740000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
May 23 18:12:26 localhost kernel: [4295156.940000] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
May 23 18:12:26 localhost kernel: [4295156.940000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
May 23 18:12:26 localhost kernel: [4295156.980000] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
May 23 18:12:26 localhost kernel: [4295156.980000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
May 23 18:13:20 localhost kernel: [4295210.707000] ACPI: PCI interrupt for device 0000:02:06.0 disabled
May 23 18:13:20 localhost ifplugd.agent[5426]: Stopping ifplugd for eth1
May 23 18:13:20 localhost NetworkManager: <debug info>^I[1148433200.278678] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_90_4b_b5_f9_43').
May 23 18:13:20 localhost NetworkManager: <information>^IDeactivating device eth1.
May 23 18:13:20 localhost kernel: [4295210.834000] ieee80211_crypt: unregistered algorithm 'NULL'
May 23 18:13:20 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.3
May 23 18:13:20 localhost dhclient: Copyright 2004-2005 Internet Systems Consortium.
May 23 18:13:20 localhost dhclient: All rights reserved.
May 23 18:13:20 localhost dhclient: For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
May 23 18:13:20 localhost dhclient:
May 23 18:13:20 localhost dhclient: Bind socket to interface: No such device
May 23 18:13:22 localhost NetworkManager: <WARNING>^I nm_device_802_11_wireless_get_mode (): error getting card mode on eth1: No such device
May 23 18:13:28 localhost kernel: [4295218.558000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
May 23 18:13:28 localhost loadndisdriver: loadndisdriver: load_driver(361): couldn't load driver bcmwl5
May 23 18:13:28 localhost kernel: [4295218.607000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'strrchr'
May 23 18:13:28 localhost kernel: [4295218.607000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmFreeContiguousMemorySpecifyCache'
May 23 18:13:28 localhost kernel: [4295218.607000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmAllocateContiguousMemorySpecifyCache'
May 23 18:13:28 localhost kernel: [4295218.607000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmGetPhysicalAddress'
May 23 18:13:28 localhost kernel: [4295218.607000] ndiswrapper (load_sys_files:218): couldn't prepare driver 'bcmwl5'
May 23 18:13:28 localhost kernel: [4295218.608000] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'

---

### Post by popkid on 2006-05-23
Hmmmm.... that is all referring to bcm43xx again, I'm guessing that perhaps it is being reloaded by hotplug when you press your wireless button on your laptop?

If you type in lsmod again, is bcm43xx listed (should be from what you just listed!)

pK

EDIT* ndiswrapper stuff at the end can't seem to load driver again

---

### Post by cwmaxson on 2006-05-23
My apologies, I've taped on the results after re-doing ndiswrapper.  Here they are:

May 23 18:06:21 localhost dhclient: send_packet: Network is down
May 23 18:06:28 localhost firmware_helper[5153]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:06.0' with driver 'bcm43xx'
May 23 18:06:28 localhost kernel: [4294799.045000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
May 23 18:06:31 localhost NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth1: No such device
May 23 18:06:36 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
May 23 18:06:36 localhost dhclient: send_packet: Network is down
May 23 18:06:51 localhost firmware_helper[5167]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:06.0' with driver 'bcm43xx'
May 23 18:06:51 localhost kernel: [4294821.899000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
May 23 18:06:54 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
May 23 18:06:54 localhost dhclient: send_packet: Network is down
May 23 18:06:54 localhost NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth1: No such device
May 23 18:06:55 localhost dhclient: No DHCPOFFERS received.
May 23 18:06:55 localhost dhclient: No working leases in persistent database - sleeping.
May 23 18:07:14 localhost firmware_helper[5186]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:06.0' with driver 'bcm43xx'
May 23 18:07:14 localhost kernel: [4294844.789000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
May 23 18:07:17 localhost NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth1: No such device
May 23 18:09:17 localhost firmware_helper[5249]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:06.0' with driver 'bcm43xx'
May 23 18:09:17 localhost kernel: [4294967.650000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
May 23 18:09:20 localhost NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth1: No such device
May 23 18:11:20 localhost firmware_helper[5356]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:02:06.0' with driver 'bcm43xx'
May 23 18:11:20 localhost kernel: [4295090.485000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
May 23 18:11:22 localhost NetworkManager: <WARNING>^I nm_device_802_11_wireless_scan (): could not trigger wireless scan on device eth1: No such device
May 23 18:12:26 localhost kernel: [4295156.660000] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
May 23 18:12:26 localhost kernel: [4295156.660000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
May 23 18:12:26 localhost kernel: [4295156.740000] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
May 23 18:12:26 localhost kernel: [4295156.740000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
May 23 18:12:26 localhost kernel: [4295156.940000] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
May 23 18:12:26 localhost kernel: [4295156.940000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
May 23 18:12:26 localhost kernel: [4295156.980000] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
May 23 18:12:26 localhost kernel: [4295156.980000] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
May 23 18:13:20 localhost kernel: [4295210.707000] ACPI: PCI interrupt for device 0000:02:06.0 disabled
May 23 18:13:20 localhost ifplugd.agent[5426]: Stopping ifplugd for eth1
May 23 18:13:20 localhost NetworkManager: <debug info>^I[1148433200.278678] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_90_4b_b5_f9_43').
May 23 18:13:20 localhost NetworkManager: <information>^IDeactivating device eth1.
May 23 18:13:20 localhost kernel: [4295210.834000] ieee80211_crypt: unregistered algorithm 'NULL'
May 23 18:13:20 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.3
May 23 18:13:20 localhost dhclient: Copyright 2004-2005 Internet Systems Consortium.
May 23 18:13:20 localhost dhclient: All rights reserved.
May 23 18:13:20 localhost dhclient: For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
May 23 18:13:20 localhost dhclient:
May 23 18:13:20 localhost dhclient: Bind socket to interface: No such device
May 23 18:13:22 localhost NetworkManager: <WARNING>^I nm_device_802_11_wireless_get_mode (): error getting card mode on eth1: No such device
May 23 18:13:28 localhost kernel: [4295218.558000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
May 23 18:13:28 localhost loadndisdriver: loadndisdriver: load_driver(361): couldn't load driver bcmwl5
May 23 18:13:28 localhost kernel: [4295218.607000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'strrchr'
May 23 18:13:28 localhost kernel: [4295218.607000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmFreeContiguousMemorySpecifyCache'
May 23 18:13:28 localhost kernel: [4295218.607000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmAllocateContiguousMemorySpecifyCache'
May 23 18:13:28 localhost kernel: [4295218.607000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmGetPhysicalAddress'
May 23 18:13:28 localhost kernel: [4295218.607000] ndiswrapper (load_sys_files:218): couldn't prepare driver 'bcmwl5'
May 23 18:13:28 localhost kernel: [4295218.608000] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'

---

### Post by popkid on 2006-05-23
Ok then... looks like bcm43xx may actually be a better way to go

can you just let me know what it says if you issue the following:

tail -50 /etc/network/interfaces

Sorry, we're are going around in circles a bit here!

pK.

---

### Post by cwmaxson on 2006-05-23
This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.


iface eth0 inet dhcp



iface dsl-provider inet ppp
provider dsl-provider

iface eth1 inet dhcp











auto eth1

auto eth0

---

### Post by Papa-san on 2006-05-23
LOL... Gotta love bcom...

I put some links in my signature that helped me, and have helped some others too...

Good luck!

---

### Post by popkid on 2006-05-23
Sorry, but I've got to get off to bed now...

I hope you can get this working, from what you have posted here, it actually seems like you are quite close.

Think this link may help too...

[http://ubuntuforums.org/showthread.php?t=180936]("http://ubuntuforums.org/showthread.php?t=180936")

When you installed ndiswrapper you did use the .inf file?

i.e

sudo ndiswrapper -i ~/Pathtoyourdriver/bcmwl5.inf
sudo ndiswrapper -m
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile

I'll check this thread tomorrow and try and help if you haven't sorted it by then...

Good luck.

pK

---

### Post by cwmaxson on 2006-05-24
Thanks heaps for the assistance, I've got it all working great!
You're my new favorite person.
Thank You.

---

### Post by popkid on 2006-05-24
[QUOTE=cwmaxson]Thanks heaps for the assistance, I've got it all working great!
You're my new favorite person.
Thank You.[/QUOTE]

:oops: No Problem at all, sorry I had to run last night, but it had got to like 3 AM here! Glad you've got it working, did you go with bcm43xx or with ndiswrapper in the end?

pK ;)

---

### Post by cwmaxson on 2006-05-24
BCM worked great.  I even got the whole WPA thing worked out.

---

### Post by popkid on 2006-05-24
Excellent news, glad you are happy with the way it is working!

pK.

---

