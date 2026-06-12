---
title: "UBUNTU upgrade from 7.04 disables wireless interface"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by peter bromley on 2007-11-14
the system asked recently for an update to ubuntu version level which was downloaded via the wireless pci card (my only connection to the internet for this pc).

however after a restart  it seems to be confused where the wire card is but allows the encription hex codes to be set but does no see any network.

I see  there are other threads that it may be possible to revert to 7.04. I really dont want to start doing unix hacks of the o/s without a safety net !

in laymans terms , how do you do roll back the o/s ?

the o/s has been fine upto now andiven been very satisfied how stable it is. 
Its normal to allow upgrades but to if its going to trash your only communication channel to the network and the internet the it ought to warn you how to recover!

without the wireless card I'm stumped in-terms of downloads and dont want to revert to a CD.
Any helpful hints appreciated
Thanks
P:confused:

---

### Post by 1337455 10534 on 2007-11-14
Before doing a new install, try;
```

sudo apt-get update
sudo apt-get install ndiswrapper-common
sudo apt-get upgrade

```

---

### Post by jw5801 on 2007-11-14
What wireless card do you have? If you were previously using ndiswrapper, then it's possible that there is a slightly better native driver now, so the native driver and ndiswrapper may be interfering, in which case it should be as simple as blacklisting the native driver (or removing ndiswrapper). Some specs please? It shouldn't be necessary to "roll-back" to feisty, we should be able to fix the issue in gutsy.

---

### Post by 1337455 10534 on 2007-11-14
Oooh, to get some good hardware specs, try;
```

lspci
# the first letter is an undercase "L"

```
and post the results.

---

### Post by peter bromley on 2007-11-15
Hi,
this is exactly what forums are about - thanks so far..
00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:06.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M890 [Chrome9] Integrated Video (rev 11)

what's the next step ?

---

### Post by jw5801 on 2007-11-15
> **peter bromley said:**
> Hi,
this is exactly what forums are about - thanks so far..
```
00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
**00:06.0 Network controller: RaLink RT2561/RT61 rev B 802.11g**
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M890 [Chrome9] Integrated Video (rev 11)
```

what's the next step ?

Ok, the bolded line is your wireless card. There's a pretty good how-to for using it in Gutsy that you can find [here](http://www.ushills.co.uk/ubuntu/RT61.html).

---

### Post by peter bromley on 2007-11-15
thanks,
making progress although it seems a tad complicated , what happens with the next version of ubuntu do i have to patch this again ?
But failure at first step via the link above, can you offer a different site please?

The requested URL /http/website.ushills.letterboxes.org/rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz was not found on this server.

---

### Post by peter bromley on 2007-11-15
i've done some searching and i think the link should be :

