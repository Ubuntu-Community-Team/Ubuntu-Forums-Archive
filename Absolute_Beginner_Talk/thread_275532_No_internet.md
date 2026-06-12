---
title: "No internet"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by neosurrealist on 2006-10-11
Hi, I'm a newbie to Ubuntu! 
I'm using Xubuntu to replace Microspot Widows on my wife's computer.
if you catch my drift.

I just installed it earlier today, and there is no internet connection and therefore no way to get updates onto it.

Does anyone have suggestions to Troubleshooting?
Please spell it out for me, because I'm native to MacOS.
Thanks in advance.
-CJDKL

---

### Post by arochester on 2006-10-11
How did you used to connect to the internet? Dial-up? ISDN? DSL? USB? Cable?

Did you used to connect by typing a username and password?

---

### Post by neosurrealist on 2006-10-11
Cable. I've tried powercycling the router etc.

---

### Post by scot524 on 2006-10-11
How are you connected to the router on the LAN side? Wired or wireless? Does the router run a DHCP server or do you use static IP's? The latter is not common in home networks, but I have to ask. Wireless can be tricky especially with the USB adaptors. If you open system --> administration --> networking what is the status of your network adaptor(s)

---

### Post by neosurrealist on 2006-10-11
The computer is plugged into a wireless router, but does not connect wirelessly. I use DHCP to connect wirelessly with a password.
 the status is active.

---

### Post by Arevos on 2006-10-11
Do you know the IP address of your router? Does your router have an administration page you can reach through a browser? Do you know if Ubuntu has successfully recognised your network card?

---

### Post by Quintin Riis on 2006-10-11
Open a terminal, and paste the output of 'ifconfig'.

Applications > Accessories > Terminal

---

### Post by neosurrealist on 2006-10-11
I don't know if it has beeen successfully recognised. but it appears that way. I don't know what the router's ip is. I was in it to set up my wireless, but I have not been into it ever since. I know other versions of linux like vectorlinux can connect to the internet.
the weird part was that it connected at one point to get updates, then disconnected after downloading one.
I'm assuming that it is connecting somewhat.
-CJDKL

---

### Post by dannyboy79 on 2006-10-11
> **Quintin Riis said:**
> Open a terminal, and paste the output of 'ifconfig'.

Applications > Accessories > Terminal

also, paste lspci -v so we can see which ethernet controller your computer uses. some laptops are funny. and you may need to load a module or driver, maybe. or it could be the infamous ipv6 issue. you can disable or enable it in firefox browser by typing about:config I think. gogle ipv6 disable in firefox and you should find the solution. or if you have internet and then lose it and you;re using dhcp it is most likely a dns issue where the dhcpclient or whatever ends up overwriting your resolv.conf when the computer restarts, there is a solution for that also. it is in here somewhere, it has something to do with making the resolv.conf read only. Good luck and post that stuff and you'll be helped pretty quickly. GOD I love helping people and I am actually a linux newbie. i tried ubuntu about 6 months ago and this is first linux experience and i am in love so i just hang around the forums and help everyone with things that I figured out in my ubuntu journey. i run xubuntu and ubuntu. x is on an old laptop Pentium MMX 266mhz with 128mg ram.

---

### Post by dannyboy79 on 2006-10-11
> **neosurrealist said:**
> I don't know if it has beeen successfully recognised. but it appears that way. I don't know what the router's ip is. I was in it to set up my wireless, but I have not been into it ever since. I know other versions of linux like vectorlinux can connect to the internet.
the weird part was that it connected at one point to get updates, then disconnected after downloading one.
I'm assuming that it is connecting somewhat.
-CJDKL

I hate to be assertive but if you want our help, an answer like, I don't know, isn't gonna allow us to help you. If we ask for output then give it to us otherwise we can't help you.

---

### Post by Quintin Riis on 2006-10-11
Also might do a 
```
echo 4.2.2.2 >> /etc/resolv.conf
```

---

### Post by dannyboy79 on 2006-10-11
> **Quintin Riis said:**
> Also might do a 
```
echo 4.2.2.2 >> /etc/resolv.conf
```

