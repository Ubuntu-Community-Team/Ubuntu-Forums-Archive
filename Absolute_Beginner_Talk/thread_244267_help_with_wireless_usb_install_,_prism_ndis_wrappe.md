---
title: "help with wireless usb install , prism? ndis wrapper?"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by alanmzifa on 2006-08-26
Hi, I'm new to Linux and I need some help with setting up my wireless Netgear WG121 USB adapter.

I dual boot Ubuntu 6 with windows XP. Currently I'm connected via a LAN cable to get internet connection to post this but my wireless router is my preferred connection as the phone point is a long way away.

I've read things about [prism drivers]("http://prism54.org/newdrivers.html") which I think are linux flavoured drivers for some devices and using ndis wrapper but it's a all a bit daunting for me and I feel I'm more likely to break something than get it set up. I think however the WG121 is supported as I see it mentioned both on the [Prism site]("http://prism54.org/newdrivers.html") and on [this page]("http://gxaafoot.homelinux.org/cgi-bin/archzoom.cgi/jean-baptiste.note@m4x.org--libre/prism54-usb--devo--0.0--patch-331/islusb_init.c") which seems to be the text of the driver file.

Can someone walk me through it step by step over a period of days ((2 yr old + weekend!). I've seen other threads here on wireless set-up but can't follow them. Don't understand the terminology.

I have ndis wrapper installed and network manager.

Thanks in advance for your help.

---

### Post by Paul133 on 2006-08-26
Can you show me the output of ```
 ifconfig 
``` and ```
 iwconfig 
``` ?

---

### Post by alanmzifa on 2006-08-26
thanks

>  ifconfig
eth0      Link encap:Ethernet  **HWaddr 00:0C:76:56:ED:63**
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:76ff:fe56:ed63/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:123 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:106529 (104.0 KiB)  TX bytes:13904 (13.5 KiB)
          Interrupt:185 Base address:0xb400

eth2      Link encap:Ethernet  **HWaddr 00:09:5B:D1:42:5D**
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)
]

and

 > iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:"W office"
          Mode:Auto  Channel=1  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.



I noticed the USB adapter has the correct address but my router's MAC address is actually 00095bcd838 not the one listed here highlighted in bold.

---

### Post by Paul133 on 2006-08-26
In system>administration>device manager what does it say the chipset of your wireless adapter is? Is it Broadcom or another company?

---

### Post by alanmzifa on 2006-08-26
under the advanced device tab I see **usb_device_846_4210_no serial**. Sorry, can't copy and paste from this window, but I think that's the bit you're looking for.

I'll pop into Windows device manager, reckon the chipset with be named there.

---

### Post by alanmzifa on 2006-08-26
some extra info from Windows, don't know if it helps.

> NETGEAR WG121 802.11g Wireless USB2.0 Adapter
 primary  	Auto IP Address: 	192.168.0.3 / 24
	Gateway: 	192.168.0.1
	Dhcp Server: 	192.168.0.1
	Physical Address: 	00:09:5B:D1:42:5D
VIA Compatable Fast Ethernet Adapter
	Auto IP Address: 	192.168.0.2 / 24
	Gateway: 	192.168.0.1
	Dhcp Server: 	192.168.0.1
	Physical Address: 	00:0C:76:56:ED:63
 
Networking Dns Servers: 	127.0.0.1
192.168.0.1

and here's something from a .cat file in the Windows driver.

> ;***********************************************************************
;Netgear WG121
;***********************************************************************

[Version]
 DriverVer           = 11/13/2003, 1.0.5.1000
 Signature           = "$Chicago$"
 Compatible          = 1
 Class               = Net
 ClassGUID           = {4d36e972-e325-11ce-bfc1-08002be10318}
 Provider            = %VER_VENDOR_STR%
;CatalogFile         = netwg121.cat

[ControlFlags]
;Exclude all PNP adapters from user selection
 ExcludeFromSelect   = *

[Manufacturer]
 %VER_VENDOR_NAME_STR% = DeviceList,NTx86

[DeviceList]
;==========
[DeviceList.NTx86]
 %A021_DESC_STR%     = WG121_A021,        USB\VID_0846&PID_4200
 %A021_DESC_STR%     = WG121_A022,        USB\VID_0846&PID_4210
[WG121_A021]       ; Win9x
 AddReg         = WG121_A021.reg, COMMON_A02.reg, COMMON_NDIS.reg, COMMON.reg
 CopyFiles      = WG121_DRIVER.copy

[WG121_A022]       ; Win9x
 AddReg         = WG121_A022.reg, COMMON_A02.reg, COMMON_NDIS.reg, COMMON.reg
 CopyFiles      = WG121_DRIVER.copy

[WG121_A021.NT]    ; Win2k
 AddReg         = WG121_A021.reg, COMMON_A02.reg.NT, COMMON_NDIS.reg.NT, COMMON.reg
 CopyFiles      = WG121_DRIVER.copy.NT
 BusType        = 0
 Characteristics= 0x84

[WG121_A022.NT]    ; Win2k
 AddReg         = WG121_A022.reg, COMMON_A02.reg.NT, COMMON_NDIS.reg.NT, COMMON.reg
 CopyFiles      = WG121_DRIVER.copy.NT
 BusType        = 0
 Characteristics= 0x84

[WG121_A021.NT.Services]
 AddService= "wg121", 2, WG121_DRIVER_A02.Service, WG121_DRIVER.EventLog

[WG121_A022.NT.Services]
 AddService= "wg121", 2, WG121_DRIVER_A02.Service, WG121_DRIVER.EventLog

[WG121_A021.reg]
 HKR,Ndi,DeviceID,0,"USB\VID_0846&PID_4200"
; 0x3890 = 14480
 HKR,,PlatformID,0,14480
 HKR,,VendorDesc,0,%A021_DESC_STR%
 HKR,,FWFileName,0,"PRISMA02.arm"

[WG121_A022.reg]
 HKR,Ndi,DeviceID,0,"USB\VID_0846&PID_4210"
; 0x3890 = 14480
 HKR,,PlatformID,0,14480
 HKR,,VendorDesc,0,%A021_DESC_STR%
 HKR,,FWFileName,0,"**PRISMA02.arm**"

I think the bit I've highlighted helps identify the chip.

---

### Post by alanmzifa on 2006-08-27
Anyone, 


I'm trying to use ndiswrapper to install the Windows driver for my USB wireless adapter. The device is supposed to be supported by ndiswrapper accoring to [this list]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#N").

I can't seem to get the driver to install however. I must be doing something stupid. I've copied the .inf ans .sys files from the adapter's intstall cd to my ubuntu desktop and then use the ndiswrapper's gui explorer to browse to it and click o.k.  When I try to do the same with the .sys file I get an error message.....not a valid driver .inf file.

**Can someone please walk me through the process of installing the drivers?**

Thanks

---

### Post by alanmzifa on 2006-08-27
** Can someone please take a look at this below? Thanks. **

I'm not sure if I know the correct way to install the driver. ndiswrapper sometimes shows one to be there and installed but says no hardware.


iwconfig shows

>  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:"W office"
          Mode:Auto  Channel=14  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

monty@monty-desktop:~$

ifup

> ifup: interface eth2 already configured

ifconfig

> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:76:56:ED:63
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:76ff:fe56:ed63/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6832 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6463 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4804983 (4.5 MiB)  TX bytes:936913 (914.9 KiB)
          Interrupt:185 Base address:0xb400

eth2      Link encap:Ethernet  HWaddr 00:09:5B:D1:42:5D
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5672 (5.5 KiB)  TX bytes:5672 (5.5 KiB)


---

