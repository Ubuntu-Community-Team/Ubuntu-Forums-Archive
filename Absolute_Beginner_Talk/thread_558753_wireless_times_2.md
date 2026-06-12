---
title: "wireless times 2"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by anfractuosities on 2007-09-24
Is it possible to set up my machine to use my internal wireless AND a usb wireless dongle?  one at a time obviously.

Thanks

---

### Post by Austin_KW on 2007-09-24
> **anfractuosities said:**
> Is it possible to set up my machine to use my internal wireless AND a usb wireless dongle?  one at a time obviously.

Thanks

Yes, but why, what exactly are you trying to achieve? If you have drivers for both devices then 2 wireless interfaces will come up. Network manager will only manage one at a time but you can manually manage the other.

---

### Post by anfractuosities on 2007-09-24
I want to build an antenna out of my trendnet 424ub to get better reception in my apartment.  But I dont want to have to bring it with me everywhere I go, hence still being able to use the internal card.  I have drivers for both, but only my internal wireless is shown in iwconfig.

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"basement"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:15:E9:19:A1:BE   
          Bit Rate:36 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/100  Signal level=-79 dBm  Noise level=-80 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1279   Missed beacon:0



also it is the realtek chipset and i am running 64 bit ubuntu feisty

---

### Post by master_kernel on 2007-09-24
Probably, depending on the device drivers. Just try plug & play for the USB.

---

### Post by anfractuosities on 2007-09-24
plug and play? like,  just plug it in?    It doesnt work, I've been at it for days, trying whatever I can find.  There is no shortage of things to try in order to ge tthis card installed, and none of them have worked.

---

### Post by Austin_KW on 2007-09-24
You need to  do a forum search for your chipset, I think you may need to use the windows driver with ndiswrapper but I am not sure. If it is not creating an interface then the driver is probably not installed by default.

---

### Post by anfractuosities on 2007-09-24
i've already  found the driver for my card, I've gone through all of the steps and counter steps of installing it with ndiswrapper,  

ndswrapper -l
recoginizes the driver and device

I get to the step iwconfig wlan0 and i get


wlan0 no such device

---

### Post by anfractuosities on 2007-09-24
is this wlan0 missing a symptom of my computer or my wiress usb stick?

---

### Post by Austin_KW on 2007-09-24
what does "ifconfig -a" and "dmesg" report when you load the driver, if it is working it should create a wlanX interface.

---

### Post by anfractuosities on 2007-09-24
iwconfig -a


eth0      Link encap:Ethernet  HWaddr 00:18:F3:85:77:35  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x8c00 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:11:D6:CD  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fe11:d6cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:9690 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64683433 (61.6 MiB)  TX bytes:6721412 (6.4 MiB)
          Interrupt:17 Base address:0xe000 Memory:ff8ff000-ff8fffff 

eth0:avah Link encap:Ethernet  HWaddr 00:18:F3:85:77:35  
          inet addr:169.254.6.115  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3734 (3.6 KiB)  TX bytes:3734 (3.6 KiB)
THE desmg was really long, here is part


dmesg


[ 9508.521644] usb 5-2: USB disconnect, address 7
[ 9515.310562] usb 5-2: new high speed USB device using ehci_hcd and address 8
[ 9515.449899] usb 5-2: configuration #1 chosen from 1 choice
[ 9515.566855] usb 5-2: reset high speed USB device using ehci_hcd and address 8
[ 9515.705588] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 9515.705599] ndiswrapper (load_sys_files:216): couldn't prepare driver 'net8187b'
[ 9515.705938] ndiswrapper (load_wrap_driver:118): couldn't load driver net8187b; check system log for messages from 'loadndisdriver'
[ 9528.422015] usb 5-2: USB disconnect, address 8
[13723.858171] usb 5-2: new high speed USB device using ehci_hcd and address 9
[13723.997524] usb 5-2: configuration #1 chosen from 1 choice
[13724.118441] usb 5-2: reset high speed USB device using ehci_hcd and address 9
[13724.257075] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[13724.257085] ndiswrapper (load_sys_files:216): couldn't prepare driver 'net8187b'
[13724.257443] ndiswrapper (load_wrap_driver:118): couldn't load driver net8187b; check system log for messages from 'loadndisdriver'
[14952.360696] usb 5-2: USB disconnect, address 9
[15590.883676] usb 5-2: new high speed USB device using ehci_hcd and address 10
[15591.022939] usb 5-2: configuration #1 chosen from 1 choice
[15591.140007] usb 5-2: reset high speed USB device using ehci_hcd and address 10
[15591.278552] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[15591.278564] ndiswrapper (load_sys_files:216): couldn't prepare driver 'net8187b'
[15591.278906] ndiswrapper (load_wrap_driver:118): couldn't load driver net8187b; check system log for messages from 'loadndisdriver'



also, driver is 64 bit versioncurrently, but ive tried them all

---

### Post by anfractuosities on 2007-09-24
i am debating about returning the dongle, and modifing my case, b/c I am getting tired of trying to make this work...its my second dongle ive tried...

---

### Post by driftingprogrammer on 2008-02-24
I get the same error - kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B, i am trying to install TL-WN620G and installed the latest ndiswrapper 1.52. The name of my drivers are net5523 and athfmwdl. I have reported my problem in more details here - [http://ubuntuforums.org/showthread.php?t=663897](http://ubuntuforums.org/showthread.php?t=663897)

Please anyone help :|

---