is that what the exact fix is for the resolv.conf getting overwritten by dhcp upon reboot? I thought it had something to do with making the resolv.conf file read only using chmod. That is only what I thought because of thinking that I read that somewhere. i have never needed to do this to my resolv.conf due to all my boxes having static ip's. anyway, glad to know cause I am going to be putting together a post very soon about every single thing to check when having internet issues as this sugject comes up WAY to much in these forums and the answers are everywhere and not just in 1 place!

---

### Post by Quintin Riis on 2006-10-11
> **dannyboy79 said:**
> is that what the exact fix is for the resolv.conf getting overwritten by dhcp upon reboot? I thought it had something to do with making the resolv.conf file read only using chmod. That is only what I thought because of thinking that I read that somewhere. i have never needed to do this to my resolv.conf due to all my boxes having static ip's. anyway, glad to know cause I am going to be putting together a post very soon about every single thing to check when having internet issues as this sugject comes up WAY to much in these forums and the answers are everywhere and not just in 1 place!
>> redirects shell output and appends to a file.  If you don't want it to be overwritten, make it read-only or search the forum for /etc/resolv.conf to find out how to prepend lines when it is generated.

Might try sudo nano /etc/dhcp3/dhclient.conf and look for prepend domain-name-servers.

4.2.2.2 is a military DNS server that can generally be expected to be online.  I add it to all machines in case a grunt cuts some fibre that doesn't look important and borks DNS for my ISP in the tristate area for four hours.

---

### Post by mahy on 2006-10-11
So you've got a wireless connection to your router...

The easiest way is to install network-manager-gnome (for Gnome) or knetworkmanager (for KDE), but there's nothing that easy-to-use i know of for Xfce... :(

Anyway, you said you connect "with password", IIRC. Do you know if it's WPA or WEP encryption? If it's WPA, you can follow this howto

[https://wiki.ubuntu.com/WifiDocs/WPAHowTo?action=show&redirect=WPAHowto](https://wiki.ubuntu.com/WifiDocs/WPAHowTo?action=show&redirect=WPAHowto)

If it's WEP, then change it to WPA (from windows) and then follow this howto. :D (just kiddin', i'm not forcing you, but it's the best you can do)

All the above mentioned builds on the fact that your machine's wifi adapter is working alrite under linux. To check it, type "iwlist scanning" into terminal and you should see info about all available access points.

---

### Post by dannyboy79 on 2006-10-11
> **mahy said:**
> So you've got a wireless connection to your router...

The easiest way is to install network-manager-gnome (for Gnome) or knetworkmanager (for KDE), but there's nothing that easy-to-use i know of for Xfce... :(  

There is always wifi-radar. I have used it on my laptop that runs xubuntu and it worked really well!!! I have recently tried out edgy and then sense i had major usb mouse issues i went back to dapper and just haven't reinstalled wi-fi radar because i just used the installer to enter my wep key so i don't need wifi-radar. i suppose if i took my latop to various places i would you it because wifi-radar keeps trrack of all your various wireless connection locations and their settings.!

I believe that he said he is connecting to a wireless router but he is using a ethernet cord.

---

### Post by neosurrealist on 2006-10-11
**ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:08:A1:14:4F:EC
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe14:4fec/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:319 dropped:0 overruns:0 frame:0
          TX packets:7 errors:10 dropped:0 overruns:0 carrier:10
          collisions:0 txqueuelen:1000
          RX bytes:2094 (2.0 KiB)  TX bytes:510 (510.0 b)
          Interrupt:177 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)

**lspci -v**

0000:00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
        Subsystem: Dell: Unknown device 0127
        Flags: bus master, fast devsel, latency 0
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01) (prog-if 00 [VGA])
        Subsystem: Dell: Unknown device 0127
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Memory at ff680000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 0127
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at ff80 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 0127
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at ff60 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 0127
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at ff40 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Dell: Unknown device 0127
        Flags: bus master, medium devsel, latency 0, IRQ 193
        Memory at ffa00800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: ff800000-ff9fffff
        Prefetchable memory behind bridge: 10000000-100fffff

0000:00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell: Unknown device 0127
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at ffa0 [size=16]
        Memory at 10100000 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
        Subsystem: Dell: Unknown device 0127
        Flags: medium devsel, IRQ 11
        I/O ports at dc80 [size=32]

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Dell: Unknown device 0127
        Flags: bus master, medium devsel, latency 0, IRQ 201
        I/O ports at d800 [size=256]
        I/O ports at dc40 [size=64]
        Memory at ffa00400 (32-bit, non-prefetchable) [size=512]
        Memory at ffa00000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:01:07.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
        Subsystem: Unknown device 4554:434e
        Flags: bus master, medium devsel, latency 64, IRQ 177
        I/O ports at ec00 [size=256]
        Memory at ff8ffc00 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at 10000000 [disabled] [size=256K]
        Capabilities: <available only to root>

