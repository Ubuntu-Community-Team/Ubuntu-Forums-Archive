---
title: "de-cyphering ifconfig and wlan0"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Buster95 on 2007-06-10
Trying to understand why my wired connection works and my wireless connection doesn't.
Question:
The wired connection, eth0, shows inet addr: 192.168.0.6, which is my Netgear DG834G router address. The "standard" local-loopback address of 127.0.0.1 also comes up.
However, the wlan0 connection does not show the router address at all and wlan0:ava (whatever the hell that is) shows a totally different inet address which I do not recognise.
I would have expected the wlan0 to point to the router address in order to "see" it.

Can anbody guide me through this?
Thanks


dexter@dexim-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:F5:57:BA:BB  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:f5ff:fe57:babb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10287 (10.0 KiB)  TX bytes:19821 (19.3 KiB)
          Interrupt:21 Base address:0x4800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:556 (556.0 b)  TX bytes:556 (556.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:15:AF:12:7D:B7  
          inet6 addr: fe80::215:afff:fe12:7db7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:13988 (13.6 KiB)

wlan0:ava Link encap:Ethernet  HWaddr 00:15:AF:12:7D:B7  
          inet addr:169.254.7.49  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-12-7D-B7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by ayenack on 2007-06-10
What wireless card do you have and what version of Ubuntu are you running?

ayenack.

---

### Post by Buster95 on 2007-06-10
> **ayenack said:**
> What wireless card do you have and what version of Ubuntu are you running?

ayenack.

Thanks ayenack,

Here is my kernel description (Feisty)
dexter@dexim-laptop:~$ uname -a
Linux dexim-laptop 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686 GNU/Linux

Not sure about the card. I'm using a Clevo laptop which uses an integrated Via chipset. Maybe this will assist.
Thanks

dexter@dexim-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 7c
       serial: 00:90:f5:57:ba:bb
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.2 duplex=full ip=192.168.0.6 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: ioport:4800-48ff iomemory:cb400400-cb4004ff irq:21
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:12:7d:b7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by ayenack on 2007-06-10
Can you give me the model of the Clevo i.e. M72S or M540N. Need to find out what wireless card you have on board and if there's a driver for it.

Also try this in terminal:
**iwconfig**

I'm sure you know this but anyway, it's a good idea not to try to configure your wireless card/network while you have your wired connection running so if you had your wired connection running while you configured you wireless this may be the problem.

ayenack.

---

### Post by Buster95 on 2007-06-10
> **ayenack said:**
> Can you give me the model of the Clevo i.e. M72S or M540N. Need to find out what wireless card you have on board and if there's a driver for it.

I'm sure you know this but anyway, it's a good idea not to try to configure your wireless card/network while you have your wired connection running so if you had your wired connection running while you configured you wireless this may be the problem.

ayenack.

Thanks ayenack,
Clevo  M66SE

I've tried disabling wired connection in order to enable wireless.
I've also loaded WiFiRadar hoping that it might do something for me, but it can't "see" the router either.
Tried manually entering router information on WiFiRadar. That didn't help either.
By the way, another laptop in my house works OK on the wireless, with the same settings.
Cheers

---

### Post by ayenack on 2007-06-10
Do you mean the M660SE? If you do then you need to take a trip to this [site]("http://www.realtek.com.tw/search/default.aspx?keyword=rtl8187") and download the drivers. There are two versions the [RTL8187B]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187B") and the [RTL8187L]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187L") not sure which of these you will need so you'll have to try each and see which works best. It seems to me that even these drivers may not work. From what I can gather there seems to be some real issues with this card. Strange as RealTek say it's supported in GNU Linux. Not to sure about this but there may also be some dependency problems, i.e. you need to install other drivers via "Synaptic" or "sudo apt get install" to get this one to work.

ayenack.

---

### Post by Buster95 on 2007-06-10
> **ayenack said:**
> Do you mean the M660SE? If you do then you need to take a trip to this [site]("http://www.realtek.com.tw/search/default.aspx?keyword=rtl8187") and download the drivers. There are two versions the [RTL8187B]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187B") and the [RTL8187L]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187L") not sure which of these you will need so you'll have to try each and see which works best. It seems to me that even these drivers may not work. From what I can gather there seems to be some real issues with this card. Strange as RealTek say it's supported in GNU Linux. Not to sure about this but there may also be some dependency problems, i.e. you need to install other drivers via "Synaptic" or "sudo apt get install" to get this one to work.

ayenack.

M66SE is what it says on the label on the bottom of the laptop. 
I know that the card worked with Edgy, so I'm still hopeful. I'll try your suggested downloads.
Thanks for your assistance. I'll report on success or otherwise.
Cheers

---

### Post by Buster95 on 2007-06-11
In response to an earlier question about iwconfig:

dexter@dexim-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Downloaded RTL8187L from the site you directed me to. Tried to extract it with "tar...etc" in a terminal.
Got all sorts of error messages, so I had look to see where it all ended up. That's shown below.