[http://sourceforge.net/project/downloading.php?groupname=rt2400&filename=rt61-1.1.0-b2.tar.gz&use_mirror=dfn](http://sourceforge.net/project/downloading.php?groupname=rt2400&filename=rt61-1.1.0-b2.tar.gz&use_mirror=dfn)

please confirm before i go any further as this seems to be a generic driver tar file.

Perhaps it would help if the link was updated ?

---

### Post by backflip on 2007-11-15
I'm waiting delivery of a new card with that chipset. I was assured by email from linuxemporium.co.uk  that :-

"Additionally the card works with Ubuntu Gutsy 7.10 without the need for
any additional driver installation.
It works out of the box and can be configured with Network Manager
Thanks to a bug with the handling of ipv6 addresses it is necessary to
edit /etc/modprobe.d/blacklist and add:
     blacklist ipv6"

I hope this is relevant.

---

### Post by jw5801 on 2007-11-15
Hmm... I think the sourceforge link is correct. But the link on that page is working, just the anchor tag is behaving funny. If you copy and paste the url he has hyperlinked: [http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz) into the address you get the file he's linked.

---

### Post by peter bromley on 2007-11-15
before i go any further can you confirm that the alternatyive that BACKFLIP has just offered :

"edit /etc/modprobe.d/blacklist and add:
blacklist ipv6"

is not the solution as its a tad easier that all the config work that jw5801 suggests !

---

### Post by jw5801 on 2007-11-15
I'm not entirely sure. I don't have the same chipset myself. That alternative can't do any harm however, so you can try it. Add the entry, reboot and see if there's any difference.
It depends how far through your connection process you're getting, as to what needs to be done. Can you see any networks? If you can't see anything to start off with, then blacklisting ipv6 won't really help. If you can see networks but are failing to connect then blacklisting the module will probably do it.

From that how-to, the important part is to install the newer kernel module (driver) and blacklist the old one. Everything from the command "sudo nano /etc/network/interfaces" is manually setting up a connection, which you probably won't need to do. The gnome network manager applet should do that for you.

---

### Post by ushills on 2007-11-15
I have now corrected the link on my site.

Thanks for referencing it.

---

### Post by peter bromley on 2007-11-15
ok, managed to install tar file however the "make" failes ... and clues please ?

peter@linux-home:~/rt61-1.1.0-b2/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/peter/rt61-1.1.0-b2/Module/rtmp_main.o
/home/peter/rt61-1.1.0-b2/Module/rtmp_main.c: In function ‘RT61_open’:
/home/peter/rt61-1.1.0-b2/Module/rtmp_main.c:405: warning: ‘deprecated_irq_flag’ is deprecated (declared at include/linux/interrupt.h:66)
/home/peter/rt61-1.1.0-b2/Module/rtmp_main.c: In function ‘rt61_init_module’:
/home/peter/rt61-1.1.0-b2/Module/rtmp_main.c:1044: warning: implicit declaration of function ‘pci_module_init’
  CC [M]  /home/peter/rt61-1.1.0-b2/Module/mlme.o
/home/peter/rt61-1.1.0-b2/Module/mlme.c: In function ‘MlmeEnqueueForRecv’:
/home/peter/rt61-1.1.0-b2/Module/mlme.c:3297: warning: format ‘%ld’ expects type ‘long int’, but argument 2 has type ‘size_t’
  CC [M]  /home/peter/rt61-1.1.0-b2/Module/connect.o
  CC [M]  /home/peter/rt61-1.1.0-b2/Module/sync.o
  CC [M]  /home/peter/rt61-1.1.0-b2/Module/assoc.o
  CC [M]  /home/peter/rt61-1.1.0-b2/Module/auth.o
  CC [M]  /home/peter/rt61-1.1.0-b2/Module/auth_rsp.o
  CC [M]  /home/peter/rt61-1.1.0-b2/Module/rtmp_data.o
/home/peter/rt61-1.1.0-b2/Module/rtmp_data.c: In function ‘RTMPHandleRxDoneInterrupt’:
/home/peter/rt61-1.1.0-b2/Module/rtmp_data.c:477: error: ‘struct sk_buff’ has no member named ‘mac’
/home/peter/rt61-1.1.0-b2/Module/rtmp_data.c: In function ‘RTMPCheckDHCPFrame’:
/home/peter/rt61-1.1.0-b2/Module/rtmp_data.c:4318: warning: unused variable ‘dest_port’
/home/peter/rt61-1.1.0-b2/Module/rtmp_data.c:4317: warning: unused variable ‘is_udp’
/home/peter/rt61-1.1.0-b2/Module/rtmp_data.c:4316: warning: unused variable ‘is_ipv4’
/home/peter/rt61-1.1.0-b2/Module/rtmp_data.c:4315: warning: unused variable ‘is_ip’
make[2]: *** [/home/peter/rt61-1.1.0-b2/Module/rtmp_data.o] Error 1
make[1]: *** [_module_/home/peter/rt61-1.1.0-b2/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
rt61.ko failed to build!
make: *** [module] Error 1
:confused:

---

### Post by jw5801 on 2007-11-15
Ah. You need the build-essential package (tools to compile code). If you have a wired internet connection run "sudo apt-get install build-essential." Otherwise, if you have a Gutsy install CD put it in and run ```
sudo apt-cd add
sudo apt-get install build-essential
```Or finally use a machine that does have a connection to get the debs from [here](http://packages.ubuntu.com/gutsy/devel/build-essential). You'll also need to get all the debs listed there as dependencies (dpkg-dev, g++, gcc, etc.). Put them all in the one folder on your Ubuntu machine and run ```
cd *folder/containing/debs/* #replace this with wherever they are.
sudo dpkg -i *.deb
```
Then try to run "make" again.

---

### Post by peter bromley on 2007-11-25
To JB5801:
the first command you suggested (i suppose to mount the cd volume) fails:

sudo apt-cd add
i then get:
sudo: apt-cd: command not found 

this is taking far to long to resolve , can i rollback the version of Ubuntu without having to e-install from the iso disc i built?

Whats next ? i don't have a gutsy install disc as you suggested.

do i have to backup all my files before rolling back or is it a nice clean system that leaves user data alone ?

more help needed please and no i don't have direct wired connections easily at hand to do any downloads !

---

### Post by peter bromley on 2008-01-06
i've still got the problem after doing all the make's etc.
I used the following link : 
[http://www.ushills.co.uk/ubuntu/RT61.html](http://www.ushills.co.uk/ubuntu/RT61.html)
and when i got to the step to restart in interfaces i got :

peter@linux-home:~$ sudo /etc/init.d/networking restart
[sudo] password for peter:
 * Reconfiguring network interfaces...                                           * Stopping the Firestarter firewall...
ra0: error fetching interface information: Device not found
ra0: error fetching interface information: Device not found
ra0: error fetching interface information: Device not found
   ...done.
 * Starting the Firestarter firewall...
ra0: error fetching interface information: Device not found
ra0: error fetching interface information: Device not found
ra0: error fetching interface information: Device not found
   ...fail!
run-parts: /etc/network/if-down.d/50firestarter exited with return code 2
There is already a pid file /var/run/dhclient.eth0.pid with pid 4054
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:15:58:6d:d5:d6
Sending on   LPF/eth0/00:15:58:6d:d5:d6
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
Ignoring unknown interface eth1=eth1.
Ignoring unknown interface eth2=eth2.
Ignoring unknown interface ath0=ath0.
Ignoring unknown interface ra0=ra0.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:15:58:6d:d5:d6
Sending on   LPF/eth0/00:15:58:6d:d5:d6
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.149 -- renewal in 274 seconds.
 * Stopping the Firestarter firewall...
ra0: error fetching interface information: Device not found
ra0: error fetching interface information: Device not found
ra0: error fetching interface information: Device not found
   ...done.
 * Starting the Firestarter firewall...
ra0: error fetching interface information: Device not found
ra0: error fetching interface information: Device not found
ra0: error fetching interface information: Device not found
   ...fail!
run-parts: /etc/network/if-up.d/50firestarter exited with return code 2
                                                                         [ OK ]
peter@linux-home:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

Any suggestions please ?
This has gone on far too long .. fortunately i can occasionally connect the wired route but its a pain not having the wireless as this all worked with the last release of Linux...
Peter

---

### Post by ushills on 2008-04-08
Please note link update for this guide

[http://www.ushills.co.uk/2008/01/rt61-wireless-card-in-gutsy.html]("http://www.ushills.co.uk/2008/01/rt61-wireless-card-in-gutsy.html")

---