0000:01:08.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
        Subsystem: GVC Corporation: Unknown device 0212
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at ff8e0000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at e8f8 [size=8]
        Capabilities: <available only to root>

---

### Post by neosurrealist on 2006-10-11
thanks for your patience, I dont have a floppy drive on my iMac. Hard to transfer files. I just had to run to the store to get a pendrive.

---

### Post by dannyboy79 on 2006-10-11
> **neosurrealist said:**
> **ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:08:A1:14:4F:EC
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:a1ff:fe14:4fec/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:319 dropped:0 overruns:0 frame:0
          TX packets:7 errors:10 dropped:0 overruns:0 carrier:10
          collisions:0 txqueuelen:1000
          RX bytes:2094 (2.0 KiB)  TX bytes:510 (510.0 b)
          Interrupt:177 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)

**lspci -v**

0000:00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
        Subsystem: Dell: Unknown device 0127
        Flags: bus master, fast devsel, latency 0
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01) (prog-if 00 [VGA])
        Subsystem: Dell: Unknown device 0127
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Memory at ff680000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 0127
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at ff80 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 0127
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at ff60 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 0127
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at ff40 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Dell: Unknown device 0127
        Flags: bus master, medium devsel, latency 0, IRQ 193
        Memory at ffa00800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: ff800000-ff9fffff
        Prefetchable memory behind bridge: 10000000-100fffff

0000:00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell: Unknown device 0127
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at ffa0 [size=16]
        Memory at 10100000 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
        Subsystem: Dell: Unknown device 0127
        Flags: medium devsel, IRQ 11
        I/O ports at dc80 [size=32]

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Dell: Unknown device 0127
        Flags: bus master, medium devsel, latency 0, IRQ 201
        I/O ports at d800 [size=256]
        I/O ports at dc40 [size=64]
        Memory at ffa00400 (32-bit, non-prefetchable) [size=512]
        Memory at ffa00000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:01:07.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
        Subsystem: Unknown device 4554:434e
        Flags: bus master, medium devsel, latency 64, IRQ 177
        I/O ports at ec00 [size=256]
        Memory at ff8ffc00 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at 10000000 [disabled] [size=256K]
        Capabilities: <available only to root>

0000:01:08.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
        Subsystem: GVC Corporation: Unknown device 0212
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at ff8e0000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at e8f8 [size=8]
        Capabilities: <available only to root>

It appears you are are getting an ip address from your router assuming your routers ip is 192.168.0.1. so that just leaves the dns problems with your dns servers getting over written when you reboot cause you probably have dhcp and then the other issue woiuld be ipv6, you'll want to try to disable it using firefox and about:config. there are plenty of posts about internet connection failing, if I werre you I would check them out because sense you are getting an ip I couldn't help you anymore.

---

### Post by Quintin Riis on 2006-10-11
Type 'route' in a terminal.  Try pinging the gateway.  Use ^C (ctrl+c) to quit ping.  If this is successful, then do the following.
```
% sudo echo '4.2.2.2' >> /etc/resolv.conf
```Then try to browse the web.

dannyboy79, please try not to quote very long posts when unnecessary.

---

### Post by dannyboy79 on 2006-10-12
> **Quintin Riis said:**
> Type 'route' in a terminal.  Try pinging the gateway.  Use ^C (ctrl+c) to quit ping.  If this is successful, then do the following.
```
% sudo echo '4.2.2.2' >> /etc/resolv.conf
```Then try to browse the web.

dannyboy79, please try not to quote very long posts when unnecessary.

Gotcha, it's kind of a bad habit to automatically hit the quote button when helping people. I'll be more carefull.

---

### Post by TiredBird on 2006-10-14
I don't understand all that technical stuff but I use 'gksu network-admin' to set up my interfaces. Its the same thing as on Ubuntu. It was installed automatically when I put in Xubuntu. I don't think 'network-manager' is necessary.

---