dexter@dexim-laptop:~$ locate rtl8187
/usr/src/linux-headers-2.6.20-15-generic/include/config/rtl8187.h
/usr/src/linux-headers-2.6.20-16/ubuntu/wireless/rtl8187
/usr/src/linux-headers-2.6.20-16/ubuntu/wireless/rtl8187/Makefile
/usr/src/linux-headers-2.6.20-16/ubuntu/wireless/rtl8187/Kconfig
/usr/src/linux-headers-2.6.20-16-generic/include/config/rtl8187.h
/usr/src/linux-headers-2.6.20-15/ubuntu/wireless/rtl8187
/usr/src/linux-headers-2.6.20-15/ubuntu/wireless/rtl8187/Makefile
/usr/src/linux-headers-2.6.20-15/ubuntu/wireless/rtl8187/Kconfig
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rtl8187
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rtl8187/rtl8187.ko
/lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rtl8187
/lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/rtl8187/rtl8187.ko

Either it worked, or the driver was already there.
Anyhow, rebooted and it still doesn't see the wireless router.

I'm still puzzled why the wlan0 interrogates an address that I don't recognise. An extract is shown below;
dexter@dexim-laptop:~$ dhclient wlan0
...........................
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
[B]Listening on LPF/wlan0/00:15:af:12:7d:b7
Sending on   LPF/wlan0/00:15:af:12:7d:b7[/B]
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

The bit in bold is what confuses me. I don't know why it's trying to "handshake" that address.
Any suggestions?
Thanks

---

### Post by ayenack on 2007-06-11
May seem like a silly question but have you got roaming on? 

So the card seems to be there and it seems to be picking up a network, maybe you should try pinging it to see if you get any joy.

Did you upgrade via Live CD or did you upgrade via net from Edgy? Reason I ask this is that if you installed Feisty from Live CD it may not have configured correctly. If you can't resolve this it may be worth installing Edgy again and then upgrading from the net this has worked for me in the past with troublesome hardware. Don't know why but it has.

Also if it's an M66SE then my guess would be that the new drivers are wrong.

Just looking back over your iwconfig post it seems strange to me that your wireless card is not associated with your Netgear Router it's seeing it because it says its there so this may be a config problem.

00:15:af:12:7d:b7 my guess is this is someone else's AP/Router that you wireless is trying to connect to for some reason. It was also listed in your earlier posts. Try turning off Multicast DNS Service Discovery. System>Administration>Services. And also make sure that Automatic Service Discovery is not on. System>Administration>Network then the General tab.

Sorry about the delay in posting back big time gap between Aus and here.

---

### Post by Buster95 on 2007-06-12
Hello ayenack,
 To answer the specifics:

> **ayenack said:**
> May seem like a silly question but have you got roaming on? 

**Roaming is off**

So the card seems to be there and it seems to be picking up a network, maybe you should try pinging it to see if you get any joy.

**Tried pinging - no success. I don't think that it is picking up the router because dhclient wlan0 returns no offers.**

Did you upgrade via Live CD or did you upgrade via net from Edgy? Reason I ask this is that if you installed Feisty from Live CD it may not have configured correctly. If you can't resolve this it may be worth installing Edgy again and then upgrading from the net this has worked for me in the past with troublesome hardware. Don't know why but it has.

**I loaded Feisty from a Canonical disk. I presumed that I it was a clean install and not an upgrade. It certainly killed my Edgy installation when I did the partitioning. Since the install, there has been a kernel upgrade, which downloaded OK (if that means anything).**



Also if it's an M66SE then my guess would be that the new drivers are wrong.

**I also got a bit puzzled when I googled Clevo M66SE and could only find M660SE. I resolved that (in my mind at least) by studiously ignoring the missing digit! Also looked on the Viaarena site. They make most of the chipsets in it, but that didn't take me anywhere.**

Just looking back over your iwconfig post it seems strange to me that your wireless card is not associated with your Netgear Router it's seeing it because it says its there so this may be a config problem.

**Although iwconfig shows that the ESSID is showing NETGEAR, I thought that it was because I manually entered that information in the "connections" settings. It certainly didn't acquire it automatically. I have removed it once to see whether it would re-acquire it using WiFi Radar. It didn't.**

00:15:af:12:7d:b7 my guess is this is someone else's AP/Router that you wireless is trying to connect to for some reason. It was also listed in your earlier posts. Try turning off Multicast DNS Service Discovery. System>Administration>Services. And also make sure that Automatic Service Discovery is not on. System>Administration>Network then the General tab.

**I'll try that suggestion and report back. I guess I could also try to find where it's being plucked from (/etc/modprobe.d/networking perhaps?) and change to my preferred flavour. What do you think?**

Sorry about the delay in posting back big time gap between Aus and here.

**Please don't apologise. I'm pathetically grateful that someone is prepared to help me through this puzzle.**

iwconfig also shows the presence of wmaster0. Should that be there? Should it be enabled? I've tried it on, off, roaming and every other which-way, but it doesn't seem to have any effect.

---

### Post by ayenack on 2007-06-13
I think that we really need to find out what wireless card you've got in your laptop. Don't know if you can contact the place where you bought it from or even Clevo. APAC email [email]asiapacifiicsales@clevo.com.tw[/email] this is the sales email but they should be able to point you in the right direction.

Feisty would be a fresh install from CD. But I think that you said that wireless worked on edgy. The kernel upgrade makes no difference, I would think.

If your wireless did work on Edgy and you have no important data on the feisty install may want to reinstall Feisty and configure wireless before wired to see if that works. I find it strange that the wireless should work on Edgy and not Feisty.

