---
title: "Wireless problems"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by TheyStudios on 2007-07-03
Ok, I'm rather new to linux in general, but I've been lurking here for quite awhile to try and figure this problem out.  I'm trying to connect to my network via a Belkin USB dongle using the rt73 chipset.  I found the drivers (v 1.0.4.0), compiled them successfully, installed them successfully (I think), it sends and recieves packets, but I can't connect to my wireless router.  I can't provide iwconfig and ifconfig information right now, as I'm on another computer (I'll hardwire my Ubuntu box up to the router later tonight), but from the posts I've seen, everything is in order.  I've tried manual configuration and DHCP setups.  

The only strange thing is when I type ifconfig into the terminal, I get an extra interface called "rausb0:av".  After some searching, I found out this is the avahi-daemon that automatically searches for access points to connect to, and I think it may be the problem I'm having.  The only thing is, I can't disable it.  I went to /etc/default/avahi-daemon and set the start option to 0, but I still have the "rausb0:av" device listed in ifconfig.

I can provide more details later tonight, but if anyone has any clues to help me, they would be much appreciated.

---

### Post by kevdog on 2007-07-03
When you mean compile your drivers, you are talking about the CVS sources from the serial monkey site, correct?  

Your card is the ra chipset, and setting up ra cards, while they are a lot different than most of the methods people talk about it the forums, can be done successfully.

There are a couple of posts I want you to look at.  Ra has a series of chipsets 2500, 61, 2400, 2570, 73.  Although these forums may reference 2500 for example, the instructions are exactly similar for the 73 version other than the initial driver you have to download and compile.  The modifications needed of the /etc/network/interfaces file should be the same.

Here are the posts:
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)
[http://ubuntuforums.org/showthread.php?t=487645](http://ubuntuforums.org/showthread.php?t=487645)

---

### Post by TheyStudios on 2007-07-03
Thank you.  I'll look through these links real quick and see if they help me.  If not, I'll repost here with the problems I had :)

---

### Post by TheyStudios on 2007-07-03
Sadly, I've been through all these options.  I turned off the security just to get this working, so there's none to worry about.  I have a strong feeling this USB dongle simply refuses to see the router, as I get stuck here every time.  Are there any known issues with Ubuntu Studio 7.04 Feisty and Netopia 3347NWG routers?  I hate to sound like a know-it-all who doesn't, but I can follow directions easily.  Right now the directions I've followed haven't helped any.  I'm certain I've screwed up somewhere, I just don't know where.  So here's my stuff:

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

rausb0    RT73 WLAN  ESSID:off/any  
          Mode:Auto  Channel=1  Bit Rate:54 Mb/s   
          RTS thr:off   Fragment thr:off
```

Note that I've already specified an SSID to use, as shown here in ifconfig.  It sees the MAC address of the router, I've checked it:
```
eth0      Link encap:Ethernet  HWaddr 00:19:D1:0C:B3:91  
          inet addr:192.168.1.6  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe0c:b391/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2930 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3309393 (3.1 MiB)  TX bytes:415124 (405.3 KiB)
          Interrupt:21 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

rausb0    Link encap:Ethernet  HWaddr 00:17:3F:AD:CC:16  
          inet6 addr: fe80::217:3fff:fead:cc16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3791 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17727 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:434188 (424.0 KiB)  TX bytes:1312242 (1.2 MiB)

rausb0:av Link encap:Ethernet  HWaddr 00:17:3F:AD:CC:16  
          inet addr:169.254.6.59  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

```

What worries me is the rausb0:av interface.  I did not put it there.  I've learned that it's likely the avahi-daemon that roams for access points (and I've learned it can cause problems), but I can't seem to disable it via standard methods (/etc/default/avahi-daemon).  I really don't want to reinstall, but I get the feeling I'm going to have to.

---

### Post by kevdog on 2007-07-04
So lets start with some basics -- can you post the following

lshw -C network
/etc/network/interfaces
iwlist scan
lsmod | grep rt

Dont worry about the av interface for now.  Its not causing the problem.

---

### Post by TheyStudios on 2007-07-04
lshw -C network:
```
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth0
       version: 10
       serial: 00:19:d1:0c:b3:91
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.6 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:1000-10ff iomemory:32000000-320000ff irq:21
  *-network
       description: Wireless interface
       physical id: 1
       logical name: rausb0
       serial: 00:17:3f:ad:cc:16
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT73 WLAN
```

/etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# rt73 wireless network device using DHCP
auto raubs0
iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
wireless-essid regicide
```

iwlist scan:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

