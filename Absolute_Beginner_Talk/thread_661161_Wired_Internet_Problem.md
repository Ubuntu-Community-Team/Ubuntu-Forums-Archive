---
title: "Wired Internet Problem"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Monkalou on 2008-01-07
I have had Linux on my machine for about a year.  The wired internet connection was working, but recently I've lost the connection.  I try pinging the router, but it tells me the network is unreachable.   

(The hardware is fine as I have a Windows wired computer running off the router as well, and I've replaced the ethernet cable with no effect.)

The routing table is messed up, but I'm not sure what set of commands to use to change it properly (and permanently, as it resets when I reboot).

> monkalou@monkalou-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0   0.0.0.0     255.255.0.0   U  0    0  0 eth0
0.0.0.0           0.0.0.0     0.0.0.0           U  1000 0 0 eth0


And the rest of the diagnostics...

> 
monkalou@monkalou-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D4:57:FC:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0x2000 

eth0:avah Link encap:Ethernet  HWaddr 00:13:D4:57:FC:88  
          inet addr:169.254.9.89  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:51 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18095 (17.6 KiB)  TX bytes:18095 (17.6 KiB)


monkalou@monkalou-desktop:~$ sudo cat /etc/resolv.conf
Password:
search earthlink.net
nameserver 207.69.188.185
nameserver 207.69.188.186
nameserver 207.69.188.187

monkalou@monkalou-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth0

monkalou@monkalou-desktop:~$ ip address show dev eth0
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:13:d4:57:fc:88 brd ff:ff:ff:ff:ff:ff
    inet 169.254.9.89/16 brd 169.254.255.255 scope link eth0:avahi



Thanks for your help!

---

### Post by kyphi on 2008-01-07
Since the router works with Windows, the problem must be in the networking configuration of Ubuntu.

Go to System -> Administration -> Networking.  Click on your Ethernet connection then Properties and check that 'Enable this connection' is checked.  Also check your Connection settings, Configuration.  The choice there is either static or dynamic.

Back to Network Settings where under DNS and DNS Servers the entry should be your modem/router address.  Under Search Domains should be your ISP's name, i.e. the section of your email address after the @.

Give that a try for a start.

---

### Post by laidback on 2008-01-07
Even if the above (from kyphi) looks correct on the screen it can be worthwhile deleting it and retyping. I've had a situation where it looks fine, but until I retyped nothing would work. I can only assume that non printable characters got into the entries.

---

### Post by Monkalou on 2008-01-07
Ok, I checked and the wired Ethernet connection is enabled and set to dhcp.  

I put my router address under the DNS server and made sure the search domain was correct. 

I restarted Linux and tried pinging my router, but I get Destination Host Unreachable.

---

### Post by kyphi on 2008-01-07
Could you try to connect your Ubuntu box to a different LAN port - such as the one that Windows is connected to.  I assume from your description that you are running two computers to the same modem/router.

Or try an older kernel.

---

### Post by laidback on 2008-01-08
Be sure you have the Enable Roaming check box DISABLED. It's in the Network>Properties screen.

---

### Post by Monkalou on 2008-01-08
I've tried an older kernel and the problem remains.  Enable Roaming is unchecked.  I've switched the ethernet cords to different ports on the router and it doesn't change anything.

---

### Post by kyphi on 2008-01-08
Is there a green light at the ethernet terminal on the computer as well as the modem/router signifying an active connection?

Have you recently installed or adjusted your firewall?

The fault is either in your Ubuntu installation or the computer that runs Ubuntu.

Since you cannot ping your router, I suspect a faulty ethernet card.

If you do not have a spare card to hand you could "borrow" the one in your Windows box and insert it into the Ubuntu box.  At least then you will know that it is or is not the ethernet card.

---

### Post by Monkalou on 2008-01-08
There light doesn't turn on for this connection on the router, nor does one light up when I plug the ethernet cable in my computer.  I think the ethernet card is busted.

Thanks for your help.

---

### Post by Monkalou on 2008-01-09
Just replaced my ethernet card and I'm back up.

Thanks

---

### Post by kyphi on 2008-01-09
Pleased to read of your success.

---