Your correct about wmaster0 to my mind this should not be there.
This brings back a problem I had with a USB wireless card that showed up on wlan0 and wlmaster0. I can't remember exactly how I resolved this but I do remember that I had to change config to rausb1 to get the thing working. Real pain.

btw if you have wireless options in Networking this should mean that your card is at least known to be there by the OS. This is a positive sign at least.

'> l*l I guess I could also try to find where it's being plucked from (/etc/modprobe.d/networking perhaps?) and change to my preferred flavour. What do you think?*

Worth a try but not hopeful on that one.

Quick question. In Network does it show wlan0 & wmaster0? Should not have two connections for one card that's for sure.

I've got to go to work now will try to get back a bit later in the day. Also try to do a bit of research on this, it's annoying bugging me to say the least.

Best of luck. ayenack.

PS if you've got windows on your laptop check in system to see what wireless card it is.

Just realised something 00:15:af:12:7d:b7 is your hardware address. Not another router/AP, I think. It's simply the wireless card in your laptop. Most likely that this is a hardware recognition problem plain and simple. Need to know what card you have in your machine.

---

### Post by ayenack on 2007-06-13
If you haven't already try these steps in terminal.

**sudo ifdown eth0**

**sudo ifdown wmaster0**

**sudo ifdown wlan0**

Leave "lo" as is. 

This should turn off all network connections on your laptop. After this is done follow the instructions bellow.

**sudo ifup wlan0**

**ifconfig** To see if it's there. Also try browsing the net. If this does not work follow instructions bellow.

In terminal.

**iwconfig wlan0 mode managed** (Type this as is)
**iwconfig wlan0 channel 11** (This will be your routers/AP's wireless channel. Normally 11. Check to be sure)
**iwconfig wlan0 essid networkname** (Your Network Name which I think is NETGEAR or Netgear DG834G)

This might work not to sure but worth a try I would say.

Also can you post the contents of this file leaving out any sensitive info i.e. network keys.

**sudo gedit /etc/network/interfaces**

Also can you post the results of this. In terminal type:

**lspci -v | less**

---

### Post by Buster95 on 2007-06-14
> **ayenack said:**
> If you haven't already try these steps in terminal.

**sudo ifdown eth0**

**sudo ifdown wmaster0**

**sudo ifdown wlan0**

Leave "lo" as is. 

This should turn off all network connections on your laptop. After this is done follow the instructions bellow.

**sudo ifup wlan0**

**ifconfig** To see if it's there. Also try browsing the net. If this does not work follow instructions bellow.

In terminal.

**iwconfig wlan0 mode managed** (Type this as is)
**iwconfig wlan0 channel 11** (This will be your routers/AP's wireless channel. Normally 11. Check to be sure)
**iwconfig wlan0 essid networkname** (Your Network Name which I think is NETGEAR or Netgear DG834G)

This might work not to sure but worth a try I would say.

Also can you post the contents of this file leaving out any sensitive info i.e. network keys.

**sudo gedit /etc/network/interfaces**

Also can you post the results of this. In terminal type:

**lspci -v | less**

Hello again,
Tried these steps and somehow lost my ethernet as well. had to wait until I got to work to report back. I'll have another go when I get home and keep you posted.
Cheers

---

### Post by ayenack on 2007-06-14
To turn eth0 back on do this in terminal.

**sudo ifup eth0** (the sudo ifup eth0 turns on your Ethernet, eth0)

Should have explained what each command does it's the same for the other commands.**sudo  ifdown wlan0** will turn off wlan0 and so forth. The " if " stands for "interface" btw.

**lspci -v | less** this will list all PCI cards/ports etc it's a way to find out what cards you have in your system. If you wanted to find out what USB cards you had you would type **lsusb -v | less** this would bring up a list of USB cards etc. When you do this it will bring up a list in terminal that you can scroll through so as to get a better understanding of what card you have. Don't know if you knew all this so put it down just in case. The " ls " stands for "list" The "-v" stands for "verbose"

---

### Post by Buster95 on 2007-06-15
> **ayenack said:**
> To turn eth0 back on do this in terminal.

**sudo ifup eth0** (the sudo ifup eth0 turns on your Ethernet, eth0)

Should have explained what each command does it's the same for the other commands.**sudo  ifdown wlan0** will turn off wlan0 and so forth. The " if " stands for "interface" btw.

**lspci -v | less** this will list all PCI cards/ports etc it's a way to find out what cards you have in your system. If you wanted to find out what USB cards you had you would type **lsusb -v | less** this would bring up a list of USB cards etc. When you do this it will bring up a list in terminal that you can scroll through so as to get a better understanding of what card you have. Don't know if you knew all this so put it down just in case. The " ls " stands for "list"

Thanks ayenack,
Regarding my knowledge of Linux, I know just enough to be dangerous but not enough to be useful!
I'll report back.
Cheers

---

### Post by Buster95 on 2007-06-16
> **ayenack said:**
> If you haven't already try these steps in terminal.

**sudo ifdown eth0**

**sudo ifdown wmaster0**

**sudo ifdown wlan0**

Leave "lo" as is. 

This should turn off all network connections on your laptop. After this is done follow the instructions bellow.

**sudo ifup wlan0**

**ifconfig** To see if it's there. Also try browsing the net. If this does not work follow instructions bellow.



In terminal.

**iwconfig wlan0 mode managed** (Type this as is)
**iwconfig wlan0 channel 11** (This will be your routers/AP's wireless channel. Normally 11. Check to be sure)
**iwconfig wlan0 essid networkname** (Your Network Name which I think is NETGEAR or Netgear DG834G)

This might work not to sure but worth a try I would say.

Also can you post the contents of this file leaving out any sensitive info i.e. network keys.

**sudo gedit /etc/network/interfaces**

Also can you post the results of this. In terminal type:

**lspci -v | less**

**sudo gedit /etc/network/interfaces**
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid NETGEAR
wireless-key [deleted}

auto wmaster0
iface wmaster0 inet dhcp
wireless-essid NETGEAR
wireless-key {deleted}
[B]
lspci -v | less[/B]
00:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
        Subsystem: VIA Technologies, Inc. P4M900 Host Bridge
        Flags: medium devsel
        Memory at c0000000 (32-bit, prefetchable) [disabled] [size=128M]
        Capabilities: <access denied>

00:00.1 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.5 PIC: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller (prog-if 20 [IO(X)-APIC])
        Flags: bus master, fast devsel, latency 0

00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6364
        Flags: bus master, fast devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: c9000000-c9ffffff
        Prefetchable memory behind bridge: a0000000-bfffffff
        Capabilities: <access denied>

00:02.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
        I/O behind bridge: 00005000-00006fff
        Prefetchable memory behind bridge: 00000000c8000000-00000000c87fffff
        Capabilities: <access denied>

00:03.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
        I/O behind bridge: 00007000-00008fff
        Memory behind bridge: ca800000-caffffff
        Prefetchable memory behind bridge: 00000000c8800000-00000000c8ffffff
        Capabilities: <access denied>

00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO
])
        Subsystem: CLEVO/KAPOK Computer Unknown device 0664
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at 4cb0 [size=8]
        I/O ports at 4ca4 [size=4]
        I/O ports at 4ca8 [size=8]
        I/O ports at 4ca0 [size=4]
        I/O ports at 4c80 [size=16]
        I/O ports at 4400 [size=256]
        Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07) (prog-if 8a [M
aster SecP PriP])
        Subsystem: CLEVO/KAPOK Computer Unknown device 0664
        Flags: bus master, medium devsel, latency 32
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 4c90 [size=16]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: CLEVO/KAPOK Computer Unknown device 0664
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at 4c00 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: CLEVO/KAPOK Computer Unknown device 0664
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at 4c20 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: CLEVO/KAPOK Computer Unknown device 0664
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at 4c40 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0) (prog-if 00 [UHCI])
        Subsystem: CLEVO/KAPOK Computer Unknown device 0664
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at 4c60 [size=32]
        Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
        Subsystem: CLEVO/KAPOK Computer Unknown device 0664
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at cb400000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
        Subsystem: CLEVO/KAPOK Computer Unknown device 0664
        Flags: medium devsel
        Capabilities: <access denied>

