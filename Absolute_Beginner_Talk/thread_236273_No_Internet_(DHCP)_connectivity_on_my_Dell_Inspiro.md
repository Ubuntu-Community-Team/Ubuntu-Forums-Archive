---
title: "No Internet (DHCP) connectivity on my Dell Inspiron laptop"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by lkvee on 2006-08-14
I'm running xubuntu 6.06 LTS on a Dell Inspiron 7000 (P2-300 with 320 MB RAM).   I'm using an old 3Com Ethernet 10Mbps PCMCIA card (16-bit) with a 3Com 10/100 dongle.

I have configured and activated eth1 but there's still no connection.   I popped in Tom's Root Boot and got this output where "Timestamp" just listed the date and time (yeah, I typed it all out instead out redirecting output):

eth0: 3Com 3c589, io 0x300, irq 9, hw_addr 00:60:08:F4:A8:49
  8K FIFO split 5:3 Rx:Tx, auto xcvr
Timestamp cardmgr[25]: executing: './network start eth0'
Timestamp cardmgr[25]: + Starting dhcpcd--
Timestamp cardmgr[25]: + SIOCADDRT: File exists
Timestamp cardmgr[25]: +
Timestamp cardmgr[25]: + ERROR
Timestamp cardmgr[25]: +
52: Terminated

Here's the output from ifconfig (Tom's Root Boot session):

eth0

Link encap:Ethernet  HWaddr 00:60:08:F4:A8:49
inet addr:1.1.1.1  Bcast:255.255.255.255  Mask:255.0.0.0
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 frame:0
collisions:0 txqueuelen:100
RX bytes:0 (0.0 b)  TX bytes:624 (624.0 b)
Interrupt:5  Base address:0x300


lo

Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:3924  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 frame:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

The "inet addr" of 1.1.1.1 for eth0 doesn't make me happy.

Here's the really interesting part - I get the same behavior regardless of which PCMCIA card I use (similar 3Com cards and two Xircom cards), which laptop I use (tried it with an HP Omnibook 800CT), or which distribution I use (failed to get DHCP up and running with debian Sarge on floppy). 

Windows computers can get connectivity in the same place without proxy settings.

I'm under the impression I'm missing a fundamental step whenever I use a Pentium I laptop.

What else should I try?

---

### Post by foolsh on 2006-08-14
yeah ip adress 1.1.1.1 is not really what your looking for i guess lol

i take it your using a wireless router some where in your home 
if you dont have a dhcp server setup somewhere your not gonna be happy 
you could manually define an ip address
```
sudo ifconfig eth0 192.168.0.something up
```
also check in the network settings to see if the local gateway and nameserver are pointing to your router most likly 192.168.0.1 for both

---

### Post by lkvee on 2006-08-15
The setup's actually wired to a university network.   The Windows computers can connect and successfully handshake with the DHCP server.  I haven't been able to do so with Linux yet.

I *am* assuming no one's changed the network architecture or infrastructure at the university.   The one way I'll know for sure is to use Tom's Root Boot on another Dell laptop.   I successfully performed a 'net install of debian Sarge with the boot, root, and net floppies.  TRB should get connectivity, since the PCMCIA card's supported.

I'm crossssssing my fingers ...

---

