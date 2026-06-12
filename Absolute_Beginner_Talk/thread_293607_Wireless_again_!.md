---
title: "Wireless again !"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by ronnie_dk on 2006-11-05
Hi there.
I have been around quite some distros now and ended up here.. :) 
I have Downloaded ISO and made the CD. Booted up and instaled *edgy*..
Reboot OK, but no wireless connection. Just as in all other posts i have read, there are lots of issues getting wireless-network connected internal or external. Nothing in the distros to make it work without trying and trying again with different approaches read on forum this and forum that, to make it work for a noob like me.. 
Actually I have different Wireless cards. A Linksys WPC54G version 3 Cardbus, and one internal ipw2200 card and none of them worked out of the box.. :( 
I'm trying the install on an Acer Travelmate 4102 WLMI Laptop.
I an not a Linux Guru at all, but the wireless networking has been available for a while now , but still only Wired support out of the box.. Why is it so?
I love playing around with alternatives to M$, but there must be a way to make wireless work the first time. Also including WPA-PSK TKIP which is standard on M$ machines today, why not on Ubuntu-Linux?
Is there anyone who can tell a noob like me and people in my situation howto make Wireless-networking work? 
I have read through a lot of posts here in this forum, but none of the suggestions will make my WPC54G card function properly.
I have tried a post saying that I have to use Windowsdriver bcmwl5.sys and inf file LSBCMNDS.inf edit some files to block automatic hardware recognition of Linksyscard >caused by faulty detection or why I don't know<  install Ndiswrapper and so on... Not working here . Period. Is it really that hard to recognize a cardbuscard and install the proper driver. That is really scaring me, but i love the Slogan > Linux for Human Beings < Ok then make it function for human beings.. ](*,) 
I'm really frustrated. I would love to throw my M$ partition out and format as EXT3.
Can someone >could be a Moderator< sort the different howtos eg. by release and maybe point me to a well working solution to my problem..
I know You guys are doing a great job regarding Ubuntu, but it still needs improvements.. How actually, I don't know but wireless is a major thing , just look all the postings..:D
Please help a newbe..Thanks

I have some info here:
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.



Ronnie from Denmark

---

### Post by ingo on 2006-11-06
hi ronnie,

not sure what you've been through already, but plug in your pcmcia cardbus card and send us your output from

sudo ifconfig

as well as the last few (relevant) lines of

sudo dmesg

and while you're at it you might as well let us have the benefit of your /etc/network/interfaces as well :)

---

### Post by ronnie_dk on 2006-11-06
Hi again: here is the results after fresh hdd install of 6.10 followed by reboot:

>  sudo ifconfig
Password:
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:7C:C8:65  
          inet addr:192.168.0.47  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe7c:c865/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8495 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4450 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11652254 (11.1 MiB)  TX bytes:448168 (437.6 KiB)
          Interrupt:169 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


Here result from sudo dmesg:
I Ejected and inserted the pcmcia card..just before the command was executed.

> synaptics: using relaxed packet validation
[17180244.564000] pccard: card ejected from slot 0
[17180244.624000] bcm43xx: Failed to switch to core 0
[17180244.624000] bcm43xx: Failed to switch to core 0
[17180244.624000] ACPI: PCI interrupt for device 0000:07:00.0 disabled
[17180257.088000] pccard: CardBus card inserted into slot 0
[17180257.088000] PCI: Enabling device 0000:07:00.0 (0000 -> 0002)
[17180257.088000] ACPI: PCI Interrupt 0000:07:00.0[A] -> GSI 18 (level, low) -> IRQ 185
[17180257.088000] PCI: Setting latency timer of device 0000:07:00.0 to 64


Here is interfaces:

>  sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


I took the iwconfig as well

>  sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



I surely hope this will help getting this machine going on wireless..
Thanks in advance.

---

### Post by ingo on 2006-11-06
Right, you have a broadcom card. I have no experience with them, I'm afraid. However, it is a cardbus card and recognised as eth1, an interface sadly lacking from your /etc/networking/interfaces file!

So open /etc/networking/interfaces with your favourite editor (as root, of course) and "clone" the two lines referring to eth0 and then change eth0 to eth1. Then type

sudo ifdown eth1

followed by

sudo ifup eth1

and tell us what happens

---

### Post by ronnie_dk on 2006-11-06
I Have now done this:
> p:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



Then i Did:
> 
ronnie@ronnie-laptop:~$ sudo ifdown eth1
ifdown: interface eth1 not configured
ronnie@ronnie-laptop:~$ sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:14:bf:dc:e7:18
Sending on   LPF/eth1/00:14:bf:dc:e7:18
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
send_packet: Network is down

ronnie@ronnie-laptop:~$ 


I also tried eth0 down > eth1 up same situation

for eth0 it works fine
>  sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:c0:9f:7c:c8:65
Sending on   LPF/eth0/00:c0:9f:7c:c8:65
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.47 -- renewal in 35938 seconds.
ronnie@ronnie-laptop:~$ 


Hmmm now what

---

### Post by ingo on 2006-11-07
this is your be all and end all

[http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto](http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto)

---

### Post by ronnie_dk on 2006-11-07
Hi ..
Thanks for your replies...
But seriously, du You think that reading 696 postings of different opinions howto make it work will solve my problem.?

First - it will take about a week to read it
Second - There will be no guaranty at all, that it might work at all when i have tried all of the suggestions posted

Back to basics.. no way to make a Free-PC today.. maybe in one or two years.. Come on .. There might be another way to solve this. ](*,) 
:-k  We ( Us noobs ) probably have to stick with M$ operating systems until there is better out-of-the-box support for Wireless-networking in linux or better/structured guides to make it work. Has no-one made a flowchart to follow..?
Sad- sad..](*,) 
Sorry . if there is no one else with better suggestions, i´d have to stick with wired connection, or stick with dual boot for internet connectivity and then only use ubuntu for local solitaire games.. What a challenge.

---