00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
        Subsystem: VIA Technologies, Inc. Unknown device 337e

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
        Subsystem: CLEVO/KAPOK Computer Unknown device 0664
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at 4800 [size=256]
        Memory at cb400400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        Memory behind bridge: cb000000-cb0fffff
        Capabilities: <access denied>

00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
        Memory behind bridge: cb100000-cb1fffff
        Capabilities: <access denied>

01:00.0 VGA compatible controller: VIA Technologies, Inc. Unknown device 3371 (rev 01) (prog-if 00 [VGA])
        Subsystem: CLEVO/KAPOK Computer Unknown device 0664
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 9
        Memory at a0000000 (32-bit, prefetchable) [size=512M]
        Memory at c9000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>

06:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
        Subsystem: VIA Technologies, Inc. VIA High Definition Audio Controller
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at cb000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

07:04.0 FLASH memory: ENE Technology Inc Unknown device 0730
        Subsystem: CLEVO/KAPOK Computer Unknown device 0664
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at cb100200 (32-bit, non-prefetchable) [size=128]
        Capabilities: <access denied>


07:04.1 Generic system peripheral [0805]: ENE Technology Inc Unknown device 0750 (prog-if 01)
        Subsystem: CLEVO/KAPOK Computer Unknown device 0664
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at cb100000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

07:04.3 FLASH memory: ENE Technology Inc Unknown device 0751
        Subsystem: CLEVO/KAPOK Computer Unknown device 0664
        Flags: bus master, medium devsel, latency 0, IRQ 17
        Memory at cb100100 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

Hope you can make more sense of this than me.
Cheers

---

### Post by carusoswi on 2007-06-16
> **ayenack said:**
> Can you give me the model of the Clevo i.e. M72S or M540N. Need to find out what wireless card you have on board and if there's a driver for it.

Also try this in terminal:
**iwconfig**

I'm sure you know this but anyway, it's a good idea not to try to configure your wireless card/network while you have your wired connection running so if you had your wired connection running while you configured you wireless this may be the problem.

ayenack.

I am curious what sort of problems this might cause.  I configured my wireless when my wired connection was running - I needed internet connection to download wrapper, although, if I had been warned to disable the wired connection during wireless configuration, I probalby could have managed it.

My wireless has only ever worked perfectly once - and that Ubuntu 7.04 installation, unfortunately, had to be overwritten with a fresh install.  Now, try as I might, I can reliably configure my wireless to function, but, it is never detected as present in the Admin->Windows Wireless Drivers dialog.

