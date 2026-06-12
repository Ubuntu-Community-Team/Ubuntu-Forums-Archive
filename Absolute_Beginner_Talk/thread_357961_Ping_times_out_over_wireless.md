---
title: "Ping times out over wireless"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by DigitalVortex on 2007-02-10
Greetings,

Basic setup of network includes two Win2K desktop machines, one Win XP Laptop, and one Ubuntu 6.06 LTS Server.  Only unit connecting through wireless is the laptop.

My wired network (desktop machines) can ping the Ubuntu Server all day.  I can ping my windows desktop machines with the wireless laptop all day.  When I try to ping the Unbuntu Server from the laptop, I will begin to get "Request Timed Out" anywhere from after 8 to 25 or so packets sent.  Once the timeouts start, they don't stop - it will not recover.

Typically something like this wouldn't bother me.  But I'm pretty sure that whatever is causing this, is the reason I can't get Putty to work from the laptop either.  Yes, I can get Putty to work just fine from the desktop machines.  From the laptop, Putty will initially connect, but at some arbitrary point, I'll get a Fatal Error and it aborts -- usually I can't reconnect it for several minutes.

I figure the problem is likely in the packets being sent by my XP laptop to the Ubuntu Server, but I'm not sure what I should be trying to tweak.  Any thoughts?

Note -- everything in this is on the internal network.  There is no firewalling setup across the LAN.

Thanks for any input -- I won't get to look at anything till late tonight.

---

### Post by DigitalVortex on 2007-02-24
I see there have been views, but no replies as yet.  The likely reason I'm going to suspect is not enough info.  In the past 2 weeks I've been scouring this forum for more info and haven't found anything to apply as yet.  So I'll add more info and hope someone has an idea.

The wireless access point is technically a DI-614+ router.  Nothing that makes it a router is turned on however.  Further, from the laptop I am able to use Remote Desktop Admin sessions with both Win2K machines on the network.  IP of this unit is 10.0.0.10.  The DI-614+ has a screen for the following wireless settings:
-Beacon interval [100]	(msec, range:1~1000, default:100)
-RTS Threshold : [2432]	(range: 256~2432, default:2432) 
-Fragmentation : [2346]	(range: 256~2346, default:2346, even number only)
-DTIM interval : [3]	(range: 1~255, default:3)
-Basic Rates :	  1-2(Mbps)     1-2-5.5-11(Mbps)     X 1-2-5.5-11-22(Mbps)
-TX Rates:   	   1-2(Mbps)      1-2-5.5-11(Mbps)     X 1-2-5.5-11-22(Mbps)
-Preamble Type :	Short Preamble         X  Long Preamble  
-Authentication :	Open System            Shared Key              X Auto
-SSID Broadcast :   X Enabled         Disabled
-Antenna transmit power:  100%
-4X Mode :    Enabled        X Disabled

The "X"s above preceed the value chosen.

The Ubuntu Server is set up with a static IP
hates@car00:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:5A:48:8B:B8
          inet addr:10.0.0.20  Bcast:10.0.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:778554 (760.3 KiB)  TX bytes:155288 (151.6 KiB)
          Interrupt:10 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)

I originally had this as dynamic DHCP and assigned the same DHCP address from the Zywall 2X firewall.  Results are the same regardless of this setup.  IP of the firewall is 10.0.0.100.

The Zywall is set up to allow all traffic accross the LAN.  As said previously I can ping the server all day from both wired machines.  I can log in with Putty on both wired machines.  Putty will lockup after several seconds to a minute on the wireless laptop however.  Additionally I can RAdmin to my Windows desktop from the laptop, open Putty, and maintain a session that way.

From the laptop my pings to the 10.0.0.10 address are clean.  From the laptop to the 10.0.0.100 of the firewally my pings are clean.  And as previously stated, at varying points ping from laptop to server will end with Request timed out and stay that way indefinitely.

From the server to 10.0.0.100, pings are clean.  From the server to the 10.0.0.10, pings are clean.  From the server to the laptop, I won't get any timeouts, but occasionally, a oddly high ping time shows up like 83 or 120 ms.  Those are the exceptions and the averages will end up less than 10 ms.

