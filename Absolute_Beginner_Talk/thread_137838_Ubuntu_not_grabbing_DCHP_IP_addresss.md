---
title: "Ubuntu not grabbing DCHP IP addresss"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by nmastae on 2006-02-28
I have a dynamic DCHP connection that works fine in Windows.
However, EVERY TIME I boot into Ubuntu it drops dead. (ISP can't "ping" me, either.) 

If I go into Network settings and reset everything manually, and then go into Network tools and reset everything *there* manually, then reboot, it _sometimes_ goes online, but not always, and it's not always clear what the magic ingredient was to make that happen. Ubuntu NEVER saves the appropriate Networking information in these places (which is why I have to renew it each time), even right after I've reset it. Exasperating!

I'm an absolute beginner with Linux, but I'm reasonably tech saavy.

Can anyone tell me how to set this to rights so that I can get online in either operating system?

Thanks a million!

---

### Post by xmastree on 2006-02-28
If you go to **System>Administration>Networking** and choose the Ethernet connection, and set it ti DHCP, like this:
[ATTACH]6537[/ATTACH]
Then deactivate (if active) and activate it again, that should be all you need to do. :-k

---

### Post by jbmalone on 2006-02-28
Shut down your computer.  Take out the power cord on your modem.  Wait 20 seconds or so, plug the cord back in.  Wait for all of the lights to return to normal, and then turn the computer back on.  This should work.  

All this does is reset your modem and force the DHCP address to be renewed.

---

### Post by nmastae on 2006-03-01
[QUOTE=xmastree]If you go to **System>Administration>Networking** and choose the Ethernet connection, and set it ti DHCP, like this:
[ATTACH]6537[/ATTACH]
Then deactivate (if active) and activate it again, that should be all you need to do. :-k[/QUOTE]
Thanks for posting this. 

Unfortunately, this is how my set up is, and it doesn't work.

That screenshot is pretty small, but it just says choose DCHP, and what ever is that little checkbox up above, right?

This is what I have...

---

### Post by nmastae on 2006-03-01
[QUOTE=jbmalone]Shut down your computer.  Take out the power cord on your modem.  Wait 20 seconds or so, plug the cord back in.  Wait for all of the lights to return to normal, and then turn the computer back on.  This should work.  

All this does is reset your modem and force the DHCP address to be renewed.[/QUOTE]
I tried this several times, but it didn't work.

What else would you suggest?

Thanks.

---

### Post by cronholio on 2006-03-01
Open a terminal and enter "sudo dhclient". Does it work?

---

### Post by Brunellus on 2006-03-01
Are you connected directly via a cable or DSL modem, or is your computer sitting behind a router?

If the latter, you must set the default gateway to be the router's local IP address (usually 192.168.0.1 or something similar).  Also ensure that the DCHP server on your router is configured, up and running.

Speaking of up and running, are you sure your primary network interface is up?  what is the output when you type this command in to a terminal:

sudo ifup eth0

?

---

### Post by cronholio on 2006-03-01
> If the latter, you must set the default gateway to be the router's local IP address (usually 192.168.0.1 or something similar)

That should be set automatically by DHCP if the router is also a DHCP server (which is the case with all modern home routers AFAIK).

---

### Post by Brunellus on 2006-03-01
[QUOTE=cronholio]That should be set automatically by DHCP if the router is also a DHCP server (which is the case with all modern home routers AFAIK).[/QUOTE]
as my moral philosophy lecturer once reminded me "the key problem is getting from OUGHT to IS."  This solved a connectivity problem with me once, ages ago.

---

### Post by gwilson on 2006-03-01
Here's a couple of things I have found.

I had an older, slower network card and the boot up (or installation) DCHP often didn't find the card because it was not fast enough or up to speed during boot. Switching to a newer, faster network card eliminated this.

However, I had similar problems to yours until I got the new card. What I did was just find out what address the network on my system needed and set it up as a static IP, thereby telling the system the address rather than asking it to find the address itself. On my system, it is 192.168.2.3 but it may be different on yours.

Here's what helped the most. If you go to Synaptic Package Manager and search for "xnet" it will find a program called xnetcardconfig. Install this program. It may be available elsewhere as xnetcardconfig_0.2.0-1_all.deb and is only a 39k file. If you install xnetcardconfig using Synaptic, it will show up in the System Tools section of the Applications menu (at least it did in mine). If not, install it, open a terminal window and just type in xnetcardconfig and hit return.

My experience was that if the network card was currently functional, this program would have already collected all of the IP information. While running xnetcarconfig, I was able to select static IP instead of DCHP and all of the information was already filled in. For me, this solved all my problems whereas the Gnome/Ubuntu utility under System/Administration/Networking did not. Why? I don't know.

Next time you boot up, the system will look directly toward the static IP you assigned using xnetcarconfig and connect with the network. At least, it worked for me!

Glen
Glen

---

### Post by nmastae on 2006-03-02
No router. Dynamic IP address. How do I find the static numbers?

Will print out this thread in Windows and cart it into Ubuntu manually. Hopefully one of these suggestions will work!

PS Older Dell, P3-650. 768 RAM. Network card works fine in W2K.

---

### Post by nmastae on 2006-03-02
[QUOTE=cronholio]Open a terminal and enter "sudo dhclient". Does it work?[/QUOTE]
:~$ sudo dhclient

Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/eth0/00:01:02:46:c5:0e
Sending on   LPF/eth0/00:01:02:46:c5:0e
Listening on LPF/lo/
Sending on   LPF/lo/
Sending on   Socket/fallback
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by nmastae on 2006-03-02
[QUOTE=Brunellus]

Speaking of up and running, are you sure your primary network interface is up?  what is the output when you type this command in to a terminal:

sudo ifup eth0

?[/QUOTE]
sudo ifup eth0
ifup: interface eth0 already configured

---

### Post by nmastae on 2006-03-02
Mysteriously online again. I don't understand how this gremlin works!

---

### Post by jamesr on 2006-03-02
Once when it is working ie capable of going on-line, enter the command

sudo ifconfig -a

Post the output for future reference

---

### Post by sony102600 on 2006-03-03
hey guys... I seem to be having similear problems.. the dhcp network config failed during install, and when doing these commands in terminal I get these results

dhclinet

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on LPF/sit0/
Listening on LPF/eth0/00:13:8f:73:e8:e9
Sending on LPF/eth0/00:13:8f:73:e8:e9
Listening on LPF/lo/
Sending on LPF/lo/
Sending on Socket/fallback
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 4
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 9
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

sudo ifconfig -a

eth0 Link encap:Ethernet HWaddr 00:13:8F:73:E8:E9
inet6 addr: fe80::213:8fff:fe73:e8e9/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:3194 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:7 dropped:0 overruns:0 carrier:7
collisions:0 txqueuelen:1000
RX bytes:1163970 (1.1 MiB) TX bytes:0 (0.0 b)
Interrupt:17 Base address:0xe400

lo Link encap:Local Loopback
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1122 errors:0 dropped:0 overruns:0 frame:0
TX packets:1122 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:102840 (100.4 KiB) TX bytes:102840 (100.4 KiB)

sit0 Link encap:IPv6-in-IPv4
inet6 addr: ::127.0.0.1/96 Scope:Unknown
UP RUNNING NOARP MTU:1480 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:11 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

---

### Post by cronholio on 2006-03-03
Can you reset the DSL/cable modem?

---

### Post by sony102600 on 2006-03-03
I go to iowa state university and am on the university network...

---

### Post by sisooktom on 2006-03-03
What kind of NIC do you have?  I have an old computer with a 10Mb 3Com Tornado, and I've had this problem with Ubuntu from day 1.  Nothing unusual about my setup either.  It's behind a Linksys router that works fine with my other box and with that one under Windows.  There is a problem somewhere in Ubuntu that is causing it.  A quick search will show you that several people have this problem, but I've been unable to fix it.

---

### Post by jamesr on 2006-03-03
It May not be, the same type of problem. The symptom may be the same but the cause might not be. In the current case, the NIC is being seen but not being seen by the DHCP server. Sometimes it better to start a new thread.

---

### Post by nmastae on 2006-03-03
[QUOTE=jamesr]Once when it is working ie capable of going on-line, enter the command

sudo ifconfig -a

Post the output for future reference[/QUOTE]
eth0      Link encap:Ethernet  HWaddr 00:01:02:46:C5:0E
          inet addr:69.12.151.212  Bcast:69.12.151.255  Mask:255.255.255.0
          inet6 addr: fe80::201:2ff:fe46:c50e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:339 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:429248 (419.1 KiB)  TX bytes:31578 (30.8 KiB)
          Interrupt:11 Base address:0x1000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1772 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1772 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:521134 (508.9 KiB)  TX bytes:521134 (508.9 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Meaning what?

---

### Post by nmastae on 2006-03-03
What seems to work is to power down the computer, turn off the DSL modem, unplug the phone cord from the wall, wait, plug in phone cord, turn on modem, boot into Ubuntu.

Isn't there an easier way?!

---

### Post by Kenzo on 2006-03-03
Try this post

[http://www.ubuntuforums.org/showthread.php?p=752577#post752577](http://www.ubuntuforums.org/showthread.php?p=752577#post752577)

---

### Post by sisooktom on 2006-03-04
[QUOTE=jamesr]It May not be, the same type of problem. The symptom may be the same but the cause might not be. In the current case, the NIC is being seen but not being seen by the DHCP server. Sometimes it better to start a new thread.[/QUOTE]

Actually, I've read through the thread and I'm pretty sure it's the same issue.  The thread linked above doesn't really help either because the problem isn't DNS, it's that you can't even get an IP.  At any rate, since it's my old machine I installed Dapper and it seems to work fine.  So I'd encourage the OP to either give it a go.

---

### Post by nmastae on 2006-03-05
All,

I HAVE DISCOVERED THE SOLUTION!!! 

Change the host name -- either in Windows or Ubuntu -- to match one another. Then the DSL connection will think it's still talking to the same machine and all will be well.

What a simple solution to a vexing problem!

In Ubunutu: System/Administrator/Networking/General/Host name
In Windows: Control Panel/System/Network Properties/Computer name

---