It's a minor thing, but, I know it "ain't" right.

Caruso

---

### Post by Buster95 on 2007-06-16
> **carusoswi said:**
> I am curious what sort of problems this might cause.  I configured my wireless when my wired connection was running - I needed internet connection to download wrapper, although, if I had been warned to disable the wired connection during wireless configuration, I probalby could have managed it.

My wireless has only ever worked perfectly once - and that Ubuntu 7.04 installation, unfortunately, had to be overwritten with a fresh install.  Now, try as I might, I can reliably configure my wireless to function, but, it is never detected as present in the Admin->Windows Wireless Drivers dialog.

It's a minor thing, but, I know it "ain't" right.

Caruso

Hello Caruso,

I have tried disabling the ethernet in order to make the wireless work, but - no cigar!
When I was running with Edgy, I had ethernet and wireless connections enabled all the time. The wireless worked OK and when I plugged the ethernet in, it "switched" over to that. I know that's what was happening, because the download rate would immediately increase.

However, with Feisty, nothing I've tried has got wireless up.
Cheers

---

### Post by ayenack on 2007-06-16
Not much help really. The section bellow is obviously your Ethernet Controller.

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
Subsystem: CLEVO/KAPOK Computer Unknown device 0664
Flags: bus master, medium devsel, latency 32, IRQ 21
I/O ports at 4800 [size=256]
Memory at cb400400 (32-bit, non-prefetchable) [size=256]
Capabilities: <access denied>

Think this might be your wireless.

07:04.1 Generic system peripheral [0805]: ENE Technology Inc Unknown device 0750 (prog-if 01)
Subsystem: CLEVO/KAPOK Computer Unknown device 0664
Flags: bus master, medium devsel, latency 32, IRQ 22
Memory at cb100000 (32-bit, non-prefetchable) [size=256]
Capabilities: <access denied>

You could try deleting the wmaster0 entry from your config but I think it will just come back up next time you reboot. Try it and see.

[email]support@clevo.com.tw[/email] Might want to try this as well.

---

### Post by carusoswi on 2007-06-17
> **Buster95 said:**
> Hello Caruso,

I have tried disabling the ethernet in order to make the wireless work, but - no cigar!
When I was running with Edgy, I had ethernet and wireless connections enabled all the time. The wireless worked OK and when I plugged the ethernet in, it "switched" over to that. I know that's what was happening, because the download rate would immediately increase.

However, with Feisty, nothing I've tried has got wireless up.
Cheers