Info from lspci:
hates@car00:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0d.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:00:13.0 Mass storage controller: Triones Technologies, Inc. HPT366/368/370/370A/372/372N (rev 01)
0000:00:13.1 Mass storage controller: Triones Technologies, Inc. HPT366/368/370/370A/372/372N (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

Any ideas?  Anyone know of something I can tweak on the router (being used as an access point only) or maybe something I can tweak on the Ubuntu server?  The NIC in the server is recognized correctly as well.

I appreciate any and all help that the many on here can offer.  I'm not new to networking, as this server is replacing a severely outdated Win NT box.  But, I am new to the vast majority of stuff on Linux.  There's a definite learning curve.

Thanks!

---

### Post by brenthaag on 2007-03-02
I have a similar problem that I am still trying to figure out.  I have a wireless access point, but I don't use it's WAN port or dhcp server.  I have a standalone PC with SmoothWall on it that does the routing.  I can connect (ping, ssh, etc.) to the wireless PCs from a wired connection on the network.  However, I cannot connect to a wireless PC from another wireless PC...

I think it has something to do with the wireless access hardware and it's routing table...I'll post something here if I figure it out.

---

### Post by DigitalVortex on 2007-03-03
> I have a wireless access point, but I don't use it's WAN port or dhcp server.
This portion of our setup is the same.  Are you able to play with settings on that unit like I described above, such as beacon interval, rts threshold, fragmentation, etc.?
> I have a standalone PC with SmoothWall on it that does the routing.  I can connect (ping, ssh, etc.) to the wireless PCs from a wired connection on the network.  However, I cannot connect to a wireless PC from another wireless PC...
Difference here that I see is I use an appliance firewall rather than "SmoothWall".  Additionally, are all of your machines Linux based, or are you in a mixed OS environment?

Two things completely baffle me on my own situation.  The machine that Ubuntu Server is on for me is a clean install.  Previously it was Win2K and I could ping that box all day long from the WinXP wireless laptop.  Basically, I put Ubuntu Server on it, it has no firewall of its own, it has a static IP, I can ping it a few times, then the ping dies and will not recover.  This has to be related to the issues I have in keeping a Putty session up between the laptop and server.  I have no problem at all pinging the Server from a wired Win2K client machine -- this problem is beyond annoying at this point.

I too intend to post back if I figure anything out, but thus far I've come up empty.  I've tried using tweaks that are suggested to help with internet surfing (mainly because I figured they could have some bearing on the way eth0 functions in general) but such things haven't helped or hurt.  I'm still at square one on the issue.

> I think it has something to do with the wireless access hardware and it's routing table...I'll post something here if I figure it out.
By the routing table, I think you mean what you have set up on the SmoothWall.  I would agree that you may find your issue there.  Did I understand correctly that your routing from the SmoothWall to the wireless machines is absolutely fine?  Yet, from wireless client to wireless client it fails...and must route through the SmoothWall --- this is the mental picture I get of your setup.  Please correct if wrong.

---

### Post by brenthaag on 2007-03-04
My network has Linux and Windows boxes.  My laptop has XP and Ubuntu on it and both of them will not route to the other (Ubuntu) box.  Therefore, it leads me to believe that it might just be a limitation of the wireless router/access point.  It is a Netgear WGR614v4 and it doesn't have the options that you discuss above.

I'm really clueless now, I've tried everything and searched till I was blue in the face!

---

### Post by DigitalVortex on 2007-03-04
Are you testing your routes/pings through the wireless via your internal IP addresses or host names?  At this point I still haven't gotten my Unbuntu Server to see the host names of my Windows clients (whether wired or otherwise).   But I haven't tried.  On the Windows boxes however, I modified the C:\WINNT\system32\drivers\etc\hosts file to include the local host name of the server with its IP...resulted in Windows clients being able to see the Ubuntu Server's name, rather than just internal IP.

If you are doing all testing via IPs, then I may very well have to agree that there is a potential limitation to the unit...one that I may also be facing but am reluctant to accept because of the success I had when the environment was all Windows.

I assume you already tested the ability to ping the wireless access point from the wireless machines, and you can ping the machine running SmoothWall from these wireless clients as well.  The clients just can't see each other.  Right?  That almost sounds like something on the SmoothWall that would be preventing the requests through it.

Out of curiosity, are you able to wire either of the currently wireless clients to the wireless access point and test communication between the clients that way?  I'm sure, like me, you've been over your Netgear with a fine toothed comb to insure absolutely nothing is turned on that would prohibit any traffic.

I don't know what's worse -- you can't get routing between two wireless machines to work at all, or my situation that it works to an extent and then dies for no apparent reason.

---

### Post by brenthaag on 2007-03-05
I haven't worried about hostnames, except for my router.  It sometimes looks for [www.routerlogin.com](www.routerlogin.com), so I put its IP address in the SmoothWall's /etc/hosts file.  Since the Smoothwall is also a DNS proxy for my LAN, the other PCs will resolve that name correctly.

I am testing with IPs only, and I have read another page on the internet where someone had the same problem with the same router I have.  I am probably going to try to get another router to test and see if it is the problem.

I have taken the laptop and connected it via a wired ethernet connection and it works fine.  I'm sorry I haven't been able to help you on your problem, though.

---

### Post by DigitalVortex on 2007-03-05
No need for apologies - misery likes company.  I have officially narrowed the problem to the DI-614+.  I finally tried testing my laptop on the network on a wired connection and it's 100% fine.  So I might try tweaking a couple of those settings I found in the router that are directly related to the wireless and see if I can't beat it.  Otherwise, I'll just end up finding another wireless access point that will do the job.

Thanks for the thoughts you did offer -- nice to know I'm not "the only one."

---

### Post by DigitalVortex on 2007-03-09
This issue just got more strange, if that's possible.  Keep in mind, I'm not well versed in commands and was attempting to follow some guidelines on using tcpdump.  I had entered the following line of code:

$ sudo tcpdump -n

Fact is, it was the only string that I tried that ended up not giving me an error.  I did this through an ssh session on a wired Win2K client.  At that point, I proceeded to try to ping the Ubuntu server from the laptop.  It worked FINE!  Further I was able to open an ssh session from the laptop as well.  It worked great!

Then I stopped the tcpdump.  I tried pinging from the laptop again.  It was back to the poor behavior again.  I tried the ssh session from the laptop and it too did not function.

So what is it about running the tcpdump that suddenly makes network communication over the wireless network the slightest bit happy?  Anyone have an idea of something low in resources I could set up to run normally on the server that would mimic this behavior and therefore allow my wireless network to work all the time?

Suggestions would be greatly appreciated!

---

### Post by DigitalVortex on 2007-03-09
One more update to provoke more thought and wonderment on my part.  When I ping the Ubuntu server from a wired machine on the network, the problem I have from the wireless laptop to the Ubuntu server disappears as well.

So, if I have ongoing communication on the eth0 interface on the server, I am able to communicate just fine with the server from the laptop's wireless connection.  Why is this happening?  Anyone know what I can do?

---

