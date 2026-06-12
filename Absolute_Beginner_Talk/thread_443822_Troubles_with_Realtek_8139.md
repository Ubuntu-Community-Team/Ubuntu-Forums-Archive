---
title: "Troubles with Realtek 8139"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by GregoryMA on 2007-05-14
I have not been able to connect to the internet using my ethernet card.  It is a Realtek 8139C/8139C+.  My internet provider uses DHCP and the network is setup for this.  The connection icon in the top right of the ubuntu window says that the connection is working but whenever I try to bring up a page it fails.  I know this is supposed to be Linux friendly card but I can't figure out what is going on.  Thanks, Greg.

---

### Post by overdrank on 2007-05-14
> **GregoryMA said:**
> I have not been able to connect to the internet using my ethernet card.  It is a Realtek 8139C/8139C+.  My internet provider uses DHCP and the network is setup for this.  The connection icon in the top right of the ubuntu window says that the connection is working but whenever I try to bring up a page it fails.  I know this is supposed to be Linux friendly card but I can't figure out what is going on.  Thanks, Greg.

Hi I did a quick search on your net card and it seems to be NOT linux friendly
[http://ubuntuforums.org/search.php?searchid=20173363](http://ubuntuforums.org/search.php?searchid=20173363)
Sorry I could not be of some help but you can search this page to find a card that will suit you.
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
Good luck! :(

---

### Post by GregoryMA on 2007-05-15
I had allready checked that and other databases of linux compatable hardware.  Everyone that I found said that Realtek 8139 is Linux friendly.  Also, this is not a wireless card, it is Ethernet.
[https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek)

---

### Post by Bachstelze on 2007-05-15
I don't think it's a problem with your card but with your network settings. What does that command output ?

```
sudo ifconfig -a
```

---

### Post by overdrank on 2007-05-15
> **GregoryMA said:**
> I had allready checked that and other databases of linux compatable hardware.  Everyone that I found said that Realtek 8139 is Linux friendly.  Also, this is not a wireless card, it is Ethernet.
[https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek)

My apologizes for the confusion, just attempting to help. :???:

---

### Post by GregoryMA on 2007-05-15
No worries Paul.  We are all friendly here.

Here is the output:

eth0 Link encap:Ethernet HWaddr 00:C0:9F:B5:29:A3
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:19 Base address:0xe000

eth1 Link encap:Ethernet HWaddr 00:90:4B:F9:2A:EC
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:3

eth0:avah Link encap:Ethernet HWaddr 00:C0:9F:B5:29:A3
inet addr:169.254.7.241 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:19 Base address:0xe000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:34 errors:0 dropped:0 overruns:0 frame:0
TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:2564 (2.5 KiB) TX bytes:2564 (2.5 KiB)

Should I be connecting to the modem (motorla sb5101 cable modem) directly or via the router? or does it matter?  

Thanks, Greg.

P.S.  Is there someway to bookmark a thread so I don't have to go and search for it?

---

### Post by Bachstelze on 2007-05-15
hmm, you seeem to have to NICs, which one is it you want to connect with ?

---

### Post by GregoryMA on 2007-05-15
I am not sure.  I do not know what a NIC is?

---

### Post by Bachstelze on 2007-05-15
Network Interface Card...

---

### Post by jerrylamos on 2007-05-15
Elementary question, there's a Network Mangler icon on the top right of the screen.  Does it have a little red mark on it?  If so, select it, then select on wired connection.  It might.

If that doesn't do it, do Applications, Accessories, Terminal
sudo dhclient

then try 
ifconfig 

again to see if there's an internet address this time

Cheers, Jerry

---

### Post by GregoryMA on 2007-05-15
Honestly, I am not sure which card to use.  I thought there was just one.  Is it unwise to just pick one, start messing with it and if nothing comes of it try the other one?

I tried your advice Jerry, but there isn't that little red dot (the tiny exclamation mark in a triangle) on the icon.  That's what is confusing me, it seems to think there is a connection.  However, when I ran dhclient it keep saying 'send packet: network is down'.

---

### Post by GregoryMA on 2007-05-15
Also, I noticed when Ubuntu is loading for about a second it says somthing to the like of "...msbios: 8254 timer not connected to IO-APIC".  Could this be related?

---