rausb0    Interface doesn't support scanning.
```

lsmod | grep rt:
```
snd_rtctimer            4384  0 
snd_timer              24196  4 snd_rtctimer,snd_pcm,snd_seq
parport_pc             36644  1 
parport                37576  3 ppdev,lp,parport_pc
rt73                  216192  0 
agpgart                35788  2 nvidia,ati_agp
usbcore               135048  5 ndiswrapper,rt73,ehci_hcd,ohci_hcd
```

Please help.

For the sake of sheep, I really want to understand what is going on with my computer right now.  I would appreciate the most in-depth descriptions possible, because I want to learn Linux.  I want to know what makes what work.  I may have a phobia of not understanding computer stuff I do, I'm not sure.  I do Flash movies and 3d animation for a living, and I understand those aspects very well.  I really want to know what's going on when I do stuff :)

---

### Post by kevdog on 2007-07-04
The rt73 driver -- was this compiled from source via the serialmonkey site??  I think I asked this above?

I searched on the serialmonkey forums for your card, it seems you must blacklist the rt73usb, rt2570, rt2x00lib, rt2500usb modules and install the _[ rt73 cvs]("http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz")_ driver.


I can give you more info if needed.

You have a typo in your /etc/network/interfaces file
> auto raubs0
iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
wireless-essid regicide

I think the first line should be
```
auto rausb0
```

Also here is a snippet I found from another post about how to set up you /etc/network/interfaces file.  Its different than yours (you will need to substitute rausb0 for wlan0)
```
	pre-up ifconfig wlan0 up
	pre-up iwconfig wlan0 essid YOUR_ESSID
	pre-up iwconfig wlan0 key WEP_KEY_OR_"OFF"_IF_YOU_HAVE_NONE
```

---

### Post by TheyStudios on 2007-07-04
Yes, all the necessary drivers are blacklisted, and this one still ceases to work.  I have the serialmonkey driver compiled and installed.

Thanks for the typo fix :)  It didn't fix my problem though, as I still have the same problems.  Does anyone have a method to really disable  avahi-daemon from starting up?  Disabling from /etc/default/avahi-daemon doesn't actually disable it, as it still loads at reboot.  Or relogin, it doesn't seem to go away no matter what I do.

---

### Post by Austin_KW on 2007-07-04
I notice that ndiswrapper is installed and using usbcore so you will want to add blacklist ndiswrapper.

When did you download the serialmonkey driver, recent versions have changed to wlan0 as the default interface, recent changes are also better at supporting SMP.

If this is a recent download of the rt73 driver, check /etc/iftab and see if there is an entry for rausb*, and also check /etc/modprobe.conf

There is a detailed howto for the rt73 at [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

You might also try letting the system boot before inserting the wireless usb, then check the output of dmesg

---

### Post by TheyStudios on 2007-07-04
This is my /etc/modprobe.conf file:
```
alias rausb0 rt73
alias wlan* rt73
```

I added ndiswrapper to my blacklist (if there is any way to just remove the driver installed, that would help me alot too :)) 

I reinstalled the rt73 driver last night, so that's pretty fresh.  It's still listed as rausb0 though.  Could that be the problem?

I'll try the boot idea as well.

---

### Post by Austin_KW on 2007-07-04
remove the first alias; "alias rausb0 rt73" and leave the wlan* and it should create the interface as wlan0.

It still should have worked after you removed the ndiswrapper even for rausb0.
"locate ndiswrapper.ko" will list all the locations of the ndiswrapper, you could just delete them

---

### Post by TheyStudios on 2007-07-04
ndiswrapper is completely gone now,  The dongle shows up as wlan0 now, and it at least shows the network I'm trying to connect to :)  Here are current...

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT73 WLAN  ESSID:"regicide"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:19:D1:0C:B3:91  
          inet addr:192.168.1.6  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe0c:b391/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28410 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40291394 (38.4 MiB)  TX bytes:1175676 (1.1 MiB)
          Interrupt:21 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:17:3F:AD:CC:16  
          inet6 addr: fe80::217:3fff:fead:cc16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:427 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1514 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:52236 (51.0 KiB)  TX bytes:112184 (109.5 KiB)

wlan0:ava Link encap:Ethernet  HWaddr 00:17:3F:AD:CC:16  
          inet addr:169.254.6.59  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
```

It still won't connect, and it's sitting right next to the router so I know it's not a range issue.  Any more ideas?  If I can't get it working today I'm gonna end up wiping and reinstalling and starting from scratch.

---

### Post by Austin_KW on 2007-07-04
Ok, you are nearly there, What are you using to configure the device (have you changed /etc/network/interfaces to reflect that the interface is now wlan0), and do you have encryption?

Also try removing the adapter and reinserting after a few seconds, if you are using /etc/network/interfaces to configure it  you may need to type "sudo ifup --f wlan0" after reinserting.

Also you can be too close to the router, there is sometimes a dead bubble around the antenna.

---

### Post by TheyStudios on 2007-07-04
My /etc/network/interfaces shows wlan0 now, I removed the references to rausb0 as well (I'm kinda anal retentive about having an extremely neat computer :P).  This is how my /etc/network/interfaces file looks now:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp

# wireless dongle thingie
iface wlan0 inet dhcp
wireless-essid regicide
wireless-key s:1234567890

auto wlan0
```

When I run sudo ifup --f wlan0, I get this:
```
There is already a pid file /var/run/dhclient.wlan0.pid with pid 7648
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:17:3f:ad:cc:16
Sending on   LPF/wlan0/00:17:3f:ad:cc:16
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

It's not finding the router :(  Any suggestions?

---

### Post by Austin_KW on 2007-07-04
I don't use wep ( i use wpa) but wep key is 40 or 104 bits. For 40 bit (sometimes referred to as 64 bit) you need either 10 hex digits or 5 ascii characters. You have set a string "s:1234567890" which is 10 ascii characters. 
Either you mean "1234567890" or "s:12345", I assume you mean the hex digits 1234567890

Try replacing you wlan0 config with
```

# wireless dongle thingie
iface wlan0 inet dhcp
auto wlan0
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid regicide
pre-up iwconfig wlan0 key 1234567890

```

and then do "sudo ifup --f wlan0"

---

