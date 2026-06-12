---
title: "Impressed - but no Internet!"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by v105 on 2007-05-13
Hi!

Well at last I have Ubuntu installed and what a difference to what I thought was an old sluggish AMD 3GHz.  It flies now.  I am still getting used to where everything is and back on my laptop at the moment with XP.  I nearly fell off my chair as it had kept all my old JPG and MP3 files on the HD.  I had backed them up on DVD just incase.

The main problem seems to be that the computer refuses to connect to the router.  It's a Netgear DG834G on ADSL.  I am using it now via Wireless on the laptop and was using it earlier on the main PC with Windows.  

When ubuntu first switches on it says it is connected to a wired network.  The light on the router flashes away as if it is talking to the PC.  So I selected to use DHCP and thought that the router would hand out an IP number.  When it refused I selected to connect manually and put in the details for a fixed IP number -
196.168.0.5  .  That's what the PC used to be with Windows XP.  The other bits were filled in for me as 255.255.255.0 and the gateway is 192.168.0.1.   The laptop gets it's IP and was assigned 192.168.0.2 and works whichever way it is set on XP via wireless or cable.

I have checked that the access control in the router is not switched on so it will allow any MAC number to connect.  I have also switched the laptop on and off and the main PC to start them up in a different order just incase that was causing a problem.

I just can't work out what's wrong as the Network controller seems to be OK, it's an SiS type on the main motherboard.  It's recognised too.  

Anyone got any ideas?  

Tried everything I can think of and read the help files...

(I was amazed the sound and video worked first time too!)

---

### Post by FuturePast on 2007-05-13
Are you comfortable using the command line?
If so, type:
$ ifconfig -a
$ iwconfig
$ ping 192.168.0.1

and post results.

---

### Post by v105 on 2007-05-13
I hope I am typing it in the right place!  Completely new to this!

for ifconfig -a  I get this 

eth0:
Link encap:Ethernet  HWaddr  00:00:00:00:00:00
int addr:192.168.0.5   Bcast: 192.168.0.255  Mask 255.255.255.0
inet6 addr: fe80::200::rr:fe00:0/64  Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
RX Packets: 51  errors:0 dropped:0 overruns:0 carrier:0
collisions:0  txqueuelen:1000
RX bytes:9181 (8.9KiB)  TX Bytes:20972 (20.4 KiB)
Interrupt 19  Base address 0xd400

lo:
link encap: Local loopback
inet addr: 127.0.0.1  Mask 255.255.0.0
inet6 addr:  :1/128  Scope: Host
UP LOOPBACK RUNNING  MTU: 16436 Metric:1
RX Packets: 219 errors 0 dropped 0 overruns 0 frame 0
TX Packets: 219 errors 0 dropped 0 overruns 0 carrier 0
collisions 0 txqueuelen:0
RX Bytes 16752 (16.1KiB) TX Bytes 16752 (16.1KiB)


---------------------------------------------
iwconfig  gives

lo  no wireless extensions
eth0  no wireless extensions   

(my wireless card by Belkin isn't recognised anyway!)

-----------------------------------------------

ping 192.168.0.1  shows this -

OMG it's going off the screen!     

64 Bytes from 192.168.0.1  icmp seq=75 ttl=255  time=0.54s

I'll try and stop that bit now.  Just had a look at the router and the "1" light for port 1 is flashing away !

------------------------------------------------

So it seems like it knows where the router is, but not what to do with it.  I might see if I have another network card handy that I can plug in to the PCI socket inside.

Do those readings give any clue?

---

### Post by FuturePast on 2007-05-13
Yes, the fact that the ping command works, means the network card is recognised and is configured properly.

I think the problem is you need to configure the DNS (domain name server).

Type:
$ host [www.google.com](www.google.com)
and see if it returns the google IP address.

---

### Post by v105 on 2007-05-13
:lolflag: I have just thrown an old network card in and it's fired up first time - amazing!

This is where the fun begins!

---

### Post by Austin_KW on 2007-05-13
Probably DNS
What is the output from command
cat /etc/resolv.conf

For your wireless card post the output of
lspci # for PCI cards or
lsusb # For usb adapters

also 
lsmod # to list your loaded drivers

---