Have you tried Automatix2 to install your NDIS Wrapper?  I know there is some push back on this board against Automatix, but, it worked well for me (except that my wireless isn't showing up as present as I mentioned in my previous post.  Until I tried Automatix, nothing else I tried (and believe me, I tried a number of good, well-intentioned suggestions) worked.

I don't really care that my wireless doesn't show up in that dialog box.  At least I know I can take my computer to a location where there is no wired connection and get my wireless to respond to any open router, and I can do that reliably every time using the iwconfig command.

I hope the OP has tried 

sudo iwconfig wlan0 ESSID 'routername' 

to get his/her wireless adapter to associate with the router.

For some reason, using System --> Administration --> Network to associate the router does not always work for me.  Again, I don't know why that is, but, it doesn't matter as long as I have a reliable work around.

Caruso

---

### Post by Buster95 on 2007-06-21
> **carusoswi said:**
> Have you tried Automatix2 to install your NDIS Wrapper?  I know there is some push back on this board against Automatix, but, it worked well for me (except that my wireless isn't showing up as present as I mentioned in my previous post.  Until I tried Automatix, nothing else I tried (and believe me, I tried a number of good, well-intentioned suggestions) worked.

I don't really care that my wireless doesn't show up in that dialog box.  At least I know I can take my computer to a location where there is no wired connection and get my wireless to respond to any open router, and I can do that reliably every time using the iwconfig command.

I hope the OP has tried 

sudo iwconfig wlan0 ESSID 'routername' 

to get his/her wireless adapter to associate with the router.

For some reason, using System --> Administration --> Network to associate the router does not always work for me.  Again, I don't know why that is, but, it doesn't matter as long as I have a reliable work around.

Caruso

Hello again,
I haven't used ndiswrapper yet. I was trying to exhaust all other options first.

Curiously I have three laptops that I want to use with this wireless router:
No 1 uses Feisty 7.04. It can't see the router, either with system/admin/network or via the termina or via WiFiRadar (which I tried when all else failed).
No 2 uses Apple MacOS. It can't see the router.
No 3 uses Microsoft XP. It found the router immediately and works flawlessly.

I tried them all with the router WEP enabled and disabled, without noticable difference.

I am, to say the least, very, very puzzled.

Cheers

---

### Post by ayenack on 2007-06-21
Hey Buster95. That MS Monopoly for you.

I have just had three of the worst working days of my life. On Tuesday night as bad luck would have it our N.A.S. went down in a big way. I've been having fun and games trying to restore it to it's previous glory since, but that's of the point.

Did you ever find out what card you've got inside your lappy? 
Because it's not worth trying ndiswrapper unless you know what card you have. You will also need the right drivers for it to work with ndiswrapper. And that's not a guarantee that it'll work. ndiswrapper can be quite tricky to use. 

Like I said before if you have MS XP or any other MS OS on the lappy you can go to Control_Panel>System>Devices and look for your wireless there double click on it and it'll bring up the card and the driver version.

If you haven't got MS on there then can you remember what drivers it used on Edgy?

A thought occurs to me if you have the drivers already on disk or otherwise you should be able to work out what chip set you have. If so post them and we'll see what we can do.

L8R's. ayenack.

P.S. > sudo iwconfig wlan0 ESSID 'routername'  have a feeling that this will bring up an error as the wlan0 is not there.

PPS Automatix2 Rocks makes life very easy on a standard desktop but can sometimes cause serious problems.

---

### Post by Buster95 on 2007-06-21
> **ayenack said:**
> Hey Buster95. That MS Monopoly for you.

I have just had three of the worst working days of my life. On Tuesday night as bad luck would have it our N.A.S. went down in a big way. I've been having fun and games trying to restore it to it's previous glory since, but that's of the point.

Did you ever find out what card you've got inside your lappy? 
Because it's not worth trying ndiswrapper unless you know what card you have. You will also need the right drivers for it to work with ndiswrapper. And that's not a guarantee that it'll work. ndiswrapper can be quite tricky to use. 

Like I said before if you have MS XP or any other MS OS on the lappy you can go to Control_Panel>System>Devices and look for your wireless there double click on it and it'll bring up the card and the driver version.

If you haven't got MS on there then can you remember what drivers it used on Edgy?

A thought occurs to me if you have the drivers already on disk or otherwise you should be able to work out what chip set you have. If so post them and we'll see what we can do.

L8R's. ayenack.

P.S.  have a feeling that this will bring up an error as the wlan0 is not there.

PPS Automatix2 Rocks makes life very easy on a standard desktop but can sometimes cause serious problems.

Hello ayenack,
Pleasing to hear that some other poor sod is having as bad a day as me! I don't feel so alone.

I have sent requests for identification of the chipset, to the addresses you suggested. Haven't received a reply.
However, you have given me an idea. To quote the great thinker Baldrick "I have a cunning plan!".

I am going to borrow a copy of XP, load it up (Yes - I know. It will wipe out my Feisty), get it to tell me what chipset I'm using, then load feisty back in and start again. When I do that I will report back for further guidance. I don't want to use ndiswrapper until I have exhausted all options.

Cheers

---

### Post by ayenack on 2007-06-22
Quick suggestion that might work maybe even a *cunning plan*. When you had Edgy on your laptop wireless worked so if I were you I'd install Edgy again and ugrade to Feisty via System>Administration>Update_Manager then at the top of the Update Manager window there's a option to Upgrade click on it and it's entirely possible that your wireless will work after the upgrade. Worth a try I think.
If you try this after you install Edgy use Update Manager to install all updates before you actually upgrade to Feisty.

Best of luck. ayenack.

---

### Post by Buster95 on 2007-06-23
> **ayenack said:**
> Quick suggestion that might work maybe even a *cunning plan*. When you had Edgy on your laptop wireless worked so if I were you I'd install Edgy again and ugrade to Feisty via System>Administration>Update_Manager then at the top of the Update Manager window there's a option to Upgrade click on it and it's entirely possible that your wireless will work after the upgrade. Worth a try I think.
If you try this after you install Edgy use Update Manager to install all updates before you actually upgrade to Feisty.

Best of luck. ayenack.

Hello ayenack,
Haven't tried your suggestion yet, but have now identified the wireless card as Realtek rtl8187 802.11b+

From searching the forum, it seems that this card should work "out of the box", except for me of course.
Checked the Realtek website, found that they have a Linux driver, newer than the one in my machine. Downloaded the tarball and untarred it, but am lost about where to go next.
I don't know how to remove the old driver and associate the new driver.
Any clues?

Also, now that I know the card, I searched for it with lsmod |grep 8187 and returned
rtl8187                34944       0
mac80211         175364       2     rc80211_simple, rtl8187
eeprom_93cx6      4352       1     rtl8187
usbcore             134280       6     rtl8187, usb_storage, libusual, ehci_hcd, uhci_hcd

I think that the first line is telling me that rtl8187 is loaded. The second line seems to be related to mac addressing. The third line is some undecipherable kernel magic and the last line seems to say that it's usb mounted.

So, that might explain why it can't be seen with lspci.

I then try lsusb and return three devices, one of which is:
Bus 005      Device 004:    ID 0bda:8187 Realtek Semiconductor Corp.

Now I'm baffled again. The driver is seen by the system but doesn't wake up.

Any ideas?

---

### Post by ayenack on 2007-06-25
You already have the drivers, the ones you down loaded for the M660SE where you turned a blind eye to the missing digit. The third line is the EEPROM (Electricaly Eraseable Programable Read Only Memory) which is sort of like BIOS for your wireless card you get it on Memory and all sorts of other devices. 

I think I know what's wrong, but am not sure, you can try this at your own risk. First type this in terminal.

**sudo gedit /etc/network/interfaces**
Delete the stuff in red bold. Save. Exit. Restart your lappy. After restart make sure that they have not come back up by re-typing the above command and having a look.

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

[COLOR="Red"][B]auto wlan0
iface wlan0 inet dhcp
wireless-essid NETGEAR
wireless-key [deleted}

auto wmaster0
iface wmaster0 inet dhcp
wireless-essid NETGEAR
wireless-key {deleted}[/B][/COLOR]

After restart type this in terminal. One line at a time.

[B]sudo -i

apt-get install build-essential

apt-get install module-assistant

module-assistant-prepare

apt-get install subversion

svn co [https://rtl-wifi.svn.sourceforge.net/svnroot/rtl-wifi](https://rtl-wifi.svn.sourceforge.net/svnroot/rtl-wifi) rtl-wifi[/B]

Restart your system. Don't forget to unplug your wired network before you set up your wireless.

If Subversion doesn't work use this: [http://www.hauke-m.de/fileadmin/rtl-wifi/rtl-wifi-20070221.tar.bz2](http://www.hauke-m.de/fileadmin/rtl-wifi/rtl-wifi-20070221.tar.bz2) (rev. 52)

System>Administration>Netowork and configure your wireless to see if it works.
That's it. The driver above may not work there's also another driver which we'll try if this  one will not work.

Good luck. ayenack.

---

### Post by Buster95 on 2007-06-25
> **ayenack said:**
> You already have the drivers, the ones you down loaded for the M660SE where you turned a blind eye to the missing digit. The third line is the EEPROM (Electricaly Eraseable Programable Read Only Memory) which is sort of like BIOS for your wireless card you get it on Memory and all sorts of other devices. 

I think I know what's wrong, but am not sure, you can try this at your own risk. First type this in terminal.

**sudo gedit /etc/network/interfaces**
Delete the stuff in red bold. Save. Exit. Restart your lappy. After restart make sure that they have not come back up by re-typing the above command and having a look.

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

[COLOR="Red"][B]auto wlan0
iface wlan0 inet dhcp
wireless-essid NETGEAR
wireless-key [deleted}

auto wmaster0
iface wmaster0 inet dhcp
wireless-essid NETGEAR
wireless-key {deleted}[/B][/COLOR]

After restart type this in terminal. One line at a time.

[B]sudo -i

apt-get install build-essential

apt-get install module-assistant

module-assistant-prepare

apt-get install subversion

svn co [https://rtl-wifi.svn.sourceforge.net/svnroot/rtl-wifi](https://rtl-wifi.svn.sourceforge.net/svnroot/rtl-wifi) rtl-wifi[/B]

Restart your system. Don't forget to unplug your wired network before you set up your wireless.

If Subversion doesn't work use this: [http://www.hauke-m.de/fileadmin/rtl-wifi/rtl-wifi-20070221.tar.bz2](http://www.hauke-m.de/fileadmin/rtl-wifi/rtl-wifi-20070221.tar.bz2) (rev. 52)

System>Administration>Netowork and configure your wireless to see if it works.
That's it. The driver above may not work there's also another driver which we'll try if this  one will not work.

Good luck. ayenack.

Thanks ayenack,
Followed your suggested steps very, very carefully; lots of stuff loaded up but no cigar! With the ethernet unplugged, I cannot acquire the router.

I haven't tried your suggested alternate site [www.hauke](www.hauke) etc. because I wasn't sure whether you meant to insert that address into the svn command replacing the sourceforge address, or whether you are suggesting that I navigate to that site and download the driver.

Cheers

---

### Post by ayenack on 2007-06-26
Try this, then try your network setup again.

ifconfig up

---

### Post by ayenack on 2007-06-26
If the above didn't work take a look at the site bellow. It seems that the drivers have to be built with the make command. I thought that the drivers were already built but they may not be.

I have just found a very good [site]("http://rtl-wifi.sourceforge.net/wiki/Installing") that should take you through the complete process of installing and making the driver for your card.  Hope this works this time.:rolleyes:

Good luck.

If you need any help with instructions on this page (where the driver directory is) post back and I'll do what I can.

---

### Post by Buster95 on 2007-06-27
> **ayenack said:**
> If the above didn't work take a look at the site bellow. It seems that the drivers have to be built with the make command. I thought that the drivers were already built but they may not be.

I have just found a very good [site]("http://rtl-wifi.sourceforge.net/wiki/Installing") that should take you through the complete process of installing and making the driver for your card.  Hope this works this time.:rolleyes:

Good luck.

If you need any help with instructions on this page (where the driver directory is) post back and I'll do what I can.

Thanks ayenack for your perseverence,
I had a quick look at the site you directed me to. I looks simple enough even for a neanderthal like me. I'll try it when I get home.
Cheers

---

### Post by ayenack on 2007-06-27
Give **ifconfig up** a go before you re-install drivers. Think the drivers may be sleeping. Worth a try.

ayenack.

---

### Post by Buster95 on 2007-06-28
> **Buster95 said:**
> Hello again,
I haven't used ndiswrapper yet. I was trying to exhaust all other options first.

Curiously I have three laptops that I want to use with this wireless router:
No 1 uses Feisty 7.04. It can't see the router, either with system/admin/network or via the termina or via WiFiRadar (which I tried when all else failed).
No 2 uses Apple MacOS. It can't see the router.
No 3 uses Microsoft XP. It found the router immediately and works flawlessly.

I tried them all with the router WEP enabled and disabled, without noticable difference.

I am, to say the least, very, very puzzled.

Cheers

Hello again Caruso,
Tried your suggested sudo iwconfig etc, etc
Regrettably, it did not result in a wireless connection.

---

### Post by Buster95 on 2007-06-28
> **ayenack said:**
> Give **ifconfig up** a go before you re-install drivers. Think the drivers may be sleeping. Worth a try.

ayenack.

Hello ayenack,
Tried ifconfig up again. It returns the message

up: error fetching interface information: device not found

Also followed up the link you directed me to. Using your instructions,
Downloaded Subversion
Downloaded rtl-wifi from sourceforge
That didn't produce a wireless connection

Downloaded the alternate
That also didn't produce a wireless connection

Tried to remove the ieee80211 stack. It wouldn't give me access.

I'm really stumbling around here. I've got more rtl8187 drivers than I know what to do with.

I've still got a driver on my desktop, that I downloaded from the Realtek site, but not sure what to do with it.

Regrettably and reluctantly, after many weeks of my own pitiful efforts and the more scholarly efforts of others such as yourself, I'm being inexorably drawn to the view that I have two clear choices: Forget wireless and stay with Ubuntu, or return to XP and put up with it's shortcomings just to get the connection. What a choice!
Cheers

---

### Post by ayenack on 2007-06-28
Well it seems as if you have finally come to the end of your tether, there's an answer to this I'm sure. To discover it is another thing. There's always ndiswrapper, if you take this route use drivers for WIN 98 not XP or 2000. The 98 drivers are more compatible.

On a different tack I really would suggest one last thing to try, I know this may seem strange and nonsensical but re-install Edgy, Update then Upgrade via Update Manager all using your wireless connection, this will take a couple of hours maybe (depends on download speed. Downloads in the region of 980MB). I think that this will work.
Don't think you've tried this but please do as I would hate to see you fall back to MS Software it's a rip-off and in my opinion comes in third out of three in the race of the major desktop OS's. 
You could just stick with Edgy for the time being. It works fine.

There have been quite a lot of post about this problem so my guess is that it'll be fixed sooner rather than later.

One last thing you could always buy a new wifi card. Check WifiDocs on these forums for a good choice. I really hate the thought of not getting this problem solved and will still try to find a solution and post back if I do. I know for sure that other people have got this card to work. The devil's in the details.

ayenack.

---

### Post by ayenack on 2007-06-28
If you're still using feisty do this.

**sudo gedit /etc/modprobe.d/blacklist**

This will bring up the file bellow. At or near the bottom of the file (the stuff I've put in red bold) comment "#" as shown on the two lines so the drivers are loaded and cross your fingers. Reboot. Try setting up wifi and using it. It's possible that this will stop your system booting, not sure but I don't think so.

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
[COLOR="Red"][B]#blacklist r818x
#blacklist r8187[/B][/COLOR]

You may need to do variations on this by un-commenting  one or the other to try to get the right driver loaded. I personally would leave the r818x un-commented to start with.  Also make a backup so if you have to use recovery mode you can just copy the old file back. If you're not in root terminal you will have to use sudo in front of these commands. Instructions bellow.

**cp /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist_backup**

To restore the file from command line.

[B]rm /etc/modprobe.d/blacklist
cp /etc/modprobe.d/blacklist_backup /etc/modprobe.d/blacklist[/B]

ayenack. Post back let me know if this works.  BTW "cp=Copy" and "rm=Remove"

---

### Post by Buster95 on 2007-06-29
> **ayenack said:**
> Well it seems as if you have finally come to the end of your tether, there's an answer to this I'm sure. To discover it is another thing. There's always ndiswrapper, if you take this route use drivers for WIN 98 not XP or 2000. The 98 drivers are more compatible.

On a different tack I really would suggest one last thing to try, I know this may seem strange and nonsensical but re-install Edgy, Update then Upgrade via Update Manager all using your wireless connection, this will take a couple of hours maybe (depends on download speed. Downloads in the region of 980MB). I think that this will work.
Don't think you've tried this but please do as I would hate to see you fall back to MS Software it's a rip-off and in my opinion comes in third out of three in the race of the major desktop OS's. 
You could just stick with Edgy for the time being. It works fine.

There have been quite a lot of post about this problem so my guess is that it'll be fixed sooner rather than later.

One last thing you could always buy a new wifi card. Check WifiDocs on these forums for a good choice. I really hate the thought of not getting this problem solved and will still try to find a solution and post back if I do. I know for sure that other people have got this card to work. The devil's in the details.

ayenack.

Thanks for the words of encouragement ayenack,
I will try your upgrade suggestion and ndiswrapper before I give up entirely.

I feel, as you do that this problem is fixable. I-just-can't-crack-the-puzzle.

Cheers

---

### Post by ayenack on 2007-06-29
Try the commenting out of the blacklisted drivers first. Your drivers are currently blacklisted by the OS so if you comment them out they will no longer be blacklisted and will load at boot and may work. I also now think that it's better to have both drivers commented. 
Also when you do this add an "x" to the end of your router name when setting up your wireless so that it looks like this NETGEARx in Network Settings.

Well good luck and fingers crossed.

---

### Post by Buster95 on 2007-07-03
> **ayenack said:**
> Try the commenting out of the blacklisted drivers first. Your drivers are currently blacklisted by the OS so if you comment them out they will no longer be blacklisted and will load at boot and may work. I also now think that it's better to have both drivers commented. 
Also when you do this add an "x" to the end of your router name when setting up your wireless so that it looks like this NETGEARx in Network Settings.

Well good luck and fingers crossed.

Thanks for the perseverence ayenack. I'll give it a go when I get home.
Cheers

---

