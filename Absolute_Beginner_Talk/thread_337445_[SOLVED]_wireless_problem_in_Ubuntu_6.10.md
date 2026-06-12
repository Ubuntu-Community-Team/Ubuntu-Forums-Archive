---
title: "[SOLVED] wireless problem in Ubuntu 6.10"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by azalamo99 on 2007-01-13
I am a newbie. After 3 days of trying to load Ubuntu 6.10 on a Dell Laptop (with no OS), I have finally succeeded. Now I am trying to set up a wireless connection using a Belkin USB Network Adapter. Although my laptop shows the adapter in the Networking window I am not able to make it work. I haven't been able to find any instructions for 6.10, everything I have found is for an older/different version. I think I have tried everything I have read in the Community Docs, but still no resolution :(  Any help will be appreciated.

---

### Post by compwiz18 on 2007-01-13
Can you run:

```

sudo lspci
sudo iwlist scan
sudo iwconfig
sudo ifconfig -a

```

and post the output?  thank you
([how to use the terminal - just in case ;)]("http://psychocats.net/ubuntu/terminal"))

---

### Post by Atomic Dog on 2007-01-13
[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)

---

### Post by azalamo99 on 2007-01-13
> **compwiz18 said:**
> Can you run:

```

sudo lspci
sudo iwlist scan
sudo iwconfig
sudo ifconfig -a

```

and post the output?  thank you
([how to use the terminal - just in case ;)]("http://psychocats.net/ubuntu/terminal"))
sudo lspci:

00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7LW [Radeon Mobility 7500]
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420
02:01.1 CardBus bridge: Texas Instruments PCI1420


sudo iwlist scan

lo		Interface doesn't support scanning.

wmaster0	Interface doesn't support scanning : Operation not supported

wlan0		Scan completed:
		Cell 01 -	 Address: 00:0F:B3:1D:48:6D
				ESSID:"ACTIONTEC"
				Mode:Master
				Frequency:2.452 GHz
				Encryption key:off
				Extra:tsf=0000000a7120b4f3

eth0		Interface doesn't support scanning.

sit0		Interface doesn't support scanning.

--------------------------------------------------------------------------------------------

sudo iwconfig

lo		no wireless extensions.

wmaster0	IEEE 802.11g	Frequency:2.412 GHz
		RTS thr:off	Fragment thr=2346 B

wlan0		IEEE 802.11g 	ESSID:"ACTIONTEC"
		Mode:Managed	Frequency:2.214 GHz	Access Point: Not-Associated
		RTS thr:off	Fragment thr=2346 B
		Encryption key:off

eth0		no wireless extensions.

sit0		no wireless extensions.

---------------------------------------------------------------------------------------------

sudo ifconfig -aeth0      Link encap:Ethernet  HWaddr 00:0B:DB:DA:37:75  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22824 (22.2 KiB)  TX bytes:22824 (22.2 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:17:3F:49:56:A5  
          inet addr:192.168.0.5  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:fe49:56a5/64 Scope:Link
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:7522 (7.3 KiB)
          Base address:0x5000 

wmaster0  Link encap:UNSPEC  HWaddr 00-17-3F-49-56-A5-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x5000 


I hope this will help. I have a hard time making any sense out of this. Thanks for your help.

---

### Post by azalamo99 on 2007-01-13
> **Atomic Dog said:**
> [https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)
Thanks for the link, but I had already went through that one and it didn't help.

---

### Post by compwiz18 on 2007-01-13
OK, try running **sudo dhclient** but make sure no network cables are plugged in to the computer.

---

### Post by azalamo99 on 2007-01-13
Ok I ran **sudo dhclient** but not sure what I got back. The last two lines stated:
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Again, this doesn't mean anything to me. Sorry.

---

### Post by compwiz18 on 2007-01-13
This simply means that your computer didn't connect - I don't know why.  However, I would suggest you try a program such as network-manager (go to the package manager) or connection-manager (in my signature) to connect, these make it 300 times easier.

If you need help installing one, or if it doesn't work, or if you just need more help in general, ask :D

---

### Post by azalamo99 on 2007-01-14
I downloaded connection-manager-1.3.2.deb but when I tried to run it (tried both from the command line and by double-clicking on the icon) and get an error message:
[COLOR="Red"]Error: Dependency is not satisfiable: libwxgtk2.6-0[/COLOR]
[COLOR="Black"]I am beginning to see why Linux never caught on :)[/COLOR]

---

### Post by psycosmyth on 2007-01-14
USB net cards are fussy with linux, I have had issues with windows running these too so it's not a linux only problem. Pcmcia are the best way to use wireless imo. I have a Dlink wna1330 plugged in my Dell, it works natively in Ubuntu, but not in any other distro, even Debian. I had a Belkin that I used with XP but I took it back and told them I used Linux and they let me exchange it. It sounds odd but it's easier sometime to just change hardware. Hey you have thousands of free apps and OS's to use now so don't fuss over a tiny netcard, I bit the bullet and I'm glad.
I just can't try other distro without some fuss, but I love Ubuntu enough not to worry.:cool:

---

### Post by azalamo99 on 2007-01-15
Ok, I'm going on this huge learning curve. I finally learned how to find libwxgtk2.6-0 and tried to install it. That pkg required I find libwxbase2.6-0 and that pkg required I find python-wxgtk2.6_2.6.3.2.1.5 and that pkg required I find phthon-wxversion_2.6.3.2.1.5_all. Once I found and installed all these pkgs I was able to install connection-manager-1.3.2 which doesn't show up anywhere I can find and now when I try to start Networking a window pops up for a "Bug Reporting tool". Apparently I am missing something. Oh well tomorrow is another day.

---

### Post by azalamo99 on 2007-01-16
Thanks psycosmyth. I took back the USB adapter and exchanged it for a pcmcia wireless card. When I inserted it, it imediately started working.

---

