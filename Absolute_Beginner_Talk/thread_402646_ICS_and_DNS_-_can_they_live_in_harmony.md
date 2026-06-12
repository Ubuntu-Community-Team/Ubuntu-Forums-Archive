---
title: "ICS and DNS - can they live in harmony?"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by Robynsveil on 2007-04-06
Hi,
I'm still having fun with this... so please bear with me for asking such silly questions. Here is a diagram of my network:

[IMG]http://www.tightbytes.com/images/Home_Network2.jpg[/IMG]

Now, I've managed to access the Ubuntu 6.10 Test Server using SSH and PuTTY - colour me Chuffed! I've installed some of the LAMP stuff, and therein lies the rub, I think. It is now a DNS server - which is always on - whilst the Windows 2K box is shut down every night. In the past (before the DNS server was operational) I was able to access some of the Windows 2K partitions from my Ubuntu workstation, probably using Samba. This morning I started the Windows 2K box, and connected to the Internet, my Ubuntu workstation was able to access the Web - I assume, via Win2K's ICS. However, when I do:

Places -> Network Servers

it brings up an icon representing the Windows Network, but double-clicking on it leaves me with an empty folder. I can ping 192.168.0.1 successfully, and ifconfig gives me:

```

eth0      Link encap:Ethernet  HWaddr 00:0C:76:4E:33:0B  
          inet addr:192.168.0.161  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:76ff:fe4e:330b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1945 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2495833 (2.3 MiB)  TX bytes:259541 (253.4 KiB)
          Interrupt:201 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10118 (9.8 KiB)  TX bytes:10118 (9.8 KiB)


```

My /etc/network/interfaces has:

> auto lo
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

...haven't really done anything to that.

Any Ideas? Anything I need to be studying?

BTW, I set up that Linux LAMP server using this tutorial - bloody brilliant, it is:

[http://www.howtoforge.com/perfect_setup_ubuntu_6.10]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10")

and it worked, for the most part (except for the thingie on page 4 where you do this install of files you'll be needing - took out the "linux-kernel-headers" bit and it worked a treat.

---

### Post by graeme_p on 2007-04-06
This [article]("http://www.practicallynetworked.com/sharing/xp_ics/") suggests you should not have ICS with another DNS server (see warning #2). Have you tried turning off the DNS server on the Ubuntu server?

Secondly, if the Ubuntu server is always on, surely it would make more sense to use that to share the connection?

Thirdly, the easiest solution is probably to use a hardware router, plug it into the cable modem and everything else into the router.  I think home routers are quite cheap these days.

With DSL connections you can usually get a combined router "modem" . From what I gather, with a cable connection you will need a separate router.

I am not sure how either solution will affect samba though......

---

### Post by Robynsveil on 2007-04-06
Thanks Graeme... you have answered my question. I agree: my DNS server *is* probably not having a symbiotic relationship with ICS, although the article you linked to didn't really explain *why*. From what I've read, there are compelling reasons to invoke a cheapo Linux box to do the proxy-server job preferentially over simply buying a router... has something to do with control. Suits me just fine: I'm a control-freak. ;)

I don't want to invoke this particular box (my test server) as proxy server, since there is a school of thought that strongly advocates physically separating proxy-server functions from web-server, file-server and database-server functionality. So, it's a matter of setting up another box real quick as DNS/NAT/proxy box running FireStarter and minimal Ubuntu Linux.

---

### Post by graeme_p on 2007-04-06
The ICS machine must be the DNS server [according to MS as well]("http://support.microsoft.com/kb/309642"), I still have no idea why.

I take the point about separating the servers - I had assumed  (OK, do not assume!) that the Windows 2000 server must be doing something other than ICS and (judging by your diagram) acting as a print server, and therefore you were not being particular about it. With a Linux NAT/proxy/DHCP box, if you attach the printer to a Linux server as well, will your Windows server be redundant?

An extra server to configure is too much work for me.......

---

### Post by Robynsveil on 2007-04-07
> **graeme_p said:**
> The ICS machine must be the DNS server [according to MS as well]("http://support.microsoft.com/kb/309642"), I still have no idea why.

My guess, Graeme, is that the hobbled, non-configurable mini-dhcp function of ICS is so that the customer doesn't try to set up an elaborate, useful network without paying the By-The-Seat charges for NT Server. My instructor at TAFE only just came to the realization that ICS *must* by its behaviour have a sort of dhcp server function in it, although M$ doesn't call it that - not anywhere that I can recall, anyway - in the help files.

> **graeme_p said:**
> I take the point about separating the servers - I had assumed  (OK, do not assume!) that the Windows 2000 server must be doing something other than ICS and (judging by your diagram) acting as a print server, and therefore you were not being particular about it. With a Linux NAT/proxy/DHCP box, if you attach the printer to a Linux server as well, will your Windows server be redundant?
At present, it does, actually. The printer is attached to its parallel port - although this Xerox industrial-strength Laser Duplex Printer has a port for Cat5 cable connection, which sounds like a good idea, eventually! - and some of the additional hard drives are used (far too infrequently) as back-up drives for the various workstations. My goal is to have file service (backups and database testing and web-site testing) primarily on that test Server currently up and running, whilst the Proxy Sever I spent all day trying to get working will do only that: router/firewall Internet connection sharing and DNS server. It would be 192.168.0.1, and the LAMP Server would be 192.168.0.100. My little group - XP and Linux - should be able to access these servers with Samba and NFS. That's the grand plan, so far. Still have a hecka lot of stuff to get my head around, though... :)

---

